---
title: ListControl (Format) の ListEntry の ListItems 要素Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362741"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl の ListEntry の ListItems 要素 (書式)

リストビューの行に値が表示されるプロパティとスクリプトを定義します。

Configuration 要素 (Format) ViewDefinitions 要素 (書式) ビュー要素 (Format) ListControl 要素 (format) ListControl (format) ListItems 要素のリストコントロール (format) ListEntry 要素の ListEntries 要素を ListControl (Format) に設定します。

## <a name="syntax"></a>構文

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>属性と要素

次のセクションでは、`ListItems` 要素の属性、子要素、および親要素について説明します。 指定できる子要素の数に制限はありません。 子要素の順序は、リストビューに表示される値の順序を定義します。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

|要素|[説明]|
|-------------|-----------------|
|[ListControl の ListItem 要素 (形式)](./listitem-element-for-listitems-for-listcontrol-format.md)|必須の要素です。<br /><br /> リストビューによって表示される値を持つプロパティまたはスクリプトを定義します。|

### <a name="parent-elements"></a>親要素

|要素|[説明]|
|-------------|-----------------|
|[ListControl の ListEntry 要素 (形式)](./listentry-element-for-listcontrol-format.md)|リストビューの定義を提供します。|

## <a name="remarks"></a>コメント

この種類のビューの詳細については、「[リストビューの作成](./creating-a-list-view.md)」を参照してください。

## <a name="example"></a>例

この例は、リストビューの3つの行を定義する XML 要素を示しています。

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>参照

[ListControl の ListEntry 要素 (形式)](./listentry-element-for-listcontrol-format.md)

[ListControl の ListItem 要素 (形式)](./listitem-element-for-listitems-for-listcontrol-format.md)

[リストビューの作成](./creating-a-list-view.md)

[PowerShell フォーマットファイルの作成](./writing-a-powershell-formatting-file.md)
