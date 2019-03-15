---
title: HelpInfo XML バージョン番号を設定する方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: d69e8a734aa96ff9b7911815fb43b81103548b59
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794350"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="1abcd-102">HelpInfo XML バージョン番号を設定する方法</span><span class="sxs-lookup"><span data-stu-id="1abcd-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="1abcd-103">このトピックでは、設定、および一般的「HelpInfo XML ファイル」と呼ばれる、更新可能なヘルプ情報ファイルにバージョン番号を大きく方法を説明します</span><span class="sxs-lookup"><span data-stu-id="1abcd-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="1abcd-104">HelpInfo XML バージョン番号を設定する方法</span><span class="sxs-lookup"><span data-stu-id="1abcd-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="1abcd-105">HelpInfo XML ファイルにバージョン番号は、更新可能なヘルプの操作に重要です。</span><span class="sxs-lookup"><span data-stu-id="1abcd-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="1abcd-106">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)と[Save-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)コマンドレットがリモートの HelpInfo XML ファイルでの UI カルチャのバージョン番号がの UI カルチャ、バージョン番号より大きい場合にのみ、新しいヘルプ ファイルをダウンロードしますローカルの HelpInfo XML、またはローカルの HelpInfo XML ファイルがないです。</span><span class="sxs-lookup"><span data-stu-id="1abcd-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="1abcd-107">HelpInfo XML ファイルで定義されている 4 つの部分のバージョン番号を使用して、 **System.Version** Microsoft .NET Framework のクラス。</span><span class="sxs-lookup"><span data-stu-id="1abcd-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="1abcd-108">形式は`N1.N2.N3.N4`します。</span><span class="sxs-lookup"><span data-stu-id="1abcd-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="1abcd-109">モジュールの作成者は、任意のバージョン番号付けは許可されているスキームを使用できます、 **System.Version**クラス。</span><span class="sxs-lookup"><span data-stu-id="1abcd-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="1abcd-110">更新可能なヘルプが必要ですそれだけで、バージョン番号の UI カルチャの増加がで指定された場所にその UI カルチャ用の CAB ファイルの新しいバージョンがアップロードされたときに、 **HelpContentURI** HelpInfo XML ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="1abcd-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="1abcd-111">次の例は、ドイツ (DE-DE) UI カルチャ、バージョンが 2.15.0.10 の HelpInfo XML ファイルの要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="1abcd-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="1abcd-112">UI カルチャのバージョン番号は、UI カルチャ用の CAB ファイルのバージョンを反映します。</span><span class="sxs-lookup"><span data-stu-id="1abcd-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="1abcd-113">全体の CAB ファイルにバージョン番号が適用されます。</span><span class="sxs-lookup"><span data-stu-id="1abcd-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="1abcd-114">CAB ファイルに別のファイルの異なるバージョン番号を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="1abcd-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="1abcd-115">各 UI カルチャのバージョン番号は、個別が評価され、モジュールがサポートするその他の UI カルチャのバージョン番号は関係なく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1abcd-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>