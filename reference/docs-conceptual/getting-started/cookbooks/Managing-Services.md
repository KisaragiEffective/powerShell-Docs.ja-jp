---
ms.date: 2017-06-05
keywords: "PowerShell, コマンドレット"
title: "サービスの管理"
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 9fd6c8bcfecc99756188409629ddf94b880aab91
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2017
---
# <a name="managing-services"></a><span data-ttu-id="e827f-103">サービスの管理</span><span class="sxs-lookup"><span data-stu-id="e827f-103">Managing Services</span></span>
<span data-ttu-id="e827f-104">サービスに関連したさまざまなタスクを実行するために設計された 8 つの主要な Service コマンドレットがあります。</span><span class="sxs-lookup"><span data-stu-id="e827f-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="e827f-105">ここでは、サービスの実行状態の一覧表示と変更についてのみ取り上げていますが、**Get-Help \&#42;-Service** でサービスに関連したコマンドレットを一覧表示したり、**Get-Help<Cmdlet-Name>** (**Get-Help New-Service** など) でサービスに関連した各種コマンドレットの情報を検索したりできます。</span><span class="sxs-lookup"><span data-stu-id="e827f-105">We will look only at listing and changing running state for services, but you can get a list Service cmdlets by using **Get-Help \&#42;-Service**, and you can find information about each Service cmdlet by using **Get-Help<Cmdlet-Name>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="e827f-106">サービスの取得</span><span class="sxs-lookup"><span data-stu-id="e827f-106">Getting Services</span></span>
<span data-ttu-id="e827f-107">**Get-Service** コマンドレットを使用して、ローカル コンピューターまたはリモート コンピューター上のサービスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="e827f-108">**Get-Process** と同様、パラメーターを指定せずに **Get-Service** コマンドを実行した場合、すべてのサービスが返されます。</span><span class="sxs-lookup"><span data-stu-id="e827f-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="e827f-109">アスタリスクをワイルドカードとして使用し、サービスを名前でフィルター処理するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="e827f-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="e827f-110">サービスの実際の名前がわかるとは限らないため、表示名でサービスを検索しなければならない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e827f-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="e827f-111">特定の名前を指定するか、ワイルドカードを使用するか、または表示名の一覧を使用することによって検索できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```
PS> Get-Service -DisplayName se*
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center
PS> Get-Service -DisplayName ServiceLayer,Server
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="e827f-112">Get-Service コマンドレットの ComputerName パラメーターを使用して、リモート コンピューター上のサービスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="e827f-113">ComputerName パラメーターには複数の値およびワイルドカード文字を使用できるため、1 つのコマンドで複数のコンピューター上のサービスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="e827f-114">たとえば、次のコマンドでは、Server01 リモート コンピューター上のサービスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="e827f-115">必要なサービスおよび依存するサービスの取得</span><span class="sxs-lookup"><span data-stu-id="e827f-115">Getting Required and Dependent Services</span></span>
<span data-ttu-id="e827f-116">Get-Service コマンドレットには、サービスの管理に非常に便利な 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="e827f-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="e827f-117">DependentServices パラメーターは、そのサービスに依存するサービスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e827f-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="e827f-118">RequiredServices パラメーターは、そのサービスが依存しているサービスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e827f-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="e827f-119">これらのパラメーターは、Get-Service が返す System.ServiceProcess.ServiceController オブジェクトの DependentServices プロパティと ServicesDependedOn (エイリアス: RequiredServices) プロパティの値を表示するだけですが、コマンドが単純化され、この情報をずっと簡単に取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e827f-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="e827f-120">次のコマンドは、LanmanWorkstation サービスが必要とするサービスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e827f-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="e827f-121">次のコマンドは、LanmanWorkstation サービスを必要とするサービスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e827f-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="e827f-122">また、依存関係を持つサービスをすべて取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="e827f-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="e827f-123">次のコマンドは、それを実行した後、Format-Table コマンドレットを使用して、コンピューター上のサービスの Status、Name、RequiredServices、DependentServices の各プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="e827f-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="e827f-124">サービスの停止、開始、一時停止、再開</span><span class="sxs-lookup"><span data-stu-id="e827f-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="e827f-125">サービスを扱うすべてのコマンドレットは、同じ形式で指定できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="e827f-126">サービスを一般的な名前 (表示名) で指定できるほか、表示名の一覧を指定したり、ワイルドカードを値として使用したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e827f-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="e827f-127">印刷スプーラーを停止するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="e827f-127">To stop the print spooler, use:</span></span>

```
Stop-Service -Name spooler
```

<span data-ttu-id="e827f-128">停止した印刷スプーラーを開始するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="e827f-128">To start the print spooler after it is stopped, use:</span></span>

```
Start-Service -Name spooler
```

<span data-ttu-id="e827f-129">印刷スプーラーを一時停止するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="e827f-129">To suspend the print spooler, use:</span></span>

```
Suspend-Service -Name spooler
```

<span data-ttu-id="e827f-130">**Restart-Service** コマンドレットの動作も、サービスを扱う他のコマンドレットと同じですが、もう少し複雑な例を示します。</span><span class="sxs-lookup"><span data-stu-id="e827f-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="e827f-131">最も簡単な使い方は、サービスの名前を指定することです。</span><span class="sxs-lookup"><span data-stu-id="e827f-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="e827f-132">印刷スプーラーの起動に関して、警告メッセージが繰り返し出力されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e827f-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="e827f-133">ある程度時間のかかるサービス操作を実行すると、タスクの実行を試みている最中であることを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e827f-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="e827f-134">複数のサービスを再開する場合は、サービスの一覧を取得してからフィルターを適用し、その上でサービスを再開するようにします。</span><span class="sxs-lookup"><span data-stu-id="e827f-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="e827f-135">サービスを扱うこれらのコマンドレットには ComputerName パラメーターはありませんが、Invoke-Command コマンドレットを使用すれば、これらのコマンドレットをリモート コンピューター上で実行できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="e827f-136">たとえば、次のコマンドでは、Server01 リモート コンピューター上のスプーラー サービスを再起動できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="e827f-137">サービスのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="e827f-137">Setting Service Properties</span></span>
<span data-ttu-id="e827f-138">Set-Service コマンドレットは、ローカル コンピューターまたはリモート コンピューター上のサービスのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="e827f-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="e827f-139">サービスの状態もプロパティの 1 つであるため、このコマンドレットを使用してサービスを開始、停止、一時停止できます。</span><span class="sxs-lookup"><span data-stu-id="e827f-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="e827f-140">Set-Service コマンドレットには、サービスのスタートアップの種類を変更できる StartupType パラメーターもあります。</span><span class="sxs-lookup"><span data-stu-id="e827f-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="e827f-141">Windows Vista 以降のバージョンの Windows で、Set-Service を使用するには、Windows PowerShell を開く際に [管理者として実行] オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e827f-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="e827f-142">詳細については、「[Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e827f-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="e827f-143">参照</span><span class="sxs-lookup"><span data-stu-id="e827f-143">See Also</span></span>
- [<span data-ttu-id="e827f-144">Get-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="e827f-144">Get-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [<span data-ttu-id="e827f-145">Set-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="e827f-145">Set-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [<span data-ttu-id="e827f-146">Restart-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="e827f-146">Restart-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [<span data-ttu-id="e827f-147">Suspend-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="e827f-147">Suspend-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)
