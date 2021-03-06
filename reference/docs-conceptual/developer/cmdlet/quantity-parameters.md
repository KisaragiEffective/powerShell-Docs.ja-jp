---
title: Quantity パラメーター |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369561"
---
# <a name="quantity-parameters"></a>数量のパラメーター

次の表に、quantity パラメーターの推奨される名前と機能を示します。

|パラメーター|機能|
|---|---|
|**All**<br>データ型: ブール値|このパラメーターは、リソースの既定のサブセットではなく、すべてのリソースを処理する必要があることを `true` に示すために実装します。 `false` がリソースのサブセットを示すように、このパラメーターを実装します。|
|**Allocation**<br>データ型: Int32|割り当てられる項目の数をユーザーが指定できるように、このパラメーターを実装します。|
|**ブロック数**<br>データ型: Int64|ユーザーがブロックカウントを指定できるように、このパラメーターを実装します。|
|**Count**<br>データ型: Int64|ユーザーがカウントを指定できるように、このパラメーターを実装します。|
|**Scope**<br>データ型: キーワード|操作するスコープをユーザーが指定できるように、このパラメーターを実装します。|

## <a name="see-also"></a>参照

[コマンドレットのパラメーター](./cmdlet-parameters.md)

[Windows PowerShell コマンドレットの記述](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
