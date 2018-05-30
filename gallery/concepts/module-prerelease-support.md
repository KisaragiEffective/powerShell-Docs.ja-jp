---
ms.date: 09/26/2017
contributor: keithb
keywords: ギャラリー, PowerShell, コマンドレット, PSGet
title: プレリリース モジュールのバージョン
ms.openlocfilehash: 2a4fcd40353450e5ba03910984c5a05772a93d0d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2018
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="fd6a9-103">プレリリース モジュールのバージョン</span><span class="sxs-lookup"><span data-stu-id="fd6a9-103">Prerelease Module Versions</span></span>

<span data-ttu-id="fd6a9-104">バージョン 1.6.0 より、PowerShellGet および PowerShell ギャラリーで 1.0.0 以降のバージョンをプレリリースとしてタグ付けできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="fd6a9-105">この機能より前は、プレリリース項目は 0 で始まるバージョンに制限されていました。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="fd6a9-106">この機能の目的は、PowerShell バージョン 3 以降、または既存のバージョンの PowerShellGet との後方互換性を失わずに [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) のバージョン管理規則に対してより優れたサポートを提供することです。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="fd6a9-107">このトピックでは、モジュールに固有の機能に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="fd6a9-108">スクリプトの同等の機能は、「[プレリリース バージョンのスクリプト](script-prerelease-support.md)」のトピックにあります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="fd6a9-109">これらの機能を使用して、パブリッシャーはモジュールまたはスクリプトをバージョン 2.5.0-alpha と識別し、プレリリース バージョンより優先される実稼働可能なバージョン 2.5.0 を後からリリースすることができます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="fd6a9-110">大まかには、プレリリースのモジュール機能には次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="fd6a9-111">モジュール マニフェストの PSData セクションに Prerelease 文字列を追加すると、モジュールがプレリリース バージョンとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="fd6a9-112">モジュールが PowerShell ギャラリーに発行されると、このデータがマニフェストから抽出され、プレリリース項目を識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="fd6a9-113">プレリリース項目を取得するには、-AllowPrerelease フラグを Find-Module、Install-Module、Update-Module、Save-Module の PowerShellGet コマンドに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span> <span data-ttu-id="fd6a9-114">フラグが指定されていないと、プレリリース項目が表示されません。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="fd6a9-115">Find-Module、Get-InstalledModule、および PowerShell ギャラリーに表示されるモジュール バージョンは、2.5.0-alpha のように Prerelease 文字列が付加された 1 つの文字列として表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="fd6a9-116">この機能の詳細については後述します。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-116">Details for the features are included below.</span></span>

