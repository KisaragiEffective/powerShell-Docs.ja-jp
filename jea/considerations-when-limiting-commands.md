---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "コマンドの制限時の考慮事項"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 9f3f79a29e0fb7ec5a5111284bb7985548e17749

---

### コマンドの制限時の考慮事項
この手順では、考慮すべき重量な点が 1 つあります。
JEA を通じて公開されるすべての機能は、管理者によって制限された領域に配置することが重要です。
管理者以外のユーザーは、JEA エンドポイント経由で使用されるスクリプトを変更する機能を持つことはできません。

関連する注意事項として、JEA ユーザーに、その JEA セッション内で JEA 構成やホワイトリストに載ったスクリプトを上書きする権限を付与しないでください。
`Copy-Item` のようなコマンドを公開するときは十分に注意してください。




<!--HONumber=Jun16_HO4-->


