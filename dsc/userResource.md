---
title: "DSC User リソース"
ms.date: 2016-05-16
keywords: PowerShell, DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 0953000ba7930116679e4371f6acad5298725fdb
ms.sourcegitcommit: 55b2457a19a2fa679fda8dc17a747ef21a98adc1
translationtype: HT
---
#<a name="dsc-user-resource"></a>DSC User リソース#

 
>適用先: Windows PowerShell 4.0、Windows PowerShell 5.0


PowerShell Desired State Configuration (DSC) の __User__ リソースは、ターゲット ノード上でローカル ユーザー アカウントを管理するためのメカニズムを備えています。


##<a name="syntax"></a>構文##

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>プロパティ
|  プロパティ  |  説明   | 
|---|---| 
| UserName| 特定の状態を保証するアカウント名を示します。| 
| 説明| ユーザー アカウントのために使用する説明を示します。| 
| 無効| アカウントが有効になっているかどうかを示します。 このアカウントを無効にするには、このプロパティを __$true__ に設定し、有効にするには __$false__ に設定します。| 
| Ensure| アカウントが存在するかどうかを示します。 このアカウントが存在することを保証するには、このプロパティを "Present" に設定し、アカウントが存在しないことを保証するには、"Absent" に設定します。| 
| FullName| ユーザー アカウントのために使用する完全名の文字列を表します。| 
| Password| このアカウントに使用するパスワードを示します。 | 
| PasswordChangeNotAllowed| ユーザーがパスワードを変更できるかどうかを示します。 ユーザーがパスワードを変更できないようにするには、このプロパティを __$true__ に設定し、ユーザーがパスワードを変更できるようにするには、__$false__ に設定します。 既定値は __$false__ です。| 
| PasswordChangeRequired| ユーザーが次回ログオンしたときにパスワードを変更する必要があるかどうかを示します。 ユーザーがパスワードを変更する必要がある場合は、このプロパティを __$true__ に設定します。 既定値は __$true__ です。| 
| PasswordNeverExpires| パスワードの有効期限が切れるかどうかを示します。 このアカウントのパスワードの有効期限が切れないようにするにはこのプロパティを __$true__ に設定し、パスワードの有効期限が切れるようにする場合は __$false__ を設定します。 既定値は __$false__ です。| 
| DependsOn | このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が __ResourceName__ で、そのタイプが __ResourceType__ である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。| 

## <a name="example"></a>例

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

