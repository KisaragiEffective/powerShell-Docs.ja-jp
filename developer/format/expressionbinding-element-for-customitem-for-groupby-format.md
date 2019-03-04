---
title: GroupBy (形式) の CustomItem ExpressionBinding 要素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854928"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="6e1ea-102">GroupBy の CustomItem の ExpressionBinding 要素 (書式)</span><span class="sxs-lookup"><span data-stu-id="6e1ea-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="6e1ea-103">コントロールによって表示されるデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="6e1ea-104">この要素は、オブジェクトの新しいグループを表示する方法を定義するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6e1ea-105">構成要素 (形式) ViewDefinitions 要素 (形式) 表示要素 (形式) GroupBy 要素の GroupBy (形式) CustomEntry 要素にカスタム コントロールの GroupBy (形式) CustomEntries 要素のカスタム コントロール要素をビュー (形式)GroupBy (形式) の CustomItem の GroupBy (形式) ExpressionBinding 要素 CustomEntry の GroupBy (形式) CustomItem 要素にカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="6e1ea-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e1ea-106">構文</span><span class="sxs-lookup"><span data-stu-id="6e1ea-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e1ea-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-107">Attributes and Elements</span></span>

<span data-ttu-id="6e1ea-108">次のセクションでは、属性、子要素、およびの親要素について説明します、`ExpressionBinding`要素。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e1ea-109">属性</span><span class="sxs-lookup"><span data-stu-id="6e1ea-109">Attributes</span></span>

<span data-ttu-id="6e1ea-110">なし。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e1ea-111">子要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-111">Child Elements</span></span>

|<span data-ttu-id="6e1ea-112">要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-112">Element</span></span>|<span data-ttu-id="6e1ea-113">説明</span><span class="sxs-lookup"><span data-stu-id="6e1ea-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="6e1ea-114">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-114">Optional element.</span></span><br /><br /> <span data-ttu-id="6e1ea-115">このコントロールで使用されるコントロールを定義します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="6e1ea-116">GroupBy (形式) の ExpressionBinding CustomControlName 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="6e1ea-117">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6e1ea-118">一般的なコントロールまたはビューのコントロールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="6e1ea-119">[GroupBy (形式) の ExpressionBinding EnumerateCollection 要素](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy (形式) の ExpressionBinding EnumerateCollection 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="6e1ea-120">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-120">Optional element.</span></span><br /><br /> <span data-ttu-id="6e1ea-121">コレクションの要素が表示されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="6e1ea-122">GroupBy (形式) の ExpressionBinding ItemSelectionCondition 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="6e1ea-123">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-123">Optional element.</span></span><br /><br /> <span data-ttu-id="6e1ea-124">このコントロールを使用するのに必要な条件を定義します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="6e1ea-125">GroupBy (形式) の ExpressionBinding の PropertyName 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="6e1ea-126">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-126">Optional element.</span></span><br /><br /> <span data-ttu-id="6e1ea-127">値を持つが、コントロールによって表示される、.NET プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="6e1ea-128">GroupBy (形式) の ExpressionBinding の ScriptBlock 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="6e1ea-129">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-129">Optional element.</span></span><br /><br /> <span data-ttu-id="6e1ea-130">値を持つが、コントロールによって表示されるスクリプトを指定します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6e1ea-131">親要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-131">Parent Elements</span></span>

|<span data-ttu-id="6e1ea-132">要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-132">Element</span></span>|<span data-ttu-id="6e1ea-133">説明</span><span class="sxs-lookup"><span data-stu-id="6e1ea-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e1ea-134">GroupBy (形式) の CustomEntry CustomItem 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="6e1ea-135">カスタム コントロールのビューで表示するデータと表示方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="6e1ea-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6e1ea-136">参照</span><span class="sxs-lookup"><span data-stu-id="6e1ea-136">See Also</span></span>

[<span data-ttu-id="6e1ea-137">GroupBy (形式) の ExpressionBinding CustomControlName 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6e1ea-138">GroupBy (形式) の ExpressionBinding EnumerateCollection 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6e1ea-139">GroupBy (形式) の ExpressionBinding ItemSelectionCondition 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6e1ea-140">GroupBy (形式) の ExpressionBinding の PropertyName 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6e1ea-141">GroupBy (形式) の ExpressionBinding の ScriptBlock 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6e1ea-142">GroupBy (形式) の CustomEntry CustomItem 要素</span><span class="sxs-lookup"><span data-stu-id="6e1ea-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="6e1ea-143">PowerShell のファイルを書式設定の書き込み</span><span class="sxs-lookup"><span data-stu-id="6e1ea-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
