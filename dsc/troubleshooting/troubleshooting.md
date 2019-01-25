---
ms.date: 10/30/2018
keywords: DSC, PowerShell, 構成, セットアップ
title: DSC のトラブルシューティング
ms.openlocfilehash: e1f36bbc97569ac0d65f003ee08f52ec174a4520
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402918"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="36c12-103">DSC のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="36c12-103">Troubleshooting DSC</span></span>

<span data-ttu-id="36c12-104">_適用対象: Windows PowerShell 4.0、Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="36c12-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="36c12-105">このトピックでは、問題が発生した場合の DSC のトラブルシューティング方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36c12-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="36c12-106">WinRM の依存関係</span><span class="sxs-lookup"><span data-stu-id="36c12-106">WinRM Dependency</span></span>

<span data-ttu-id="36c12-107">Windows PowerShell Desired State Configuration (DSC) は、WinRM に依存します。</span><span class="sxs-lookup"><span data-stu-id="36c12-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="36c12-108">WinRM は、Windows Server 2008 R2 および Windows 7 では既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="36c12-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="36c12-109">WinRM を有効にするには、Windows PowerShell 管理者特権セッションで `Set-WSManQuickConfig` を実行します。</span><span class="sxs-lookup"><span data-stu-id="36c12-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="36c12-110">Get-DscConfigurationStatus の使用</span><span class="sxs-lookup"><span data-stu-id="36c12-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="36c12-111">[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) コマンドレットは、ターゲット ノードから構成状態に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="36c12-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="36c12-112">構成の実行が成功したかどうかについての基本情報を含む、リッチ オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="36c12-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="36c12-113">オブジェクトを調べ、次に挙げるような構成の実行に関する詳細を知ることができます:</span><span class="sxs-lookup"><span data-stu-id="36c12-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="36c12-114">失敗したすべてのリソース</span><span class="sxs-lookup"><span data-stu-id="36c12-114">All of the resources that failed</span></span>
- <span data-ttu-id="36c12-115">再起動を要求したすべてのリソース</span><span class="sxs-lookup"><span data-stu-id="36c12-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="36c12-116">構成の実行時のメタ構成の設定</span><span class="sxs-lookup"><span data-stu-id="36c12-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="36c12-117">など</span><span class="sxs-lookup"><span data-stu-id="36c12-117">Etc.</span></span>

