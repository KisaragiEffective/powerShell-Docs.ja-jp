---
title: Windows PowerShell ISE でプロファイルを使用する方法
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# Windows PowerShell ISE でプロファイルを使用する方法
このトピックでは、Windows PowerShellÂ® Integrated Scripting Environment (ISE) でプロファイルを使用する方法について説明します。 このセクションのタスクを実行する前に、[about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054) を確認するか、またはコンソール ウィンドウに「get\-help about\_profiles」と入力して **ENTER** キーを押すことをお勧めします。.

プロファイルは、新しいセッションを開始するときに自動的に実行される Windows PowerShell ISE スクリプトです。  Windows PowerShell ISE 用に 1 つ以上の Windows PowerShell プロファイルを作成すると、Windows PowerShell または Windows PowerShell ISE 環境の構成に、自分の用途に合わせて変数、エイリアス、関数、色やフォントの設定などを追加するために利用できます。 プロファイルは、開始するすべての Windows PowerShell ISE セッションに影響を与えます。

> [!NOTE]
> スクリプトの実行やプロファイルの読み込みが可能かどうかは、Windows PowerShell の実行ポリシーによって決まります。 既定の実行ポリシーは "Restricted" で、プロファイルを含め、すべてのスクリプトが実行されないようにします。 "Restricted" ポリシーを使う場合は、プロファイルを読み込めません。 実行ポリシーの詳細については、「[about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6)」を参照してください。.

## Windows PowerShell ISE で使うプロファイルの選択
Windows PowerShell ISE は、現在のユーザーとすべてのユーザーのプロファイルをサポートしています。 また、すべてのホストに適用される Windows PowerShell プロファイルもサポートしています。

使用するプロファイルは、Windows PowerShell と Windows PowerShell ISE の使用方法によって決まります。

-   Windows PowerShell を実行するために Windows PowerShell ISE のみを使う場合は、すべての項目を ISE 固有のプロファイルの 1 つに保存します。たとえば、Windows PowerShell ISE 用の CurrentUserCurrentHost プロファイルや、Windows PowerShell ISE 用の AllUsersCurrentHost プロファイルです。

-   Windows PowerShell を実行するために複数のホスト プログラムを使う場合は、関数、エイリアス、変数、コマンドをすべてのホスト プログラムに影響を与えるプロファイルに保存します。たとえば、CurrentUserAllHosts プロファイルや、AllUsersAllHosts プロファイルです。また、色やフォントのカスタマイズのような ISE 固有の機能は、Windows PowerShell ISE 用の CurrentUserCurrentHost プロファイルか、Windows PowerShell ISE 用の AllUsersCurrentHost プロファイルに保存します。

Windows PowerShell ISE で作成して利用できるプロファイルは次のとおりです。 各プロファイルは、それぞれ特定のパスに保存されます。

|プロファイルの種類|プロファイルのパス|
|----------------|----------------|
|"現在のユーザー、PowerShell ISE"|$profile.CurrentUserCurrentHost、または $profile|
|"すべてのユーザー、PowerShell ISE"|$profile.AllUsersCurrentHost|
|"現在のユーザー、すべてのホスト"|$profile.CurrentUserAllHosts|
|"すべてのユーザー、すべてのホスト"|$profile.AllUsersAllHosts|

## 新しいプロファイルを作成するには
"現在のユーザー、Windows PowerShell ISE" の新しいプロファイルを作成するには、次のコマンドを実行します。

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

"すべてのユーザー、Windows PowerShell ISE" の新しいプロファイルを作成するには、次のコマンドを実行します。

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

"現在のユーザー、すべてのホスト" の新しいプロファイルを作成するには、次のコマンドを実行します。

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

"すべてのユーザー、すべてのホスト" の新しいプロファイルを作成するには、次のように入力します。

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## プロファイルを編集するには

1.  プロファイルを開くには、編集するプロファイルを設定した変数を指定してコマンド psedit を実行します。 たとえば、"現在のユーザー、Windows PowerShell ISE" のプロファイルを開くには、「psEdit $profile」と入力します。 `psEdit $profile`

2.  プロファイルに、いくつかの項目を追加します。 たとえば、次の例のように入力します。

    -   コンソール ウィンドウの既定の背景色を青に変更するには、プロファイル ファイルに「`$psISE.Options.OutputPaneBackground = 'blue'`」と入力します。 $psISE 変数の詳細については、「[Windows PowerShell ISE オブジェクト モデル リファレンス](https://technet.microsoft.com/en-us/library/e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c)」を参照してください。.

    -   フォント サイズを 20 に変更するには、プロファイル ファイルに「$psISE.Options.FontSize =20」と入力します。 `$psISE.Options.FontSize =20`

3.  プロファイル ファイルを保存するには、**[ファイル]** メニューの **[保存]** をクリックします。 Windows PowerShell ISE を次に開いた時点で、カスタマイズの内容が適用されます。

## 参照
[about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Windows PowerShell ISE の使用](Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


