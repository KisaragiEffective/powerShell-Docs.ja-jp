---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "DSC Script リソース"
ms.openlocfilehash: 3824cbf48d980069b923d91e1fa24739e5d4e617
ms.sourcegitcommit: 378c7ed4e8c8c1c5fe71417b9ba672a4c990630b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="dsc-script-resource"></a>DSC Script リソース

 
> 適用先: Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) の **Script** リソースは、ターゲット ノードで Windows PowerShell スクリプトのブロックを実行するためのメカニズムを備えています。 `Script` リソースには、`GetScript`、`SetScript`、`TestScript` プロパティがあります。 このプロパティは、各ターゲット ノードに対して実行されるスクリプト ブロックに設定する必要があります。 

`GetScript` スクリプト ブロックは、現在のノードの状態を表すハッシュ テーブルを返します。 ハッシュ テーブルに入るキーは 1 つだけです (`Result`)。値の型は `String` になります。 何も返す必要はありません。 DSC は、このスクリプト ブロックの出力を処理しません。

`TestScript` スクリプト ブロックは、現在のノードを変更する必要があるかどうかを判定します。 ノードが最新の場合は `$true` を返します。 ノードの構成が最新ではなく、`SetScript` スクリプト ブロックで更新する必要がある場合は、`$false` が返されます。 `TestScript` スクリプト ブロックは DSC によって呼び出されます。

`SetScript` スクリプト ブロックはノードを変更します。 これは、`TestScript` ブロックから `$false` が返された場合に DSC によって呼び出されます。

`GetScript`、`TestScript`、または `SetScript` スクリプト ブロックで構成スクリプトの変数を使用する必要がある場合は、`$using:` スコープを使用します (例については、以下を参照してください)。


## <a name="syntax"></a>構文

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>プロパティ

|  プロパティ  |  説明   | 
|---|---| 
| GetScript| [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) コマンドレットを呼び出すと実行される Windows PowerShell スクリプトのブロックを提供します。 このブロックでは、ハッシュ テーブルを返す必要があります。 ハッシュ テーブルに入るキーは 1 つだけです (**結果**)。値の型は**文字列**になります。| 
| SetScript| Windows PowerShell スクリプトのブロックを提供します。 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) コマンドレットを呼び出すと、**TestScript** ブロックが最初に実行されます。 **TestScript** ブロックが **$false** を返した場合は、**SetScript** ブロックが実行されます。 **TestScript** ブロックが **$true** を返した場合は、**SetScript** ブロックが実行されません。| 
| TestScript| Windows PowerShell スクリプトのブロックを提供します。 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) コマンドレットを呼び出すと、このブロックが実行されます。 これが **$false** を返した場合は、SetScript ブロックが実行されます。 これが **$true** を返した場合は、SetScript ブロックが実行されません。 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) コマンドレットを呼び出すと、**TestScript** ブロックも実行されます。 ただし、この場合、TestScript ブロックがどのような値を返すかに関係なく、**SetScript** ブロックは実行されません。 **TestScript** ブロックは、実際の構成が現在の Desired State Configuration と一致する場合には True を返す必要があり、一致しない場合には False を返す必要があります  (現在の Desired State Configuration は DSC を使用しているノードに適用された最後の構成です)。| 
| Credential| 資格情報が必要な場合、このスクリプトの実行に使用する資格情報を示します。| 
| DependsOn| このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が **ResourceName** で、そのタイプが **ResourceType** である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。

## <a name="example-1"></a>例 1
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a>例 2
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

このリソースは、構成のバージョンをテキスト ファイルに書き込んでいます。 このバージョンはクライアント コンピューターで利用できますが、いずれのノードでも使用できないため、PowerShell の `using` スコープを指定して、`Script` リソースのスクリプト ブロックそれぞれに渡す必要があります。 ノードの MOF ファイルを生成すると、`$version` 変数の値は、クライアント コンピューター上のテキスト ファイルから読み取られます。 各スクリプト ブロックの `$using:version` 変数は、DSC によって `$version` 変数の値に置き換えられます。