<span data-ttu-id="36c12-118">次のパラメーター セットは、最後の構成の実行状況に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="36c12-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="36c12-119">次のパラメーター セットは、以前のすべての構成の実行状況に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="36c12-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="36c12-120">例</span><span class="sxs-lookup"><span data-stu-id="36c12-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ReosurceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="36c12-121">スクリプトが実行されません。DSC を使用してスクリプト エラーの診断をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="36c12-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="36c12-122">すべての Windows ソフトウェアと同じく、DSC は[イベント ビューアー](https://support.microsoft.com/hub/4338813/windows-help)から参照可能な[ログ](/windows/desktop/EventLog/about-event-logging)にエラーとイベントを記録します。</span><span class="sxs-lookup"><span data-stu-id="36c12-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="36c12-123">これらのログを調べることは、特定の操作が失敗した理由や、今後エラーを防止する方法を理解するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="36c12-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="36c12-124">構成スクリプトの記述は複雑になることがあります。そのため、作成しながらエラーをより簡単に追跡できるように、DSC ログ リソースを使用して DSC 分析イベント ログで構成の進行状況を追跡してください。</span><span class="sxs-lookup"><span data-stu-id="36c12-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="36c12-125">DSC イベント ログの場所</span><span class="sxs-lookup"><span data-stu-id="36c12-125">Where are DSC event logs?</span></span>

<span data-ttu-id="36c12-126">イベント ビューアーでは、DSC イベントには。**アプリケーションとサービス ログ/Microsoft/Windows/Desired State Configuration の**</span><span class="sxs-lookup"><span data-stu-id="36c12-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="36c12-127">対応する PowerShell コマンドレット [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) を次のように実行して、イベント ログを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="36c12-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="36c12-128">上に示すように、DSC のプライマリ ログ名は **Microsoft->Windows->DSC** です (簡略化のため、Windows の下にあるその他のログ名は表示していません)。</span><span class="sxs-lookup"><span data-stu-id="36c12-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="36c12-129">完全なログ名を作成するには、プライマリ名にチャネル名を追加します。</span><span class="sxs-lookup"><span data-stu-id="36c12-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="36c12-130">DSC エンジンは、主に 3 つの種類のログに書き込みます。[操作、分析、およびデバッグ ログ](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11))します。</span><span class="sxs-lookup"><span data-stu-id="36c12-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="36c12-131">分析ログとデバッグ ログは既定でオフになっているため、それらをイベント ビューアーで有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36c12-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="36c12-132">これを行うには、Windows PowerShell で「Show-EventLog」と入力するか、または、**[スタート]** ボタンをクリックし、**[コントロール パネル]**、**[管理ツール]**、**[イベント ビューアー]** の順にクリックして、イベント ビューアーを開きます。</span><span class="sxs-lookup"><span data-stu-id="36c12-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="36c12-133">イベント ビューアーの **[表示]** メニューで、**[分析およびデバッグ ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36c12-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="36c12-134">分析チャネルのログ名は **Microsoft-Windows-Dsc/Analytic** で、デバッグ チャネルのログ名は **Microsoft-Windows-Dsc/Debug** です。</span><span class="sxs-lookup"><span data-stu-id="36c12-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="36c12-135">次の例に示すように、[wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) ユーティリティを使用してログを有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="36c12-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="36c12-136">DSC ログに含まれる内容</span><span class="sxs-lookup"><span data-stu-id="36c12-136">What do DSC logs contain?</span></span>

<span data-ttu-id="36c12-137">DSC ログは、メッセージの重要度に基づいて 3 つのログ チャネルに分割されています。</span><span class="sxs-lookup"><span data-stu-id="36c12-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="36c12-138">DSC の操作ログにはすべてのエラー メッセージが含まれ、問題の識別に使用できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="36c12-139">分析ログには、より大量のイベントが含まれ、エラーがどこで発生したかを識別できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="36c12-140">このチャネルには、詳細メッセージも含まれます (ある場合)。</span><span class="sxs-lookup"><span data-stu-id="36c12-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="36c12-141">デバッグ ログには、エラーがどのように発生したかを理解するのに役立つログが含まれています。</span><span class="sxs-lookup"><span data-stu-id="36c12-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="36c12-142">DSC イベント メッセージは、すべてのイベント メッセージの先頭が、DSC 操作を一意に表すジョブ ID になるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="36c12-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="36c12-143">次の例では、DSC 操作ログに記録された最初のイベントからメッセージを取得しようとしています。</span><span class="sxs-lookup"><span data-stu-id="36c12-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="36c12-144">DSC イベントは、ユーザーが 1 つの DSC ジョブからイベントを集計できるように特定の構造に記録されます。</span><span class="sxs-lookup"><span data-stu-id="36c12-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="36c12-145">その構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="36c12-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="36c12-146">1 つの DSC 操作からのイベントの収集</span><span class="sxs-lookup"><span data-stu-id="36c12-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="36c12-147">DSC イベント ログには、各種の DSC 操作によって生成されたイベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="36c12-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="36c12-148">ただし、通常、関心があるのはある特定の操作の詳細のみです。</span><span class="sxs-lookup"><span data-stu-id="36c12-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="36c12-149">すべての DSC ログは、それぞれの DSC 操作に対して一意であるジョブ ID プロパティによってグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="36c12-150">ジョブ ID は、すべての DSC イベントの最初のプロパティ値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="36c12-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="36c12-151">次の手順では、グループ化された配列構造にすべてのイベントを蓄積する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36c12-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="36c12-152">ここでは、変数 `$SeparateDscOperations` にジョブ ID でグループ化されたログが含まれています。</span><span class="sxs-lookup"><span data-stu-id="36c12-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="36c12-153">この変数の各配列要素は、さまざまな DSC 操作によって記録されたイベントのグループを表しており、ログの詳細にアクセスできるようになっています。</span><span class="sxs-lookup"><span data-stu-id="36c12-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="36c12-154">[Where-Object](/powershell/module/microsoft.powershell.core/where-object) を使用して変数 `$SeparateDscOperations` 内のデータを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="36c12-155">次に、DSC のトラブルシューティングに役立つデータを抽出する 5 つのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="36c12-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="36c12-156">1:操作エラー</span><span class="sxs-lookup"><span data-stu-id="36c12-156">1: Operations failures</span></span>

<span data-ttu-id="36c12-157">すべてのイベントには[重大度レベル](/windows/desktop/WES/defining-severity-levels)があります。</span><span class="sxs-lookup"><span data-stu-id="36c12-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="36c12-158">この情報を使用して、エラー イベントを識別できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="36c12-159">2:過去 30 分間に実行された操作の詳細</span><span class="sxs-lookup"><span data-stu-id="36c12-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="36c12-160">それぞれの Windows イベントのプロパティである `TimeCreated` は、イベントが作成された時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="36c12-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="36c12-161">このプロパティを特定の日付/時刻オブジェクトと比較すると、すべてのイベントをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="36c12-162">3:最後の操作からのメッセージ</span><span class="sxs-lookup"><span data-stu-id="36c12-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="36c12-163">最後の操作は、配列グループ `$SeparateDscOperations` の最初のインデックスに格納されています。</span><span class="sxs-lookup"><span data-stu-id="36c12-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="36c12-164">グループのメッセージに対してインデックス 0 のクエリを実行すると、最後の操作に関するすべてのメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="36c12-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="36c12-165">4:最近失敗した操作について記録されたエラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="36c12-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="36c12-166">`$SeparateDscOperations[0].Group` には、最後の操作に関する一連のイベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="36c12-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="36c12-167">レベル表示名に基づいてイベントをフィルター処理するには、`Where-Object` コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="36c12-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="36c12-168">結果は `$myFailedEvent` 変数に格納され、これをより細かく分析してイベント メッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="36c12-169">5:特定のジョブ ID 用に生成されたすべてのイベント</span><span class="sxs-lookup"><span data-stu-id="36c12-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="36c12-170">`$SeparateDscOperations` はグループの配列で、グループのそれぞれに固有のジョブ ID として名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="36c12-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="36c12-171">`Where-Object` コマンドレットを実行すると、特定のジョブ ID を持つイベントのグループを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="36c12-172">xDscDiagnostics を使用した DSC ログの分析</span><span class="sxs-lookup"><span data-stu-id="36c12-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="36c12-173">**xDscDiagnostics** は、コンピューター上の DSC 障害の分析に役立つ複数の関数で構成される PowerShell モジュールです。</span><span class="sxs-lookup"><span data-stu-id="36c12-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="36c12-174">これらの関数は、過去の DSC 操作からのすべてのローカル イベント、またはリモート コンピューター上の DSC イベントの識別に役立ちます (有効な資格情報を使用)。</span><span class="sxs-lookup"><span data-stu-id="36c12-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="36c12-175">ここでは、開始から終了まで 1 回の一意の DSC 実行を定義するために、DSC 操作という用語を使用します。</span><span class="sxs-lookup"><span data-stu-id="36c12-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="36c12-176">たとえば、`Test-DscConfiguration` は独立した DSC 操作です。</span><span class="sxs-lookup"><span data-stu-id="36c12-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="36c12-177">同様に、DSC の他のすべてのコマンドレット (`Get-DscConfiguration` や `Start-DscConfiguration` など) をそれぞれ別の DSC 操作として識別できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="36c12-178">この関数は、[xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics) で説明されています。</span><span class="sxs-lookup"><span data-stu-id="36c12-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="36c12-179">ヘルプを参照するには、`Get-Help <cmdlet name>` を実行します。</span><span class="sxs-lookup"><span data-stu-id="36c12-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="36c12-180">DSC 操作の詳細の取得</span><span class="sxs-lookup"><span data-stu-id="36c12-180">Getting details of DSC operations</span></span>

<span data-ttu-id="36c12-181">`Get-xDscOperation` 関数は、1 台以上のコンピューターで実行される DSC 操作の結果を検索し、それぞれの DSC 操作で生成されたイベントのコレクションが含まれているオブジェクトを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="36c12-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="36c12-182">たとえば、次の出力では、3 つのコマンドが実行されました。</span><span class="sxs-lookup"><span data-stu-id="36c12-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="36c12-183">1 つ目のコマンドは成功し、他の 2 つのコマンドは失敗しました。</span><span class="sxs-lookup"><span data-stu-id="36c12-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="36c12-184">これらの結果が `Get-xDscOperation` の出力にまとめられています。</span><span class="sxs-lookup"><span data-stu-id="36c12-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="36c12-185">また、`Newest` パラメーターを使用して最近の操作の結果のみを表示するように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="36c12-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="36c12-186">DSC イベントの詳細の取得</span><span class="sxs-lookup"><span data-stu-id="36c12-186">Getting details of DSC events</span></span>

<span data-ttu-id="36c12-187">`Trace-xDscOperation` コマンドレットは、イベント、そのイベントの種類、および特定の DSC 操作から生成されたメッセージ出力のコレクションが含まれているオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="36c12-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="36c12-188">通常、`Get-xDscOperation` を使用した操作のいずれかでエラーが発生した場合、その操作をトレースすると、どのイベントによってエラーが発生したかがわかります。</span><span class="sxs-lookup"><span data-stu-id="36c12-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="36c12-189">`SequenceID` パラメーターを使用して特定のコンピューターの特定の操作に対するイベントを取得します。</span><span class="sxs-lookup"><span data-stu-id="36c12-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="36c12-190">たとえば、`SequenceID` に 9 を指定すると、`Trace-xDscOperaion` は最後の操作から 9 番目の DSC 操作のトレースを取得します。</span><span class="sxs-lookup"><span data-stu-id="36c12-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="36c12-191">渡す、 **GUID** 、特定の DSC 操作に割り当てられている (によって返される、`Get-xDscOperation`コマンドレット) その DSC 操作のイベントの詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="36c12-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="36c12-192">`Trace-xDscOperation` では、分析ログ、デバッグ ログ、および操作ログからイベントを集計するため、上記のようにこれらのログを有効にするように、プロンプトで要求されます。</span><span class="sxs-lookup"><span data-stu-id="36c12-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="36c12-193">また、`Trace-xDscOperation` の出力を変数に保存して、イベントに関する情報を収集することもできます。</span><span class="sxs-lookup"><span data-stu-id="36c12-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="36c12-194">次のコマンドを使用すると、特定の DSC 操作のすべてのイベントを表示できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="36c12-195">次の出力のように、`Get-WinEvent` コマンドレットと同じ結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36c12-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="36c12-196">まず、`Get-xDscOperation` を使用して、コンピューターでの DSC 構成実行のうち、最新のいくつかを一覧表示すると理想的です。</span><span class="sxs-lookup"><span data-stu-id="36c12-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="36c12-197">次に、`Trace-xDscOperation` でいずれかの単一の操作を (その SequenceID または JobID を使用して) 調べると、バックグラウンドで何が行われたかがわかります。</span><span class="sxs-lookup"><span data-stu-id="36c12-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="36c12-198">リモート コンピューターのイベントの取得</span><span class="sxs-lookup"><span data-stu-id="36c12-198">Getting events for a remote computer</span></span>

<span data-ttu-id="36c12-199">`Trace-xDscOperation` コマンドレットの `ComputerName` パラメーターを使用して、リモート コンピューターのイベントの詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="36c12-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="36c12-200">これを行う前に、ファイアウォール ルールを作成してリモート コンピューターでのリモート管理を許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36c12-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="36c12-201">これで、`Trace-xDscOperation` への呼び出しでそのコンピューターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="36c12-202">リソースが更新されません。キャッシュをリセットする方法</span><span class="sxs-lookup"><span data-stu-id="36c12-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="36c12-203">DSC エンジンは、効率化のために、PowerShell モジュールとして実装されているリソースをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="36c12-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="36c12-204">ただし、リソースを作成すると同時にテストする場合には、このことによって問題が発生することがあります。これは、DSC では、プロセスが再開されるまで、キャッシュされたバージョンを読み込むためです。</span><span class="sxs-lookup"><span data-stu-id="36c12-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="36c12-205">新しいバージョンが読み込まれるようにする唯一の方法は、DSC エンジンをホストしているプロセスを明示的に強制終了することです。</span><span class="sxs-lookup"><span data-stu-id="36c12-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="36c12-206">同様に、カスタム リソースを追加および変更した後で `Start-DscConfiguration` を実行した場合、その変更はコンピューターを再起動しないと反映されません。</span><span class="sxs-lookup"><span data-stu-id="36c12-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="36c12-207">これは、DSC が WMI Provider Host Process (WmiPrvSE) で動作し、通常、WmiPrvSE のインスタンスは同時にいくつも動作しているためです。</span><span class="sxs-lookup"><span data-stu-id="36c12-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="36c12-208">コンピューターを再起動すると、ホスト プロセスが再起動し、キャッシュがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="36c12-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="36c12-209">コンピューターを再起動することなく、構成を正常にリサイクルし、キャッシュをクリアするには、ホスト プロセスを停止してから再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36c12-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="36c12-210">このことは、プロセスを識別し、停止し、再起動することで、インスタンスごとに実行できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="36c12-211">また、以下に示すように、`DebugMode` を使用して PowerShell DSC リソースを再読み込みすることもできます。</span><span class="sxs-lookup"><span data-stu-id="36c12-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="36c12-212">DSC エンジンをホストしているプロセスを識別し、インスタンスごとにそのプロセスを停止するには、DSC エンジンをホストしている WmiPrvSE のプロセス ID を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="36c12-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="36c12-213">次に、プロバイダーを更新するために、次のコマンドを使用して WmiPrvSE プロセスを停止し、再度 **Start-DscConfiguration** を実行します。</span><span class="sxs-lookup"><span data-stu-id="36c12-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="36c12-214">DebugMode の使用</span><span class="sxs-lookup"><span data-stu-id="36c12-214">Using DebugMode</span></span>

<span data-ttu-id="36c12-215">ホスト プロセスの再起動時に `DebugMode` を使用して常にキャッシュをクリアするように、DSC ローカル構成マネージャー (LCM) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="36c12-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="36c12-216">**TRUE** に設定すると、エンジンは常に PowerShell DSC リソースを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="36c12-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="36c12-217">リソースの書き込みが完了した後、**FALSE** に設定し直して、モジュールをキャッシュするようにエンジンの動作を戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="36c12-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="36c12-218">次は、`DebugMode` がどのようにキャッシュを自動的に更新できるかを示すデモです。</span><span class="sxs-lookup"><span data-stu-id="36c12-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="36c12-219">まず、既定の構成を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="36c12-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="36c12-220">`DebugMode` が **"None"** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="36c12-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="36c12-221">`DebugMode` のデモを設定するには、次の PowerShell リソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="36c12-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="36c12-222">ここで、上記のリソースを使用して `TestProviderDebugMode` という名前で構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="36c12-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="36c12-223">ファイル `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` の内容は **1** になっています。</span><span class="sxs-lookup"><span data-stu-id="36c12-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="36c12-224">ここで、次のスクリプトを使用してプロバイダー コードを更新します。</span><span class="sxs-lookup"><span data-stu-id="36c12-224">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="36c12-225">このスクリプトは、乱数を生成し、それに合わせてプロバイダー コードを更新します。</span><span class="sxs-lookup"><span data-stu-id="36c12-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="36c12-226">`DebugMode` を false に設定しても、ファイル "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" の内容は変わりません。</span><span class="sxs-lookup"><span data-stu-id="36c12-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="36c12-227">ここで、ご利用の構成スクリプト内で `DebugMode` を **"ForceModuleImport"** に設定します。</span><span class="sxs-lookup"><span data-stu-id="36c12-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="36c12-228">上記のスクリプトを再度実行すると、ファイルの内容が毎回異なるものになります。</span><span class="sxs-lookup"><span data-stu-id="36c12-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="36c12-229">(`Get-DscConfiguration` を実行して確認できます)。</span><span class="sxs-lookup"><span data-stu-id="36c12-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="36c12-230">次に、さらに 2 つの実行の結果を示します (実際にスクリプトを実行した結果は異なる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="36c12-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a><span data-ttu-id="36c12-231">参照</span><span class="sxs-lookup"><span data-stu-id="36c12-231">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="36c12-232">概念</span><span class="sxs-lookup"><span data-stu-id="36c12-232">Concepts</span></span>

- [<span data-ttu-id="36c12-233">Build Custom Windows PowerShell Desired State Configuration Resources (カスタム Windows PowerShell Desired State Configuration のビルド)</span><span class="sxs-lookup"><span data-stu-id="36c12-233">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="36c12-234">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="36c12-234">Other Resources</span></span>

- [<span data-ttu-id="36c12-235">Windows PowerShell Desired State Configuration Cmdlets (Windows PowerShell Desired State Configuration のコマンドレット)</span><span class="sxs-lookup"><span data-stu-id="36c12-235">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)