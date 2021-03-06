---
title: モジュールとスナップイン |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811661"
---
# <a name="modules-and-snap-ins"></a>モジュールとスナップイン

コマンドレットは、(Windows PowerShell 2.0 によって導入された) モジュールまたはスナップインを使用してセッションに追加できます。コマンドレットをセッションに追加すると、ホストアプリケーションまたはコマンドラインで対話形式で実行できます。

次の理由により、セッションにコマンドレットを追加するための配信方法としてモジュールを使用することをお勧めします。

- モジュールを使用すると、コマンドレットが定義されているアセンブリを読み込むことによってコマンドレットを追加できます。 スナップインクラスを実装する必要はありません。

- モジュールを使用すると、変数、関数、スクリプト、型、書式設定ファイルなどの他のリソースを追加できます。

- スナップインは、セッションにコマンドレットとプロバイダーを追加するためにのみ使用できます。

## <a name="see-also"></a>参照

[Windows PowerShell モジュールを記述する](writing-a-windows-powershell-module.md)

[Writing a Windows PowerShell Cmdlet (Windows PowerShell コマンドレットの記述)](../cmdlet/cmdlet-overview.md)
