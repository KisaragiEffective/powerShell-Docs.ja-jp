---
title: "DSC WindowsOptionalFeatureSet リソース"
ms.date: 2016-05-24
keywords: PowerShell, DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 1fab04dfcd4ce927bbe526b93c826cf3749a42a5
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet リソース

> 適用先: Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) の **WindowsOptionalFeatureSet** リソースは、オプション機能をターゲット ノードで有効にするためのメカニズムを備えています。 このリソースは[複合リソース](authoringResourceComposite.md)であり、`Name` プロパティに指定されている機能ごとに [WindowsOptionalFeature リソース](windowsOptionalFeatureResource.md)を呼び出します。

Windows のオプション機能の数を同じ状態に構成するときにこのリソースを使用します。

## <a name="syntax"></a>構文

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>プロパティ

|  プロパティ  |  説明   | 
|---|---| 
| 名前| 有効または無効にする機能の名前を示します。| 
| Ensure| 機能が有効化かどうかを指定します。 機能を確実に有効にするには、このプロパティを "Present" に設定します。機能を確実に無効にするには、このプロパティを "Absent" に設定します。|
| ソース| 実装されていません。|
| NoWindowsUpdateCheck| 機能を有効にするソース ファイルを検索するとき、DISM が Windows Update (WU) を確認するかどうかを指定します。 $true の場合、DISM は WU を確認しません。|
| RemoveFilesOnDisable| **[$true]** に設定すると、無効時に (つまり、**[Ensure]** が "Absent" に設定されているとき)、機能に関連付けられているすべてのファイルが削除されます。|
| ログ レベル| ログに表示される最大の出力レベル。 有効な値は "ErrorsOnly" (エラーのみが記録されます)、"ErrorsAndWarning" (エラーと警告が記録されます)、"ErrorsAndWarningAndInformation" (エラー、警告、デバッグ情報が記録されます) です。|
| LogPath| リソース プロバイダーの操作を記録するログ ファイルへのパス。| 
| DependsOn| このリソースを構成する前に、他のリソースの構成を実行する必要があることを指定します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が __ResourceName__ で、そのタイプが __ResourceType__ である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。| 
 



