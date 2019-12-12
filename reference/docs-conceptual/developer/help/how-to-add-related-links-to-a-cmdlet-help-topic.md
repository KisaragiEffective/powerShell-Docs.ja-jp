---
title: コマンドレットに関連するリンクを追加する方法に関するヘルプトピック |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361221"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="9b2a9-102">コマンドレットのヘルプ トピックに関連リンクを追加する方法</span><span class="sxs-lookup"><span data-stu-id="9b2a9-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="9b2a9-103">このセクションでは、Windows PowerShell®コマンドレットのヘルプトピックに関連するその他のコンテンツへの参照を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b2a9-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="9b2a9-104">これらの参照はコマンドウィンドウに表示されるため、参照先のコンテンツに直接リンクされません。</span><span class="sxs-lookup"><span data-stu-id="9b2a9-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="9b2a9-105">Windows PowerShell®に含まれているコマンドレットのヘルプトピックでは、これらのリンクでは、他のコマンドレット、概念コンテンツ ("about_")、および Windows PowerShell®に関連しないその他のドキュメントやヘルプファイルを参照しています。</span><span class="sxs-lookup"><span data-stu-id="9b2a9-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="9b2a9-106">次の XML は、関連トピックへの2つの参照を含む、関係リンクノードを追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b2a9-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



