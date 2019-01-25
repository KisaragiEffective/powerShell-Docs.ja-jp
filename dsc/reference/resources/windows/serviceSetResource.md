---
ms.date: 06/12/2017
keywords: DSC, PowerShell, 構成, セットアップ
title: DSC ServiceSet リソース
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047559"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="f9959-103">DSC ServiceSet リソース</span><span class="sxs-lookup"><span data-stu-id="f9959-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="f9959-104">適用先:Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f9959-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f9959-105">PowerShell Desired State Configuration (DSC) の **ServiceSet** リソースは、ターゲット ノード上でサービスを管理するためのメカニズムを備えています。</span><span class="sxs-lookup"><span data-stu-id="f9959-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="f9959-106">このリソースは[複合リソース](../../../resources/authoringResourceComposite.md)であり、`Name` プロパティに指定されているサービスごとに [Service リソース](serviceResource.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f9959-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="f9959-107">サービスの数を同じ状態に構成するときにこのリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9959-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9959-108">構文</span><span class="sxs-lookup"><span data-stu-id="f9959-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="f9959-109">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f9959-109">Properties</span></span>

|  <span data-ttu-id="f9959-110">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f9959-110">Property</span></span>  |  <span data-ttu-id="f9959-111">説明</span><span class="sxs-lookup"><span data-stu-id="f9959-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="f9959-112">名前</span><span class="sxs-lookup"><span data-stu-id="f9959-112">Name</span></span>| <span data-ttu-id="f9959-113">サービス名を示します。</span><span class="sxs-lookup"><span data-stu-id="f9959-113">Indicates the service names.</span></span> <span data-ttu-id="f9959-114">これは表示名とは異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="f9959-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="f9959-115">[Get-Service](https://technet.microsoft.com/library/hh849804.aspx) コマンドレットを使用すると、サービスとその現在の状態の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f9959-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="f9959-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="f9959-116">StartupType</span></span>| <span data-ttu-id="f9959-117">サービスのスタートアップの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="f9959-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="f9959-118">このプロパティに許容される値は次のとおりです。**自動**、**無効**、および**手動**</span><span class="sxs-lookup"><span data-stu-id="f9959-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="f9959-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="f9959-119">BuiltInAccount</span></span>| <span data-ttu-id="f9959-120">サービスに使用するサインイン アカウントを示します。</span><span class="sxs-lookup"><span data-stu-id="f9959-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="f9959-121">このプロパティに許容される値は次のとおりです。**LocalService**、 **LocalSystem**、および**NetworkService**します。</span><span class="sxs-lookup"><span data-stu-id="f9959-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="f9959-122">State</span><span class="sxs-lookup"><span data-stu-id="f9959-122">State</span></span>| <span data-ttu-id="f9959-123">サービスに対して保証する状態を示します。**停止**または**を実行している**します。</span><span class="sxs-lookup"><span data-stu-id="f9959-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="f9959-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="f9959-124">Ensure</span></span>| <span data-ttu-id="f9959-125">サービスがシステムに存在するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f9959-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="f9959-126">サービスが存在しないようにするには、このプロパティを **[Absent]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="f9959-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="f9959-127">ターゲットが存在するようにするには、**[Present]** (既定値) に設定します。</span><span class="sxs-lookup"><span data-stu-id="f9959-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="f9959-128">Credential</span><span class="sxs-lookup"><span data-stu-id="f9959-128">Credential</span></span>| <span data-ttu-id="f9959-129">サービス リソースを実行するアカウントの資格情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f9959-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="f9959-130">このプロパティおよび **BuiltinAccount** プロパティを同時に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f9959-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="f9959-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f9959-131">DependsOn</span></span>| <span data-ttu-id="f9959-132">このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f9959-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f9959-133">たとえば、最初に実行するリソース構成スクリプト ブロックの ID が *ResourceName* で、そのタイプが *ResourceType* である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。</span><span class="sxs-lookup"><span data-stu-id="f9959-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="f9959-134">例</span><span class="sxs-lookup"><span data-stu-id="f9959-134">Example</span></span>

<span data-ttu-id="f9959-135">次の構成で "Windows オーディオ" サービスと "リモート デスクトップ サービス" サービスが開始します。</span><span class="sxs-lookup"><span data-stu-id="f9959-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```