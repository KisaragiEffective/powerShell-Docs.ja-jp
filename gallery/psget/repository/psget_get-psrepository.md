---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "ギャラリー, PowerShell, コマンドレット, PSGet"
title: Get-PSRepository
ms.openlocfilehash: 96f87428312c233757aa5fcae405a192aadff385
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="get-psrepository" class="xliff"></a>

# Get-PSRepository

コンピューター上の登録されているリポジトリを取得します。

<a id="description" class="xliff"></a>

## 説明

Get-PSRepository コマンドレットでは、コンピューター上の現在のユーザーに対して登録されている PowerShell モジュール リポジトリを取得します。

登録されている各リポジトリに対して、Get-PSRepository は PSRepository オブジェクトを返します。これは必要に応じて登録済みのリポジトリの登録を解除するための Unregister-PSRepository にパイプできます。

<a id="cmdlet-syntax" class="xliff"></a>

## コマンドレット構文
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>

## コマンドレット オンライン ヘルプ リファレンス

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

<a id="example-commands" class="xliff"></a>

## コマンド例

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

