---
ms.date: 11/22/2019
keywords: powershell,コマンドレット
title: Format コマンドを使用した出力ビューの変更
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417596"
---
# <a name="using-format-commands-to-change-output-view"></a>Format コマンドを使用した出力ビューの変更

PowerShell には、特定のオブジェクトに対するプロパティの表示方法を制御できるコマンドレットのセットが用意されています。 すべてのコマンドレットの名前は、動詞 `Format` から始まります。 これらには、表示するプロパティを選択できます。

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

この記事では、`Format-Wide`、`Format-List`、`Format-Table` のコマンドレットについて説明します。

PowerShell の各オブジェクトの種類には、表示するプロパティを指定しない場合に使用される既定のプロパティがあります。 どのコマンドレットでも、同じ **Property** パラメーターを使用して、表示するプロパティを指定します。 `Format-Wide` はプロパティを 1 つだけ表示するため、その **Property** パラメーターには値を 1 つだけ設定します。ただし、`Format-List` と `Format-Table` の Property パラメーターには、プロパティ名のリストを使用できます。

この例では、`Get-Process` コマンドレットの既定の出力は、Internet Explorer の 2 つのインスタンスが実行されていることを示しています。

```powershell
Get-Process -Name iexplore
```

**Process** オブジェクトの既定の形式では、次に示すプロパティが表示されます。

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>単一項目出力のための Format-Wide の使用

`Format-Wide` コマンドレットでは、既定では、オブジェクトの既定のプロパティだけが表示されます。 各オブジェクトに関連付けられている情報が、1 つの列に表示されます。

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

既定以外のプロパティを指定することもできます。

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>列による Format-Wide 表示の制御

`Format-Wide` コマンドレットでは、一度に表示できるプロパティは 1 つだけです。 これは、大きなリストを複数の列に表示する場合に便利です。

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>リスト ビューのための Format-List の使用

`Format-List` コマンドレットによって、リストの形式でオブジェクトを表示します。各プロパティはラベル付けされ、別々の行に表示されます。

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

必要な数だけプロパティを指定できます。

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Format-List でワイルドカードを使用して詳細情報を取得する

`Format-List` コマンドレットでは、その **Property** パラメーターの値としてワイルドカードを使用できます。 こうすることで、詳細情報を表示できます。 多くの場合、オブジェクトには必要以上の情報が含まれています。既定では PowerShell ですべてのプロパティ値が表示されないのはそのためです。 オブジェクトのプロパティをすべて表示するには、`Format-List -Property *` コマンドを使用します。 次のコマンドは、1 つのプロセスについて 60 行を超える出力を生成します。

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

`Format-List` コマンドは詳細の表示に役立ちますが、項目が多数含まれる出力の概要が必要な場合は、よりシンプルな表形式ビューの方が便利なことが多いです。

## <a name="using-format-table-for-tabular-output"></a>表形式出力のための Format-Table の使用

プロパティ名を指定せずに `Format-Table` コマンドレットを使用して `Get-Process` コマンドの出力を書式設定した場合は、`Format` コマンドレットを使用せずに行った場合とまったく同じ出力になります。 既定では、PowerShell によって **Process** オブジェクトが表形式で表示されます。

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>Format-Table 出力の改善 (AutoSize)

表形式ビューは情報を大量に表示するには便利ですが、データの表示幅が狭すぎる場合は解釈しにくいことがあります。 前の例では、出力は切り捨てられています。 `Format-Table` コマンドを実行するときに **AutoSize** パラメーターを指定すると、PowerShell では、表示される実際のデータに基づいて列の幅を計算します。 これにより、列を読み取ることができるようになります。

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

`Format-Table` コマンドレットでは引き続きデータを切り捨てることもありますが、切り捨てられるのは画面の端だけです。 最後に表示されるもの以外のプロパティには、最長データ要素が正しく表示されるために必要なだけのサイズが与えられます。

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

`Format-Table` コマンドでは、プロパティが重要度順に一覧表示されていると仮定します。 したがって、先頭に最も近いプロパティを完全に表示しようとします。 `Format-Table` コマンドですべてのプロパティを表示できない場合は、表示から一部の列が削除されます。 この動作は、前の例の **DependentServices** プロパティで確認できます。

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Format-Table 出力の列内の折り返し (Wrap)

**Wrap** パラメーターを使用することで、長い `Format-Table` データをその表示列内で強制的に折り返すことができます。 **Wrap** パラメーターだけを使用した場合、必ずしも期待どおりにはなりません。**AutoSize** も指定しなければ、既定の設定が使用されるためです。

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

**Wrap** パラメーターを単独で使用すると、処理はあまり遅くなりません。 しかし、**AutoSize** を使用した場合、大規模なディレクトリ構造の再帰的ファイル リスト表示を実行すると、最初の出力項目が表示されるまで長い時間がかかり、大量のメモリが使用されることがあります。

システム負荷が気にならなければ、**AutoSize** は **Wrap** パラメーターと共に使用する場合に適しています。
最初の列では 1 行に項目を表示するために必要な幅が引き続き使用されますが、必要に応じて最後の列が折り返されます。

> [!NOTE]
> 最も広い列を最初に指定すると、一部の列が表示されない場合があります。 最適な結果を得るには、最初に最小のデータ要素を指定します。

次の例では、最も幅の広いプロパティを最初に指定しています。

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

折り返しを使用した場合でも、最後の **Id** 列は省略されます。

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>表出力の整理 (-GroupBy)

表形式出力制御のためのもう一つの便利なパラメーターは、**GroupBy** です。 長い表形式リストは特に、比較しにくい場合があります。 **GroupBy** パラメーターは、プロパティ値に基づいて出力をグループ化します。 たとえば、検査しやすくするために、**StartType** 別にサービスをグループ化できます。この場合、プロパティ リストから **StartType** の値を省略します。

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
