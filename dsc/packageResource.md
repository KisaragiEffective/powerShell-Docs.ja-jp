---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "DSC Package リソース"
ms.openlocfilehash: f7bcbd387db422037614feee7c4a00d93b3cec4e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="dsc-package-resource" class="xliff"></a>

# DSC Package リソース

> 適用先: Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) の **Package** リソースは、Windows インストーラーや setup.exe パッケージなど、ターゲット ノードでパッケージをインストールまたはアンインストールするメカニズムを備えています。

<a id="syntax" class="xliff"></a>

## 構文

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

<a id="properties" class="xliff"></a>

## プロパティ
|  プロパティ  |  説明   | 
|---|---| 
| 名前| 特定の状態を保証するパッケージの名前を示します。| 
| パス| パッケージが存在するパスを示します。| 
| ProductId| パッケージを一意に識別する製品 ID を示します。| 
| 引数| 指定されたとおりにパッケージに渡される引数の文字列を一覧表示します。| 
| Credential| リモート ソースのパッケージへのアクセスを提供します。 このプロパティは、パッケージのインストールには使用されません。 パッケージは常に、ローカル システムにインストールされます。| 
| Ensure| パッケージがインストールされるかどうかを示します。 このプロパティを "Absent" に設定すると、パッケージはインストールされません (またはパッケージがインストールされている場合はアンインストールされます)。 パッケージがインストールされるようにするには、"Present" に設定します (既定値)。| 
| LogPath| プロバイダーがパッケージをインストールまたはアンインストールするためのログ ファイルを保存する場所の完全パスを示します。| 
| DependsOn | このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が **ResourceName** で、そのタイプが **ResourceType** である場合、このプロパティを使用する構文は DependsOn = "[ResourceType]ResourceName" になります。| 
| ReturnCode| 想定されるリターン コードを示します。 実際のリターン コードがここで指定される想定される値と一致しない場合、構成はエラーを返します。| 

<a id="example" class="xliff"></a>

## 例

この例では、指定されたパスに配置され、指定された製品 ID が割り当てられている .msi インストーラーを実行します。

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    } 
}
```

