---
ms.date: 08/23/2017
keywords: PowerShell, コマンドレット
title: Windows PowerShell Web Access でのアクセスに関する問題のトラブルシューティング
ms.openlocfilehash: c9b98c7a1685679eb88b718de0351154cb84e92e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402533"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="89e95-103">Windows PowerShell Web Access でのアクセスに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="89e95-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="89e95-104">更新:2013 年 6 月 24日 (改訂、2017 年 8 月 23 日)</span><span class="sxs-lookup"><span data-stu-id="89e95-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="89e95-105">適用先:Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="89e95-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="89e95-106">次のセクションでは、Windows PowerShell Web Access を利用したリモート コンピューターへの接続で発生する可能性がある一般的な問題とその問題の解決案を提示します。</span><span class="sxs-lookup"><span data-stu-id="89e95-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="89e95-107">サインイン エラー</span><span class="sxs-lookup"><span data-stu-id="89e95-107">Sign-in failure</span></span>

<span data-ttu-id="89e95-108">エラー発生の原因として以下が考えられます。</span><span class="sxs-lookup"><span data-stu-id="89e95-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="89e95-109">コンピューターまたはリモート コンピューターの特定のセッション構成に対するユーザー アクセスを許可する承認規則が存在しない。</span><span class="sxs-lookup"><span data-stu-id="89e95-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="89e95-110">Windows PowerShell Web Access では制限的なセキュリティを採用しているため、承認規則を使ってリモート コンピューターへのアクセス権をユーザーに明示的に付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89e95-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="89e95-111">承認規則の作成の詳細については、「[Windows PowerShell Web Access の承認規則とセキュリティ機能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89e95-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="89e95-112">ユーザーによる対象コンピューターへのアクセスが承認されていない。</span><span class="sxs-lookup"><span data-stu-id="89e95-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="89e95-113">これはアクセス制御リスト (ACL) によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="89e95-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="89e95-114">詳細については、「[Windows PowerShell Web Access へのサインイン](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)」か Windows PowerShell チーム ブログを参照してください。</span><span class="sxs-lookup"><span data-stu-id="89e95-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="89e95-115">Windows PowerShell のリモート管理が対象コンピューター上で有効になっていない。</span><span class="sxs-lookup"><span data-stu-id="89e95-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="89e95-116">ユーザーが接続しようとしているコンピューターでリモート管理が有効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="89e95-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="89e95-117">詳細については、「[リモート処理用にコンピューターを構成する方法](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89e95-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="89e95-118">内部サーバー エラー</span><span class="sxs-lookup"><span data-stu-id="89e95-118">Internal Server Error</span></span>

<span data-ttu-id="89e95-119">ユーザーが Internet Explorer ウィンドウで Windows PowerShell Web Access にサインインしようとすると、**[内部サーバー エラー]** ページが表示されるか、*Internet Explorer* が応答しなくなる。</span><span class="sxs-lookup"><span data-stu-id="89e95-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="89e95-120">この問題は Internet Explorer に限られている。</span><span class="sxs-lookup"><span data-stu-id="89e95-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="89e95-121">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="89e95-121">Possible cause</span></span>

<span data-ttu-id="89e95-122">この問題は、ユーザーがサインイン時に指定したドメイン名に漢字が含まれていた場合や、ゲートウェイ サーバー名に 1 つ以上の漢字が含まれている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="89e95-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="89e95-123">回避策</span><span class="sxs-lookup"><span data-stu-id="89e95-123">Workaround</span></span>

1. <span data-ttu-id="89e95-124">[Internet Explorer 10 をインストールし、実行します](https://ie.microsoft.com/testdrive/info/downloads/Default.html)。</span><span class="sxs-lookup"><span data-stu-id="89e95-124">[Install and run Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)</span></span>
1. <span data-ttu-id="89e95-125">Internet Explorer の **[ドキュメント モード]** 設定を *[IE10 標準]* に変更します。</span><span class="sxs-lookup"><span data-stu-id="89e95-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="89e95-126">**F12** キーを押して開発者ツール コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="89e95-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="89e95-127">Internet Explorer 10 で、**[ブラウザー モード]** をクリックし、*[Internet Explorer 10]* をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89e95-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="89e95-128">**[ドキュメント モード]**、*[IE10 標準]* の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="89e95-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="89e95-129">もう一度 **F12** キーを押して開発者ツール コンソールを閉じます。</span><span class="sxs-lookup"><span data-stu-id="89e95-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="89e95-130">Internet Explorer 10 の自動プロキシ構成を無効にします。</span><span class="sxs-lookup"><span data-stu-id="89e95-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="89e95-131">**[ツール]**、 **[インターネット オプション]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="89e95-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="89e95-132">**[インターネット オプション]** ダイアログ ボックスの **[接続]** タブで、**[LAN の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89e95-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="89e95-133">**[設定を自動的に検出する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="89e95-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="89e95-134">**[OK]** をクリックし、もう一度 **[OK]** をクリックして、*[インターネット オプション]* ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="89e95-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="89e95-135">リモートのワークグループ コンピューターに接続できない</span><span class="sxs-lookup"><span data-stu-id="89e95-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="89e95-136">対象のコンピューターがワークグループ メンバーである場合、次の構文を使ってユーザー名を入力し、コンピューターにサインインします: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="89e95-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="89e95-137">ロールがインストールされているにもかかわらず Web サーバー (IIS) 管理ツールが見つからない</span><span class="sxs-lookup"><span data-stu-id="89e95-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="89e95-138">`Install-WindowsFeature` コマンドレットを使って Windows PowerShell Web Access をインストールした場合、コマンドレットに `-IncludeManagementTools` パラメーターを追加しない限り管理ツールはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="89e95-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="89e95-139">例については、「[Windows PowerShell コマンドレットを使って Windows PowerShell Web Access をインストールするには](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89e95-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="89e95-140">ゲートウェイ サーバーを対象とする**役割と機能の追加ウィザード**のセッションでツールを選択することで、IIS マネージャー コンソールとその他の必要な IIS 管理ツールを追加できます。</span><span class="sxs-lookup"><span data-stu-id="89e95-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="89e95-141">役割および機能の追加ウィザードは、サーバー マネージャー内で開きます。</span><span class="sxs-lookup"><span data-stu-id="89e95-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="89e95-142">Windows PowerShell Web Access Web サイトにアクセスできない</span><span class="sxs-lookup"><span data-stu-id="89e95-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="89e95-143">Internet Explorer セキュリティ強化の構成 (IE ESC) を有効にして、信頼済みサイトの一覧に Windows PowerShell Web Access Web サイトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="89e95-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="89e95-144">セキュリティ上の理由からお勧めはできませんが、IE ESC を無効にするという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="89e95-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="89e95-145">IE ESC は、サーバー マネージャーの [ローカル サーバー] ページの [プロパティ] タイルで無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="89e95-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="89e95-146">"承認エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="89e95-146">An authorization failure occurred.</span></span> <span data-ttu-id="89e95-147">対象のコンピューターに接続する権限が与えられているかどうかを確認してください。"</span><span class="sxs-lookup"><span data-stu-id="89e95-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="89e95-148">ゲートウェイ サーバーが対象のコンピューターであり、ワークグループ内にある場合に、接続しようとすると上記のエラー メッセージが表示される。</span><span class="sxs-lookup"><span data-stu-id="89e95-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="89e95-149">ゲートウェイ サーバーが対象のサーバーでもあり、ワークグループ内にある場合は、ユーザー名、コンピューター名、ユーザー グループ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="89e95-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="89e95-150">ドット (.) を単体で使用してコンピューター名を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="89e95-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="89e95-151">シナリオと適切な値</span><span class="sxs-lookup"><span data-stu-id="89e95-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="89e95-152">すべてのケース</span><span class="sxs-lookup"><span data-stu-id="89e95-152">All cases</span></span>

<span data-ttu-id="89e95-153">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89e95-153">Parameter</span></span> | <span data-ttu-id="89e95-154">値</span><span class="sxs-lookup"><span data-stu-id="89e95-154">Value</span></span>
-- | --
<span data-ttu-id="89e95-155">UserName</span><span class="sxs-lookup"><span data-stu-id="89e95-155">UserName</span></span> | <span data-ttu-id="89e95-156">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="89e95-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="89e95-157">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="89e95-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="89e95-158">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="89e95-158">.\\user\_name</span></span>
<span data-ttu-id="89e95-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="89e95-159">UserGroup</span></span> | <span data-ttu-id="89e95-160">Server\_name\\user\_group</span><span class="sxs-lookup"><span data-stu-id="89e95-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="89e95-161">Localhost\\user\_group</span><span class="sxs-lookup"><span data-stu-id="89e95-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="89e95-162">.\\user\_group</span><span class="sxs-lookup"><span data-stu-id="89e95-162">.\\user\_group</span></span>
<span data-ttu-id="89e95-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="89e95-163">ComputerGroup</span></span> | <span data-ttu-id="89e95-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="89e95-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="89e95-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="89e95-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="89e95-166">.\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="89e95-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="89e95-167">ゲートウェイ サーバーがドメイン内にある場合</span><span class="sxs-lookup"><span data-stu-id="89e95-167">Gateway server is in a domain</span></span>

<span data-ttu-id="89e95-168">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89e95-168">Parameter</span></span> | <span data-ttu-id="89e95-169">値</span><span class="sxs-lookup"><span data-stu-id="89e95-169">Value</span></span>
-- | --
<span data-ttu-id="89e95-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="89e95-170">ComputerName</span></span> | <span data-ttu-id="89e95-171">ゲートウェイ サーバーの完全修飾名または Localhost</span><span class="sxs-lookup"><span data-stu-id="89e95-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="89e95-172">ゲートウェイ サーバーがワークグループ内にある場合</span><span class="sxs-lookup"><span data-stu-id="89e95-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="89e95-173">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89e95-173">Parameter</span></span> | <span data-ttu-id="89e95-174">値</span><span class="sxs-lookup"><span data-stu-id="89e95-174">Value</span></span>
-- | --
<span data-ttu-id="89e95-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="89e95-175">ComputerName</span></span> | <span data-ttu-id="89e95-176">サーバー名</span><span class="sxs-lookup"><span data-stu-id="89e95-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="89e95-177">ゲートウェイの資格情報</span><span class="sxs-lookup"><span data-stu-id="89e95-177">Gateway credentials</span></span>

<span data-ttu-id="89e95-178">次のいずれかの形式の資格情報を使用して、対象コンピューターとしてゲートウェイ サーバーにサインインします。</span><span class="sxs-lookup"><span data-stu-id="89e95-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="89e95-179">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="89e95-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="89e95-180">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="89e95-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="89e95-181">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="89e95-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="89e95-182">セキュリティ識別子 (SID) が認証規則に表示される</span><span class="sxs-lookup"><span data-stu-id="89e95-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="89e95-183">承認規則内に、構文 user\_name/computer\_name ではなくセキュリティ識別子 (SID) が表示される</span><span class="sxs-lookup"><span data-stu-id="89e95-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="89e95-184">規則が有効ではなくなっているか、Active Directory Domain Services のクエリが失敗しています。</span><span class="sxs-lookup"><span data-stu-id="89e95-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="89e95-185">以前はワークグループ内にあったゲートウェイ サーバーが後でドメインに参加した場合は通常、承認規則は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="89e95-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="89e95-186">規則の IPv6 アドレスにドメインが含まれるとき、サインインできない</span><span class="sxs-lookup"><span data-stu-id="89e95-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="89e95-187">ドメインを伴う IPv6 アドレスとして承認規則内で指定されている対象コンピューターにサインインできない。</span><span class="sxs-lookup"><span data-stu-id="89e95-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="89e95-188">承認規則では、ドメイン名形式の IPv6 アドレスがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="89e95-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="89e95-189">IPv6 アドレスを使用して対象コンピューターを指定するには、承認規則内で元の (コロンを含む) IPv6 アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="89e95-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="89e95-190">Windows PowerShell Web Access のサインイン ページでは、ドメイン名形式の IPv6 アドレスも数値形式の (コロンを含む) IPv6 アドレスも対象コンピューター名としてサポートされていますが、承認規則内では異なります。</span><span class="sxs-lookup"><span data-stu-id="89e95-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="89e95-191">IPv6 アドレスの詳細については、[IPv6 の動作のしくみに関するページ](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89e95-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="89e95-192">参照</span><span class="sxs-lookup"><span data-stu-id="89e95-192">See Also</span></span>

- <span data-ttu-id="89e95-193">[Windows PowerShell Web Access の承認規則とセキュリティ機能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="89e95-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="89e95-194">[Web ベースの Windows PowerShell コンソールの使用](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="89e95-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="89e95-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="89e95-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)