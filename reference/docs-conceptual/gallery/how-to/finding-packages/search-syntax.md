---
ms.date: 06/12/2017
contributor: JKeithB
keywords: ギャラリー, PowerShell, コマンドレット, PSGallery
title: ギャラリー検索構文
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328453"
---
# <a name="gallery-search-syntax"></a>ギャラリー検索構文

[PowerShell ギャラリーの Web サイト](https://www.powershellgallery.com/)を使って、PowerShell ギャラリーを検索することができます。
PowerShell ギャラリーの Web サイトでは単語、フレーズ、キーワード表現を使用して検索結果を絞り込むテキスト検索ボックスが用意されています。

## <a name="search-by-keywords"></a>キーワードで検索

    dsc azure sql

検索では、3 つのキーワードすべてを含む関連ドキュメントの検索が試みられ、一致するドキュメントが返されます。

## <a name="search-using-phrases-and-keywords"></a>フレーズとキーワードを使用して検索

    "azure sql" deployment

引用符 ("") の間にフレーズを入力すると、個々のキーワードではなく、特定のフレーズの検索に変わります。
一致するドキュメントには通常、大文字と小文字のバリエーション (例: "Azure SQL" など) を含む "azure sql" そのままのフレーズを含み、また通常は 'deployment' という単語も含まれます。

## <a name="filtering-on-fields"></a>フィールドのフィルター処理

特定のパッケージ ID (または 'Id'、'id') を検索するか、検索語句の前にフィールド名を付けて他の特定のフィールドを検索します。

検索可能フィールドは現在、'Id'、'Version'、'Tags'、'Author'、'Owner'、'Functions'、'Cmdlets'、'DscResources'、'PowerShellVersion' です。

[ID とタイトルの間の違いは何ですか。 ID とは、コンソールで使用する名前です。 タイトルとは、検索結果のパッケージ ページの上部に表示される内容です。]

## <a name="examples"></a>例

    ID:PSReadline
    
ID に "PSReadline" が含まれるパッケージを検索します。

    Id:"AzureRM.Profile"

ID フィールドで "AzureRM.Profile" のあるパッケージを検索する別の方法です。

'Id' フィルターは部分文字列の一致のため、次のように検索した場合、

    Id:"azure"

これにより、"AzureRM.Profile" と "Azure.Storage" を含む結果が提供されます。

また、1 つのフィールドで複数のキーワードを検索することもできます。 

    id:azure tags:intellisense

また、二重引用符を使ってフレーズ検索を行うこともできます。

    id:"azure.storage"

DSC タグのあるすべてのパッケージを検索します。

    Tags:DSC

指定した関数のあるすべてのパッケージを検索します。

    Functions:Get-TreeSize

指定したコマンドレットのあるすべてのパッケージを検索します。

    Cmdlets:Get-AzureRmEnvironment

指定した DSC リソース名のあるすべてのパッケージを検索します。

    DscResources:xArchive

指定した PowerShellVersion のあるすべてのパッケージを検索します

    PowerShellVersion:2.0

最後に、'commands' など、サポートされていないフィールドを使用すると、単に無視され、すべてのフィールドが検索されます。 そのため、次のクエリ

    commands:blobs storage

は次のクエリと同じものとして解釈されます。

    blobs storage
