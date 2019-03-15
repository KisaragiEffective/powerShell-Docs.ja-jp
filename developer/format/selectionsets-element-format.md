---
title: SelectionSets 要素 (式) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853568"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="45765-102">SelectionSets 要素 (書式)</span><span class="sxs-lookup"><span data-stu-id="45765-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="45765-103">書式設定ファイルのすべてのビューで使用できる .NET オブジェクトの共通セットを定義します。</span><span class="sxs-lookup"><span data-stu-id="45765-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="45765-104">ビューおよび書式設定ファイルのコントロールは、選択範囲のセットの名前のみを使用してオブジェクトの完全なセットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="45765-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="45765-105">構成要素 SelectionSets 要素の形式</span><span class="sxs-lookup"><span data-stu-id="45765-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="45765-106">構文</span><span class="sxs-lookup"><span data-stu-id="45765-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45765-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="45765-107">Attributes and Elements</span></span>

<span data-ttu-id="45765-108">次のセクションでは、属性、子要素、およびの親要素について説明します、`SelectionSets`要素。</span><span class="sxs-lookup"><span data-stu-id="45765-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="45765-109">各子要素は、セットの名前で参照できるオブジェクトのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="45765-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="45765-110">子要素の順序は大きくありません。</span><span class="sxs-lookup"><span data-stu-id="45765-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="45765-111">属性</span><span class="sxs-lookup"><span data-stu-id="45765-111">Attributes</span></span>

<span data-ttu-id="45765-112">なし。</span><span class="sxs-lookup"><span data-stu-id="45765-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45765-113">子要素</span><span class="sxs-lookup"><span data-stu-id="45765-113">Child Elements</span></span>

|<span data-ttu-id="45765-114">要素</span><span class="sxs-lookup"><span data-stu-id="45765-114">Element</span></span>|<span data-ttu-id="45765-115">説明</span><span class="sxs-lookup"><span data-stu-id="45765-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45765-116">SelectionSet 要素 (形式)</span><span class="sxs-lookup"><span data-stu-id="45765-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="45765-117">必須の要素。</span><span class="sxs-lookup"><span data-stu-id="45765-117">Required element.</span></span><br /><br /> <span data-ttu-id="45765-118">セットの名前で参照できる .NET オブジェクトの 1 つのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="45765-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="45765-119">親要素</span><span class="sxs-lookup"><span data-stu-id="45765-119">Parent Elements</span></span>

|<span data-ttu-id="45765-120">要素</span><span class="sxs-lookup"><span data-stu-id="45765-120">Element</span></span>|<span data-ttu-id="45765-121">説明</span><span class="sxs-lookup"><span data-stu-id="45765-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45765-122">構成要素</span><span class="sxs-lookup"><span data-stu-id="45765-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="45765-123">書式設定ファイルの最上位の要素を表します。</span><span class="sxs-lookup"><span data-stu-id="45765-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45765-124">コメント</span><span class="sxs-lookup"><span data-stu-id="45765-124">Remarks</span></span>

<span data-ttu-id="45765-125">継承によって関連付けられているオブジェクトのセットなどの 1 つの名前を使用して参照する関連のオブジェクトのセットがある場合は、選択範囲のセットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="45765-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="45765-126">ビューを定義するときに、それぞれのビュー内のすべてのオブジェクトを一覧表示するのではなく設定の選択範囲の名前を使用してオブジェクトのセットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="45765-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="45765-127">一般的な選択範囲のセットは、書式設定ファイルのビューまたはビューの定義を定義するときに、名前によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="45765-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="45765-128">このような場合、`SelectionSetName`の子要素、`ViewSelectedBy`と`EntrySelectedBy`要素を使用するデータセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="45765-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="45765-129">選択範囲のセットの詳細については、次を参照してください。[オブジェクト設定を定義する](./defining-selection-sets.md)します。</span><span class="sxs-lookup"><span data-stu-id="45765-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45765-130">参照</span><span class="sxs-lookup"><span data-stu-id="45765-130">See Also</span></span>

[<span data-ttu-id="45765-131">構成要素</span><span class="sxs-lookup"><span data-stu-id="45765-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="45765-132">選択範囲のセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="45765-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="45765-133">SelectionSet 要素 (形式)</span><span class="sxs-lookup"><span data-stu-id="45765-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="45765-134">PowerShell のファイルを書式設定の書き込み</span><span class="sxs-lookup"><span data-stu-id="45765-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)