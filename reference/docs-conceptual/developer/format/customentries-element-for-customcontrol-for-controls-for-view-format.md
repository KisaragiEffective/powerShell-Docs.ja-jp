---
title: View (Format) 用のコントロールの CustomControl の CustomEntries 要素Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368811"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="5f267-102">View の Controls の CustomControl の CustomEntries 要素 (書式)</span><span class="sxs-lookup"><span data-stu-id="5f267-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="5f267-103">コントロールの定義を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f267-103">Provides the definitions for the control.</span></span> <span data-ttu-id="5f267-104">この要素は、ビューで使用できるコントロールを定義するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f267-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5f267-105">Configuration 要素 (Format) ViewDefinitions 要素 (書式) ビュー要素 (書式) コントロールの要素 (書式) コントロールのコントロール要素を表示するためのコントロール (format) の CustomControl 要素のコントロール要素ビューのコントロールの CustomControl (形式)</span><span class="sxs-lookup"><span data-stu-id="5f267-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5f267-106">構文</span><span class="sxs-lookup"><span data-stu-id="5f267-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5f267-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="5f267-107">Attributes and Elements</span></span>

<span data-ttu-id="5f267-108">次のセクションでは、`CustomEntries` 要素の属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f267-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="5f267-109">指定できる子要素の数に上限はありません。</span><span class="sxs-lookup"><span data-stu-id="5f267-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="5f267-110">属性</span><span class="sxs-lookup"><span data-stu-id="5f267-110">Attributes</span></span>

<span data-ttu-id="5f267-111">なし。</span><span class="sxs-lookup"><span data-stu-id="5f267-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5f267-112">子要素</span><span class="sxs-lookup"><span data-stu-id="5f267-112">Child Elements</span></span>

|<span data-ttu-id="5f267-113">要素</span><span class="sxs-lookup"><span data-stu-id="5f267-113">Element</span></span>|<span data-ttu-id="5f267-114">説明</span><span class="sxs-lookup"><span data-stu-id="5f267-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f267-115">ビューのコントロール (Format) の CustomEntry 要素</span><span class="sxs-lookup"><span data-stu-id="5f267-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="5f267-116">必須の要素です。</span><span class="sxs-lookup"><span data-stu-id="5f267-116">Required element.</span></span><br /><br /> <span data-ttu-id="5f267-117">コントロールの定義を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f267-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5f267-118">親要素</span><span class="sxs-lookup"><span data-stu-id="5f267-118">Parent Elements</span></span>

|<span data-ttu-id="5f267-119">要素</span><span class="sxs-lookup"><span data-stu-id="5f267-119">Element</span></span>|<span data-ttu-id="5f267-120">説明</span><span class="sxs-lookup"><span data-stu-id="5f267-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f267-121">View (Format) コントロールのコントロールの CustomControl 要素</span><span class="sxs-lookup"><span data-stu-id="5f267-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="5f267-122">ビューによって使用されるコントロールを定義します。</span><span class="sxs-lookup"><span data-stu-id="5f267-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f267-123">コメント</span><span class="sxs-lookup"><span data-stu-id="5f267-123">Remarks</span></span>

<span data-ttu-id="5f267-124">ほとんどの場合、コントロールの定義は1つだけであり、1つの `CustomEntry` 要素で指定されます。</span><span class="sxs-lookup"><span data-stu-id="5f267-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="5f267-125">ただし、同じコントロールを使用して異なる .NET オブジェクトを表示する場合は、複数の定義を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f267-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="5f267-126">このような場合は、オブジェクトまたはオブジェクトのセットごとに `CustomEntry` 要素を定義できます。</span><span class="sxs-lookup"><span data-stu-id="5f267-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f267-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f267-127">See Also</span></span>

[<span data-ttu-id="5f267-128">ビューのコントロール (Format) の CustomEntry 要素</span><span class="sxs-lookup"><span data-stu-id="5f267-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="5f267-129">View (Format) コントロールのコントロールの CustomControl 要素</span><span class="sxs-lookup"><span data-stu-id="5f267-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="5f267-130">PowerShell フォーマットファイルの作成</span><span class="sxs-lookup"><span data-stu-id="5f267-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