<span data-ttu-id="fd6a9-117">この変更は、PowerShell に組み込まれているモジュール バージョンのサポートには影響せず、PowerShell 3.0、4.0、および 5 と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="fd6a9-118">モジュール バージョンをプレリリースとして識別する</span><span class="sxs-lookup"><span data-stu-id="fd6a9-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="fd6a9-119">PowerShellGet がプレリリース バージョンをサポートするには、モジュール マニフェスト内の 2 つのフィールドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="fd6a9-120">プレリリース バージョンが使用される場合、モジュール マニフェストに含まれる ModuleVersion は 3 パートのバージョンで、既存の PowerShell バージョン管理に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="fd6a9-121">バージョンの形式は A.B.C になります。A、B、C はすべて整数です。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="fd6a9-122">Prerelease 文字列は、PrivateData の PSData セクションの、モジュール マニフェストに指定されます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="fd6a9-123">Prerelease 文字列の詳しい要件は後述します。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="fd6a9-124">モジュールをプレリリースとして定義するモジュール マニフェストの例のセクションは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="fd6a9-125">Prerelease 文字列の詳しい要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="fd6a9-126">Prerelease 文字列は、Major.Minor.Build の ModuleVersion が 3 セグメントである場合にのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="fd6a9-127">これは、SemVer v1.0.0 と適合します。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="fd6a9-128">ハイフンは、ビルド番号と Prerelease 文字列の間の区切り文字です。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="fd6a9-129">ハイフンは、Prerelease 文字列の最初の文字としてのみ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="fd6a9-130">Prerelease 文字列には ASCII 英数字 [0-9A-Za-z-] のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="fd6a9-131">Prerelease 文字列はアルファベットで始めることをお勧めします。項目の一覧を見たときにプレリリース バージョンであることが識別しやすくなるためです。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span>
- <span data-ttu-id="fd6a9-132">現時点では、SemVer v1.0.0 の Prerelease 文字列のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="fd6a9-133">Prerelease 文字列には (SemVer 2.0 では許可されている) ピリオドまたは + [.+] のどちらかを含めることは__できません__。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="fd6a9-134">サポートされている Prerelease 文字列には、-alpha、-alpha1、-BETA、-update20171020 などがあります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="fd6a9-135">__並べ替え順序およびインストール フォルダーへのプレリリース バージョン管理の影響__</span><span class="sxs-lookup"><span data-stu-id="fd6a9-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="fd6a9-136">並べ替え順序は、PowerShell ギャラリーへの発行時に重要なプレリリース バージョンを使用するときや、PowerShellGet コマンドを使用してモジュールをインストールするときに変更されます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="fd6a9-137">Prerelease 文字列が 2 つのモジュールに指定されている場合、並べ替え順序はハイフンの後の文字列部分に基づきます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="fd6a9-138">そのため、バージョン 2.5.0-alpha は 2.5.0-beta より小さく、2.5.0-beta は 2.5.0-gamma より小さくなります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="fd6a9-139">2 つのモジュールに同じ ModuleVersion が含まれ、うち 1 つに Prerelease 文字列が含まれる場合は、Prerelease 文字列のないモジュールが実稼働可能なバージョンと見なされ、(Prerelease 文字列を含む) プレリリース バージョンより後のバージョンとして並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="fd6a9-140">たとえば、2.5.0 と 2.5.0-beta を比較すると、2.5.0 バージョンの方が後だと見なされます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="fd6a9-141">PowerShell ギャラリーに発行すると、既定により、発行されているモジュールのバージョンが必ず PowerShell ギャラリーにある以前に発行されているバージョンよりも後のバージョンになります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="fd6a9-142">PowerShellGet コマンドを使用してプレリリース項目を検索および取得する</span><span class="sxs-lookup"><span data-stu-id="fd6a9-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="fd6a9-143">Find-Module、Install-Module、Update-Module、Save-Module の PowerShellGet コマンドを使用してプレリリース項目を操作するには、-AllowPrerelease フラグを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="fd6a9-144">-AllowPrerelease が指定されていると、プレリリース項目が存在する場合にはその項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="fd6a9-145">-AllowPrerelease フラグが指定されていないと、プレリリース項目が表示されません。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="fd6a9-146">PowerShellGet モジュールのコマンドで、これに対する唯一の例外が Get-InstalledModule です。場合によっては Uninstall-Module も含まれます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="fd6a9-147">Get-InstalledModule は常にモジュールのバージョン文字列にプレリリース情報を自動的に表示します。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="fd6a9-148">Uninstall-Module は__バージョンが指定されていない__場合に、既定でモジュールの最新のバージョンをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="fd6a9-149">この動作は変更されていません。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-149">That behavior has not changed.</span></span> <span data-ttu-id="fd6a9-150">ただし、-RequiredVersion を使用してプレリリース バージョンが指定された場合は、-AllowPrerelease が必要になります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="fd6a9-151">例</span><span class="sxs-lookup"><span data-stu-id="fd6a9-151">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="fd6a9-152">プレリリースが指定されているかどうかの違いしかない、モジュールのバージョンの同時インストールはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="fd6a9-153">PowerShellGet を使用してモジュールをインストールすると、ModuleVersion を使用してフォルダー名が作成され、同じモジュールの異なるバージョンが同時にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="fd6a9-154">Prerelease 文字列のない ModuleVersion がフォルダー名で使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="fd6a9-155">ユーザーが MyModule バージョン 2.5.0-alpha をインストールすると、MyModule\2.5.0 フォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span> <span data-ttu-id="fd6a9-156">その後、ユーザーが 2.5.0-beta をインストールすると、2.5.0-beta バージョンがフォルダー MyModule\2.5.0 の内容を__上書き__します。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span> <span data-ttu-id="fd6a9-157">この方法の 1 つの利点が、実稼働可能バージョンのインストール後にプレリリース バージョンをアンインストールする必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="fd6a9-158">以下の例は、予想すべき内容を示します。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-158">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="fd6a9-159">-RequiredVersion が指定されていない場合、Uninstall-Module によってモジュールの最新バージョンが削除されます。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="fd6a9-160">-RequiredVersion が指定されていて、これがプレリリースである場合、-AllowPrerelease をコマンドに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd6a9-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a><span data-ttu-id="fd6a9-161">詳細情報</span><span class="sxs-lookup"><span data-stu-id="fd6a9-161">More details</span></span>

- [<span data-ttu-id="fd6a9-162">プレリリース バージョンのスクリプト</span><span class="sxs-lookup"><span data-stu-id="fd6a9-162">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="fd6a9-163">Find-Module</span><span class="sxs-lookup"><span data-stu-id="fd6a9-163">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="fd6a9-164">Install-Module</span><span class="sxs-lookup"><span data-stu-id="fd6a9-164">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="fd6a9-165">Save-Module</span><span class="sxs-lookup"><span data-stu-id="fd6a9-165">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="fd6a9-166">Update-Module</span><span class="sxs-lookup"><span data-stu-id="fd6a9-166">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="fd6a9-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="fd6a9-167">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="fd6a9-168">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="fd6a9-168">UnInstall-Module</span></span>](/powershell/gallery/psget/module/psget_uninstall-module)