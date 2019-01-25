---
ms.date: 03/15/2018
keywords: DSC, PowerShell, 構成, セットアップ
title: Microsoft Azure での DSC の使用
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402158"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="6957a-103">Microsoft Azure での DSC の使用</span><span class="sxs-lookup"><span data-stu-id="6957a-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="6957a-104">Microsoft Azure の Desired State Configuration (DSC) は、[Azure Desired State Configuration 拡張機能ハンドラー](/azure/virtual-machines/extensions/dsc-overview)および [Azure Automation DSC](/azure/automation/automation-dsc-overview) によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6957a-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="6957a-105">Azure Desired State Configuration 拡張機能ハンドラー</span><span class="sxs-lookup"><span data-stu-id="6957a-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="6957a-106">Azure DSC 拡張機能を使用すると、Microsoft Azure でホストされている VM を DSC で管理することができます。</span><span class="sxs-lookup"><span data-stu-id="6957a-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="6957a-107">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6957a-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="6957a-108">Azure Desired State Configuration 拡張機能ハンドラーの概要</span><span class="sxs-lookup"><span data-stu-id="6957a-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="6957a-109">Azure Resource Manager テンプレートを使用した Windows VMSS および Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="6957a-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="6957a-110">資格情報を Azure DSC 拡張機能ハンドラーに渡す</span><span class="sxs-lookup"><span data-stu-id="6957a-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="6957a-111">Azure Desired State Configuration 拡張機能の履歴</span><span class="sxs-lookup"><span data-stu-id="6957a-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="6957a-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="6957a-112">Azure Automation DSC</span></span>

<span data-ttu-id="6957a-113">[Azure Automation サービス](https://azure.microsoft.com/en-us/services/automation/) を使用すると、DSC 構成、リソース、管理対象ノードを Azure 内で管理することができます。</span><span class="sxs-lookup"><span data-stu-id="6957a-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="6957a-114">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6957a-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="6957a-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="6957a-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="6957a-116">Azure Automation DSC の使用</span><span class="sxs-lookup"><span data-stu-id="6957a-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="6957a-117">Azure Automation DSC による管理のためのマシンのオンボード</span><span class="sxs-lookup"><span data-stu-id="6957a-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)