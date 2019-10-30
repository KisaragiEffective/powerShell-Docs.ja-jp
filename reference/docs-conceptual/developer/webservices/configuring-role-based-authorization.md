---
title: ロールベースの承認を構成する |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359771"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="c2839-102">ロール ベースの認可を構成する</span><span class="sxs-lookup"><span data-stu-id="c2839-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="c2839-103">このトピックでは、「 [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) 管理のためのカスタム承認の実装」で説明されている Customauthorization インターフェイスのサンプル実装に対して、ロールベースの承認ポリシーを構成する方法について説明します。[OData IIS 拡張機能](./implementing-custom-authorization-for-a-management-odata-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="c2839-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="c2839-104">この例では、サンプル管理 OData アプリケーションで使用される XML ファイルを構成して、承認ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="c2839-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="c2839-105">2つのロールを作成し、ワークフローを含むさまざまな Windows PowerShell モジュールをそれらのロールに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="c2839-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="c2839-106">XML ファイルを定義するスキーマは、「[ロールベースの承認構成スキーマ](./role-based-authorization-configuration-schema.md)」に記載されています。</span><span class="sxs-lookup"><span data-stu-id="c2839-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="c2839-107">RBacConfiguration .xml ファイルの変更</span><span class="sxs-lookup"><span data-stu-id="c2839-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="c2839-108">このファイルは、アプリケーションの承認ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="c2839-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="c2839-109">ロールは `Group` ノードを使用して定義されます。</span><span class="sxs-lookup"><span data-stu-id="c2839-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="c2839-110">@No__t_0 ノードは、そのグループに割り当てられたユーザーが実行できる Windows PowerShell コマンドを定義します。</span><span class="sxs-lookup"><span data-stu-id="c2839-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="c2839-111">ユーザーは `User` ノードを使用してグループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c2839-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="c2839-112">これらの例では、[管理者 `Group`] ノードにモジュールを追加し、各グループにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="c2839-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="c2839-113">グループノードへのモジュールの追加</span><span class="sxs-lookup"><span data-stu-id="c2839-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="c2839-114">テキストエディターで、 **Rbacconfiguration**という名前のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c2839-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="c2839-115">このファイルは、web サービスのメインアプリケーションディレクトリに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2839-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="c2839-116">ファイルに次のテキストを挿入します。</span><span class="sxs-lookup"><span data-stu-id="c2839-116">Insert the following text in the file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. <span data-ttu-id="c2839-117">このファイルには、2つの `Group` ノードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2839-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="c2839-118">これらは、この例で使用される2つのロール、`NonAdminGroup` と `AdminGroup` ロールを表します。</span><span class="sxs-lookup"><span data-stu-id="c2839-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="c2839-119">最初の `Group` ノードの終了 `Cmdlets` タグのすぐ後に、次の XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2839-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="c2839-120">グループノードへのユーザーの追加</span><span class="sxs-lookup"><span data-stu-id="c2839-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="c2839-121">テキストエディターで、 **Rbacconfiguration .xml**ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c2839-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="c2839-122">このファイルは、インストール前にエンドポイント名を変更しなかった場合は、C: \\ \inetpub\wwwroot\Modata フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="c2839-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="c2839-123">[@No__t_0] ノードの終了タグのすぐ後に、次の XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2839-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="c2839-124">前の手順で追加した XML のすぐ後に、次の XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2839-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```