---
ms.date: 06/12/2017
keywords: WMF, PowerShell, セットアップ
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222175"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="72af3-102">PowerShellGet による PowerShell モジュールの検出、インストール、およびインベントリ</span><span class="sxs-lookup"><span data-stu-id="72af3-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="72af3-103">このリリースの WMF には PowerShellGet が含まれています。</span><span class="sxs-lookup"><span data-stu-id="72af3-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="72af3-104">Find-Module では、-Tag パラメーターを使用してモジュールのメタデータをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="72af3-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="72af3-105">Find-Module では、-Filter パラメーターを使用してリポジトリ固有の検索言語をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="72af3-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="72af3-106">Find-Module では、-Command、-DscResource、および -Includes パラメーターを使用してモジュールのコンテンツに基づいてフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="72af3-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="72af3-107">Find-DscResource では、リポジトリ内の個々の DSC リソースを検出できます。</span><span class="sxs-lookup"><span data-stu-id="72af3-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="72af3-108">NuGet によるファイル共有からのインストールおよびファイル共有への発行のサポート</span><span class="sxs-lookup"><span data-stu-id="72af3-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="72af3-109">コマンド例</span><span class="sxs-lookup"><span data-stu-id="72af3-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="72af3-110">PowerShellGet の新機能</span><span class="sxs-lookup"><span data-stu-id="72af3-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="72af3-111">Windows PowerShell 5.0 以降の Side-by-Side バージョン サポート</span><span class="sxs-lookup"><span data-stu-id="72af3-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="72af3-112">モジュールの依存関係のインストール サポート</span><span class="sxs-lookup"><span data-stu-id="72af3-112">Module dependency installation support</span></span>
-   <span data-ttu-id="72af3-113">次の 3 つの新しいコマンドレット</span><span class="sxs-lookup"><span data-stu-id="72af3-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="72af3-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="72af3-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="72af3-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="72af3-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="72af3-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="72af3-116">Save-Module</span></span>
