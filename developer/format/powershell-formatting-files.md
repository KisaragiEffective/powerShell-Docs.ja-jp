---
title: Windows PowerShell の書式設定ファイル |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 49344d32dfcef36a904772b4a7237646a63cb12a
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794639"
---
# <a name="windows-powershell-formatting-files"></a><span data-ttu-id="ced1f-102">Windows PowerShell 書式設定ファイル</span><span class="sxs-lookup"><span data-stu-id="ced1f-102">Windows PowerShell Formatting Files</span></span>

<span data-ttu-id="ced1f-103">Windows PowerShell には、いくつかの書式設定ファイルが用意されています (. format.ps1xml) のインストール ディレクトリ内にある (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="ced1f-103">Windows PowerShell provides several formatting files (.format.ps1xml) that are located in the installation directory (`$pshome`).</span></span> <span data-ttu-id="ced1f-104">これらの各ファイルには、特定の一連の .NET オブジェクトの既定の表示を定義します。</span><span class="sxs-lookup"><span data-stu-id="ced1f-104">Each of these files defines the default display for a specific set of .NET objects.</span></span> <span data-ttu-id="ced1f-105">これらのファイルを変更しない必要があります。</span><span class="sxs-lookup"><span data-stu-id="ced1f-105">These files should never be changed.</span></span> <span data-ttu-id="ced1f-106">ただし、独自のカスタム書式設定ファイルを作成するための参照としてそれらを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ced1f-106">However, you can use them as a reference for creating your own custom formatting files.</span></span>

<span data-ttu-id="ced1f-107">Certificate.Format.ps1xml は、x.509 証明書などの証明書ストアと証明書ストア内のオブジェクトの表示を定義します。</span><span class="sxs-lookup"><span data-stu-id="ced1f-107">Certificate.Format.ps1xml Defines the display of objects in the Certificate store such as x.509 certificates and certificate stores.</span></span>

<span data-ttu-id="ced1f-108">DotNetTypes.Format.ps1xml は、CultureInfo、FileVersionInfo、および EventLogEntry オブジェクトなどの他の .NET オブジェクトの表示を定義します。</span><span class="sxs-lookup"><span data-stu-id="ced1f-108">DotNetTypes.Format.ps1xml Defines the display of miscellaneous .NET objects such as CultureInfo, FileVersionInfo, and EventLogEntry objects.</span></span>

<span data-ttu-id="ced1f-109">FileSystem.Format.ps1xml は、ファイルとディレクトリのオブジェクトなどのファイル システム オブジェクトの表示を定義します。</span><span class="sxs-lookup"><span data-stu-id="ced1f-109">FileSystem.Format.ps1xml Defines the display of file system objects such as file and directory objects.</span></span>

<span data-ttu-id="ced1f-110">使用されるさまざまなビューを Help.Format.ps1xml 定義、 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help)フル、パラメーター、および例の詳細なビューなどのコマンドレット。</span><span class="sxs-lookup"><span data-stu-id="ced1f-110">Help.Format.ps1xml Defines the different views used by the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, such as the detailed, full, parameters, and example views.</span></span>

<span data-ttu-id="ced1f-111">PowerShellCore.Format.ps1xml 定義によって返されるオブジェクトなどの Windows PowerShell コア コマンドレットによって生成されたオブジェクトの表示、 [Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)と[Get-history](/powershell/module/Microsoft.PowerShell.Core/Get-History)コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="ced1f-111">PowerShellCore.Format.ps1xml Defines the display of the objects generated by Windows PowerShell core cmdlets, such as the objects returned by the [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) and [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlets.</span></span>

<span data-ttu-id="ced1f-112">PowerShellTrace.Format.ps1xml 定義のトレース オブジェクトによって生成されるものなどの表示、 [Trace-command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command)コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="ced1f-112">PowerShellTrace.Format.ps1xml Defines the display of trace objects such as those generated by the [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.</span></span>

<span data-ttu-id="ced1f-113">Registry.Format.ps1xml では、レジストリ オブジェクト キーとエントリのオブジェクトなどの表示を定義します。</span><span class="sxs-lookup"><span data-stu-id="ced1f-113">Registry.Format.ps1xml Defines the display of registry objects such as key and entry objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ced1f-114">参照</span><span class="sxs-lookup"><span data-stu-id="ced1f-114">See Also</span></span>

[<span data-ttu-id="ced1f-115">Windows PowerShell コマンドレットの記述</span><span class="sxs-lookup"><span data-stu-id="ced1f-115">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)