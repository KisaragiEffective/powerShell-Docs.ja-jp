---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: パイプラインからオブジェクトを削除する (Where-Object)
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 1f7d064c7bf2dd551ea96b29762fbccad8174084
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057914"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>パイプラインからオブジェクトを削除する (Where-Object)

Windows PowerShell では、考えていた数よりも多くのオブジェクトが生成され、パイプラインに渡されることがよくあります。 **Format** コマンドレットを使用して、特定のオブジェクトのプロパティを指定し、表示することができます。しかし、これはオブジェクト全体を表示から削除するという問題には役立ちません。 パイプラインの終了前に、オブジェクトをフィルタリングすることによって、最初に生成されたオブジェクトのサブセット上でのみアクションを実行できます。

Windows PowerShell には、`Where-Object` コマンドレットがあります。これを使用すると、パイプラインの各オブジェクトをテストし、特定のテスト条件を満たしている場合にのみ、オブジェクトをパイプラインに沿って渡すことができます。 テストを通過しなかったオブジェクトは、パイプラインから削除されます。 テスト条件は、`Where-Object` **FilterScript** パラメーターの値として指定します。

## <a name="performing-simple-tests-with-where-object"></a>Where-Object を使用して単純なテストを実行する

**FilterScript** の値は、true または false に評価される*スクリプト ブロック* - (中かっこ {} で囲まれた 1 つまたは複数の Windows PowerShell コマンド) です。 これらのスクリプト ブロックはごく単純にすることができますが、作成するには別の Windows PowerShell の概念である比較演算子について知っておく必要があります。 比較演算子は、演算子の両辺のアイテムを比較します。 比較演算子は、'-' 文字で始まり、名前が続きます。 基本的な比較演算子は、ほとんどの種類のオブジェクトで機能します。 より高度な比較演算子の中には、テキストまたは配列でのみ機能するものもあります。

> [!NOTE]
> 既定では、テキストで使用する場合、Windows PowerShell の比較演算子は大文字小文字を区別しません。

解析の考慮事項のため、<、>、= などのシンボルは、比較演算子として使用されません。 代わりに、比較演算子は文字で構成されます。 基本的な比較演算子を次の表に挙げます。

|比較演算子|意味|例 (true を返す)|
|-----------------------|-----------|--------------------------|
|-eq|次の値と等しい|1 -eq 1|
|-ne|次の値と等しくない|1 -ne 2|
|-lt|次の値未満|1 -lt 2|
|-le|次の値以下|1 -le 2|
|-gt|次の値より大きい|2 -gt 1|
|-ge|次の値以上|2 -ge 1|
|-like|次の文字列と類似 (テキストのワイルドカード比較)|"file.doc" -like "f\*.do?"|
|-notlike|次の文字列と類似していない (テキストのワイルドカード比較)|"file.doc" -notlike "p\*.doc"|
|-contains|[内容]|1,2,3 -contains 1|
|-notcontains|[次の値を含まない]|1,2,3 -notcontains 4|

Where-Object スクリプト ブロックは、パイプライン中の現在のオブジェクトを参照するために、特殊変数 `$_` を使用します。 次に挙げるのは、その働きを示す例です。 数値の一覧があり、3 未満の値だけを返したい場合、Where-Object を使用して、次のように入力して数値を抽出できます。

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>オブジェクトのプロパティに基づくフィルタリング

`$_` は、現在のパイプライン オブジェクトを参照するので、テストのためにそのプロパティにアクセスできます。

例として、WMI の Win32_SystemDriver クラスを取り上げます。 特定のシステムには、何百ものシステム ドライバーが存在する可能性がありますが、関心を向けるのは、現在実行中のシステム ドライバーなど、システム ドライバーの特定のセットだけの場合があります。 Get-Member を使用して、Win32_SystemDriver メンバーを表示する場合 (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**)、関連するプロパティは State に、ドライバーが実行中であればその値は "Running" になります。 システム ドライバーをフィルタリングして、次のように入力して実行中のドライバーのみを選択できます。

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

生成されるのは、依然として長い一覧です。 StartMode 値を同様にテストして、自動的に起動されるドライバーのセットのみを選択するようフィルタリングすることにします。

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

これにより、もう必要のない数多くの情報が与えられます。それらのドライバーが実行中なのはわかっています。 事実、この時点でおそらく必要とされる情報は、名前と表示名だけです。 次のコマンドには、それら 2 つのプロパティのみが含まれており、よりシンプルに結果を出力します。

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

上記のコマンドには Where-Object 要素が 2 つありますが、次のように -and 論理演算子を使用して、Where-Object 要素 1 つで表現することができます。

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

標準的な論理演算子を次の表に挙げます。

|論理演算子|意味|例 (true を返す)|
|--------------------|-----------|--------------------------|
|-and|論理積。両辺が true の場合は true|(1 -eq 1) -and (2 -eq 2)|
|-or|論理和。どちらかの辺が true の場合は true|(1 -eq 1) -or (1 -eq 2)|
|-not|論理否定。true と false を逆にする|-not (1 -eq 2)|
|\!|論理否定。true と false を逆にする|\!(1 -eq 2)|
