---
title: コマンドレット内でスクリプトを起動する方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855838"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="e691e-102">コマンドレット内でスクリプトを呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="e691e-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="e691e-103">この例では、コマンドレットに指定されているスクリプトを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e691e-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="e691e-104">スクリプトは、コマンドレットによって実行され、結果は、のコレクションとしてコマンドレットに返されます[System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e691e-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="e691e-105">スクリプト ブロックを呼び出す</span><span class="sxs-lookup"><span data-stu-id="e691e-105">To invoke a script block</span></span>

1. <span data-ttu-id="e691e-106">コマンドは、スクリプト ブロックをコマンドレットに渡されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e691e-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="e691e-107">スクリプト ブロックが指定された場合、コマンドは、必要なパラメーターを持つスクリプト ブロックを起動します。</span><span class="sxs-lookup"><span data-stu-id="e691e-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="e691e-108">スクリプトがの返されたコレクションを反復処理し、 [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)オブジェクトし、必要な操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="e691e-108">Then, the script iterates through the returned collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="e691e-109">参照</span><span class="sxs-lookup"><span data-stu-id="e691e-109">See Also</span></span>

[<span data-ttu-id="e691e-110">Windows PowerShell コマンドレットの記述</span><span class="sxs-lookup"><span data-stu-id="e691e-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)