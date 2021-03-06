---
title: CustomControl の CustomEntries 要素のビュー (形式) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364081"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>View の CustomControl の CustomEntries 要素 (書式)

カスタムコントロールビューの定義を提供します。 カスタムコントロールビューでは、1つまたは複数の定義を指定する必要があります。

Configuration 要素 (Format) ViewDefinitions 要素 (書式) ビュー要素 (Format) CustomControl Element (Format) CustomControl for View (Format) の CustomEntries 要素

## <a name="syntax"></a>構文

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>属性と要素

次のセクションでは、`CustomControlEntries` 要素の属性、子要素、および親要素について説明します。 1つまたは複数の子要素を指定する必要があります。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

|要素|[説明]|
|-------------|-----------------|
|[View (Format) の CustomEntries の CustomEntry 要素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|必須の要素です。<br /><br /> カスタムコントロールビューの定義を提供します。|

### <a name="parent-elements"></a>親要素

|要素|[説明]|
|-------------|-----------------|
|[View (Format) の CustomControl 要素](./customcontrol-element-for-view-format.md)|必須の要素です。<br /><br /> ビューのカスタムコントロール形式を定義します。|

## <a name="remarks"></a>コメント

ほとんどの場合、コントロールには定義が1つだけあります。定義は1つの `CustomEntry` 要素で定義されます。 ただし、同じコントロールを使用して異なる .NET オブジェクトを表示する場合は、複数の定義を含めることができます。 このような場合は、オブジェクトまたはオブジェクトのセットごとに `CustomEntry` 要素を定義できます。

## <a name="see-also"></a>参照

[View (Format) の CustomControl 要素](./customcontrol-element-for-view-format.md)

[View (Format) の CustomEntries の CustomEntry 要素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[PowerShell フォーマットファイルの作成](./writing-a-powershell-formatting-file.md)
