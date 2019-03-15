---
title: GetProc03 (VB.NET) サンプル コード |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854638"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="fec4d-102">GetProc03 (VB.NET) サンプル コード</span><span class="sxs-lookup"><span data-stu-id="fec4d-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="fec4d-103">次のコードの実装を示しています、`Get-Process`パイプライン処理の入力を受け入れることができるコマンドレット。</span><span class="sxs-lookup"><span data-stu-id="fec4d-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="fec4d-104">この実装を定義、`Name`をパイプラインの入力を受け取るパラメーターが、指定された名前に基づいて、ローカル コンピューターからプロセス情報を取得しを使用して、 [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)パイプラインにオブジェクトを送信するため、出力メカニズムとしてのメソッド。</span><span class="sxs-lookup"><span data-stu-id="fec4d-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fec4d-105">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="fec4d-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->