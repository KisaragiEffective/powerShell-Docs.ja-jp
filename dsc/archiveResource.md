---
ms.date: 06/12/2017
keywords: DSC, PowerShell, 構成, セットアップ
title: DSC Archive リソース
ms.openlocfilehash: 458b4f0f20dc96dab62e709183c25ff57d971aae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219472"
---
# <a name="dsc-archive-resource"></a>DSC Archive リソース

> 適用先: Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) の Archive リソースは、特定のパスでアーカイブ (.zip) ファイルをアンパックするメカニズムを備えています。

## <a name="syntax"></a>構文
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>プロパティ

|  プロパティ  |  説明   |
|---|---|
| Destination| アーカイブ コンテンツが抽出されることを保証する場所を指定します。|
| パス| アーカイブ ファイルのソース パスを指定します。|
| __チェックサム__| 2 つのファイルが同じであるかどうかを決定するときに使用するタイプを定義します。 __Checksum__ が指定されていない場合、ファイルまたはディレクトリ名のみが比較に使用されます。 有効な値は、SHA-1、SHA-256、SHA-512、createdDate、modifiedDate、none (既定) です。 __Validate__ を指定せずに __Checksum__ を指定した場合、構成は失敗します。|
| Ensure| アーカイブのコンテンツが __Destination__ に存在するかどうかを決定します。 コンテンツが存在することを保証するには、このプロパティを __Present__ に設定します。 コンテンツが存在しないことを保証するには、__Absent__ に設定します。 既定値は __Present__ です。|
| DependsOn | このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が ResourceName で、そのタイプが __ResourceType__ である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。|
| [検証]| Checksum プロパティを使用して、アーカイブが署名と一致するかどうかを確認します。 Validate を指定せずに Checksum を指定した場合、構成は失敗します。 Checksum を指定せずに Validate を指定した場合、SHA-256 チェックサムが既定で使用されます。|
| Force| 特定のファイル操作 (ファイルの上書き、空でないディレクトリの削除など) によって、エラーが発生します。 Force プロパティを使用すると、このようなエラーが上書きされます。 既定値は False です。|

## <a name="example"></a>例

次の例は、Archive リソースを使用して、Test.zip というアーカイブ ファイルのコンテンツが指定した宛先に存在し、抽出されていることを保証する方法を示します。

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```