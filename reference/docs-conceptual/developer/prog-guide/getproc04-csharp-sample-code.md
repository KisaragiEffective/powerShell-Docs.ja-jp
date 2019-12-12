---
title: GetProc04 (C#) Sample Code |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 0ca2ccc5188f0c1784ec14ac204c1fdd624c2e66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416116"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="bb8b4-102">GetProc04 (C#) サンプル コード</span><span class="sxs-lookup"><span data-stu-id="bb8b4-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="bb8b4-103">次のコードは、終了しないエラーを報告する `Get-Process` コマンドレットの実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="bb8b4-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="bb8b4-104">この実装では、 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)メソッドを呼び出して、終了しないエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="bb8b4-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="bb8b4-105">この getprov04.cs コマンドレットC#のソースファイル () をダウンロードするには、Microsoft Windows Software Development Kit For windows Vista および .NET Framework 3.0 ランタイムコンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb8b4-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bb8b4-106">ダウンロードの手順については、「 [Windows powershell をインストールする方法」および「Windows POWERSHELL SDK をダウンロードする方法](/powershell/scripting/developer/installing-the-windows-powershell-sdk)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb8b4-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="bb8b4-107">ダウンロードしたソースファイルは、 **\<PowerShell Samples >** ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="bb8b4-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bb8b4-108">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="bb8b4-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="bb8b4-109">参照</span><span class="sxs-lookup"><span data-stu-id="bb8b4-109">See Also</span></span>

[<span data-ttu-id="bb8b4-110">Windows PowerShell プログラマーズガイド</span><span class="sxs-lookup"><span data-stu-id="bb8b4-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="bb8b4-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bb8b4-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
