---
title: Windows PowerShell コンテンツ プロバイダーを作成する |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 1bccbfab55f4ba4476678b130bd9db91eed7df80
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795319"
---
# <a name="creating-a-windows-powershell-content-provider"></a><span data-ttu-id="d5ea2-102">Windows PowerShell コンテンツ プロバイダーを作成する</span><span class="sxs-lookup"><span data-stu-id="d5ea2-102">Creating a Windows PowerShell Content Provider</span></span>

<span data-ttu-id="d5ea2-103">このトピックでは、データ ストア内の項目の内容を操作するユーザーを有効にする Windows PowerShell プロバイダーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-103">This topic describes how to create a Windows PowerShell provider that enables the user to manipulate the contents of the items in a data store.</span></span> <span data-ttu-id="d5ea2-104">その結果、項目の内容を操作できるプロバイダーは Windows PowerShell コンテンツ プロバイダーとしてに呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-104">As a consequence, a provider that can manipulate the contents of items is referred to as a Windows PowerShell content provider.</span></span>

> [!NOTE]
> <span data-ttu-id="d5ea2-105">ダウンロードすることができます、 C# Microsoft Windows ソフトウェア開発キットの Windows Vista と .NET Framework 3.0 ランタイム コンポーネントを使用して、このプロバイダーのソース ファイル (AccessDBSampleProvider06.cs)。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d5ea2-106">ダウンロードの手順については、次を参照してください。 [Windows PowerShell のインストールと、Windows PowerShell SDK をダウンロードする方法](/powershell/developer/installing-the-windows-powershell-sdk)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d5ea2-107">ダウンロードしたソース ファイルは、  **\<PowerShell のサンプル >** ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="d5ea2-108">その他の Windows PowerShell プロバイダーの実装の詳細については、次を参照してください。 [Your Windows PowerShell プロバイダーの設計](./designing-your-windows-powershell-provider.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="d5ea2-109">次の一覧には、このトピックのセクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-109">The following list contains the sections in this topic.</span></span> <span data-ttu-id="d5ea2-110">Windows PowerShell コンテンツ プロバイダーの作成に慣れていない場合は、出現する順序でこれらのセクションを参照します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-110">If you are unfamiliar with writing a Windows PowerShell content provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="d5ea2-111">ただし、Windows PowerShell コンテンツ プロバイダーの作成に習熟する場合は、必要な情報に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-111">However, if you are familiar with writing a Windows PowerShell content provider, go directly to the information that you need.</span></span>

- [<span data-ttu-id="d5ea2-112">Windows PowerShell コンテンツ プロバイダー クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-112">Defining the Windows PowerShell Content Provider Class</span></span>](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [<span data-ttu-id="d5ea2-113">基本機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-113">Defining Base Functionality</span></span>](#Define-Functionality-of-Base-Class)

- [<span data-ttu-id="d5ea2-114">コンテンツのリーダーの実装</span><span class="sxs-lookup"><span data-stu-id="d5ea2-114">Implementing a Content Reader</span></span>](#Implementing-a-Content-Reader)

- [<span data-ttu-id="d5ea2-115">コンテンツのライターの実装</span><span class="sxs-lookup"><span data-stu-id="d5ea2-115">Implementing a Content Writer</span></span>](#Implementing-a-Content-Writer)

- [<span data-ttu-id="d5ea2-116">コンテンツのリーダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-116">Retrieving the Content Reader</span></span>](#Retrieving-the-Content-Reader)

- [<span data-ttu-id="d5ea2-117">動的パラメーターをアタッチ、`Get-Content`コマンドレット</span><span class="sxs-lookup"><span data-stu-id="d5ea2-117">Attaching Dynamic Parameters to the `Get-Content` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [<span data-ttu-id="d5ea2-118">コンテンツのライターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-118">Retrieving the Content Writer</span></span>](#Retrieving-the-Content-Writer)

- [<span data-ttu-id="d5ea2-119">動的パラメーター、Add_Content をアタッチし、`Set-Content`コマンドレット</span><span class="sxs-lookup"><span data-stu-id="d5ea2-119">Attaching Dynamic Parameters to the Add_Content and `Set-Content` Cmdlets</span></span>](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [<span data-ttu-id="d5ea2-120">コンテンツをクリアします。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-120">Clearing Content</span></span>](#Clearing-Content)

- [<span data-ttu-id="d5ea2-121">動的パラメーターをアタッチ、`Clear-Content`コマンドレット</span><span class="sxs-lookup"><span data-stu-id="d5ea2-121">Attaching Dynamic Parameters to the  `Clear-Content` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [<span data-ttu-id="d5ea2-122">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="d5ea2-122">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="d5ea2-123">オブジェクトの種類を定義して、書式設定</span><span class="sxs-lookup"><span data-stu-id="d5ea2-123">Defining Object Types and Formatting</span></span>](#defining-object-types-and-formatting)

- [<span data-ttu-id="d5ea2-124">Windows PowerShell プロバイダーの構築</span><span class="sxs-lookup"><span data-stu-id="d5ea2-124">Building the Windows PowerShell provider</span></span>](#Building-the-Windows-PowerShell-Provider)

- [<span data-ttu-id="d5ea2-125">Windows PowerShell プロバイダーのテスト</span><span class="sxs-lookup"><span data-stu-id="d5ea2-125">Testing the Windows PowerShell provider</span></span>](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a><span data-ttu-id="d5ea2-126">Windows PowerShell コンテンツ プロバイダー クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-126">Define the Windows PowerShell Content Provider Class</span></span>

<span data-ttu-id="d5ea2-127">Windows PowerShell コンテンツ プロバイダーがサポートする .NET クラスを作成する必要があります、 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-127">A Windows PowerShell content provider must create a .NET class that supports the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span> <span data-ttu-id="d5ea2-128">このセクションで説明されている項目プロバイダーのクラス定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-128">Here is the class definition for the item provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

<span data-ttu-id="d5ea2-129">このクラス定義を[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性には、2 つのパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-129">Note that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="d5ea2-130">最初のパラメーターには、Windows PowerShell で使用されるプロバイダーのわかりやすい名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-130">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="d5ea2-131">2 番目のパラメーターには、プロバイダーがコマンドの処理中に、Windows PowerShell ランタイムに公開する Windows PowerShell の特定機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-131">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="d5ea2-132">このプロバイダーでは、追加した Windows PowerShell の特定の機能はありません。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-132">For this provider, there are no added Windows PowerShell specific capabilities.</span></span>

## <a name="define-functionality-of-base-class"></a><span data-ttu-id="d5ea2-133">基底クラスの機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-133">Define Functionality of Base Class</span></span>

<span data-ttu-id="d5ea2-134">」の説明に従って[デザイン、Windows PowerShell プロバイダー](./designing-your-windows-powershell-provider.md)、 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)クラスが提供されるその他のいくつかのクラスから派生別のプロバイダー機能。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-134">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="d5ea2-135">Windows PowerShell コンテンツ プロバイダーでは、そのため、通常定義のすべてのこれらのクラスによって提供される機能します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-135">A Windows PowerShell content provider, therefore, typically defines all of the functionality provided by those classes.</span></span>

<span data-ttu-id="d5ea2-136">セッション固有の初期化情報を追加して、プロバイダーによって使用されているリソースを解放するための機能を実装する方法の詳細については、次を参照してください。[基本的な Windows PowerShell プロバイダーを作成する](./creating-a-basic-windows-powershell-provider.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-136">For more information about how to implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="d5ea2-137">ただし、ここでは、説明されているプロバイダーを含む、ほとんどのプロバイダーは、この Windows PowerShell によって提供される機能の既定の実装を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-137">However, most providers, including the provider described here, can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="d5ea2-138">データ ストアにアクセスするには、プロバイダーがのメソッドを実装する必要があります、 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基本クラス。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-138">To access the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="d5ea2-139">これらのメソッドの実装の詳細については、次を参照してください。 [Windows PowerShell ドライブ プロバイダーを作成する](./creating-a-windows-powershell-drive-provider.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-139">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="d5ea2-140">プロバイダーの取得、設定、および消去の項目などのデータ ストアの項目を操作するによって提供されるメソッドを実装する必要があります、 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基本クラス。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-140">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="d5ea2-141">これらのメソッドの実装の詳細については、次を参照してください。 [Windows PowerShell 項目プロバイダーを作成する](./creating-a-windows-powershell-item-provider.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-141">For more information about implementing these methods, see [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="d5ea2-142">プロバイダーを複数レイヤーのデータ ストアを操作するによって提供されるメソッドを実装する必要があります、 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基本クラス。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-142">To work on multi-layer data stores, the provider must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="d5ea2-143">これらのメソッドの実装の詳細については、次を参照してください。 [Windows PowerShell コンテナー プロバイダーを作成する](./creating-a-windows-powershell-container-provider.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-143">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

<span data-ttu-id="d5ea2-144">再帰的なコマンド、入れ子になったコンテナーは、相対パスをサポートするプロバイダーを実装する必要があります、 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基本クラス。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-144">To support recursive commands, nested containers, and relative paths, the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="d5ea2-145">この Windows PowerShell コンテンツ プロバイダーの接続はさらに、 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)へのインターフェイス、 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基本クラス、および、したがって、そのクラスによって提供されるメソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-145">In addition, this Windows PowerShell content provider can attaches [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface to the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class, and must therefore implement the methods provided by that class.</span></span> <span data-ttu-id="d5ea2-146">詳細については、これらのメソッドの実装を参照してくださいを参照してください[ナビゲーションの Windows PowerShell プロバイダーを実装する](./creating-a-windows-powershell-navigation-provider.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-146">For more information, see implementing those methods, see [Implement a Navigation Windows PowerShell Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

## <a name="implementing-a-content-reader"></a><span data-ttu-id="d5ea2-147">コンテンツのリーダーの実装</span><span class="sxs-lookup"><span data-stu-id="d5ea2-147">Implementing a Content Reader</span></span>

<span data-ttu-id="d5ea2-148">項目からコンテンツを読み取る、プロバイダーがから派生したコンテンツのリーダー クラスを実装する必要があります[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-148">To read content from an item, a provider must implements a content reader class that derives from [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).</span></span> <span data-ttu-id="d5ea2-149">このプロバイダーのコンテンツのリーダーは、データ テーブルの行の内容にアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-149">The content reader for this provider allows access to the contents of a row in a data table.</span></span> <span data-ttu-id="d5ea2-150">コンテンツのリーダー クラスを定義、**読み取り**メソッドを指定された行からデータを取得し、そのデータを表すリストを返します、**シーク**コンテンツのリーダーを移動する方法、 **閉じる**メソッドをコンテンツのリーダーを閉じると、 **Dispose**メソッド。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-150">The content reader class defines a **Read** method that retrieves the data from the indicated row and returns a list representing that data, a **Seek** method that moves the content reader, a **Close** method that closes the content reader, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a><span data-ttu-id="d5ea2-151">コンテンツのライターの実装</span><span class="sxs-lookup"><span data-stu-id="d5ea2-151">Implementing a Content Writer</span></span>

<span data-ttu-id="d5ea2-152">コンテンツは、項目を書き込む、プロバイダーが、コンテンツを実装する必要がありますライター クラスから派生[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-152">To write content to an item, a provider must implement a content writer class derives from [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).</span></span> <span data-ttu-id="d5ea2-153">コンテンツ ライター クラスを定義、**書き込み**指定した行の内容を書き込むメソッドを**シーク**コンテンツのライターを移動する方法、**閉じる**を閉じる方法、コンテンツのライター、 **Dispose**メソッド。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-153">The content writer class defines a **Write** method that writes the specified row content, a **Seek** method that moves the content writer, a **Close** method that closes the content writer, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a><span data-ttu-id="d5ea2-154">コンテンツのリーダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-154">Retrieving the Content Reader</span></span>

<span data-ttu-id="d5ea2-155">項目からコンテンツを取得するプロバイダーを実装する必要があります、 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)サポートするために、`Get-Content`コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-155">To get content from an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) to support the `Get-Content` cmdlet.</span></span> <span data-ttu-id="d5ea2-156">このメソッドは、指定されたパスにある項目のコンテンツのリーダーを返します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-156">This method returns the content reader for the item located at the specified path.</span></span> <span data-ttu-id="d5ea2-157">リーダー オブジェクトは、コンテンツの読み取り開くことができます。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-157">The reader object can then be opened to read the content.</span></span>

<span data-ttu-id="d5ea2-158">実装を次に示します[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)このプロバイダーは、このメソッドにします。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-158">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) for this method for this provider.</span></span>

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a><span data-ttu-id="d5ea2-159">GetContentReader の実装に関する注意点</span><span class="sxs-lookup"><span data-stu-id="d5ea2-159">Things to Remember About Implementing GetContentReader</span></span>

<span data-ttu-id="d5ea2-160">実装を次の条件が適用[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span><span class="sxs-lookup"><span data-stu-id="d5ea2-160">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span></span>

- <span data-ttu-id="d5ea2-161">Windows PowerShell コンテンツ プロバイダーがから ExpandWildcards、フィルター、インクルード、または除外するには、プロバイダーの機能を宣言可能性があります、プロバイダー クラスを定義するときに、 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列挙体。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-161">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="d5ea2-162">これらのケースの実装で、 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)メソッドがメソッドに渡されたパスが指定した要件を満たしていることを確認する必要があります機能。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-162">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="d5ea2-163">これを行うには、メソッドがプロパティにアクセス適切なたとえば、 [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)と[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-163">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="d5ea2-164">既定では、このメソッドのオーバーライドを取得しないようにしない限り、ユーザーが非表示オブジェクト用のリーダー、 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)プロパティに設定されて`true`します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-164">By default, overrides of this method should not retrieve a reader for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="d5ea2-165">パスが、ユーザーが非表示の項目を表すかどうかエラーを記述する必要がありますと[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)に設定されている`false`します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-165">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a><span data-ttu-id="d5ea2-166">動的パラメーター、Get-content コマンドレットをアタッチ</span><span class="sxs-lookup"><span data-stu-id="d5ea2-166">Attaching Dynamic Parameters to the Get-Content Cmdlet</span></span>

<span data-ttu-id="d5ea2-167">`Get-Content`コマンドレットは、実行時に動的に指定されている追加のパラメーターを必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-167">The `Get-Content` cmdlet might require additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="d5ea2-168">これらの動的パラメーターを提供する Windows PowerShell コンテンツ プロバイダーを実装する必要があります、 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)メソッド。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-168">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span> <span data-ttu-id="d5ea2-169">このメソッドは、指定されたパスにある項目の動的パラメーターを取得し、プロパティと、コマンドレット クラスのように属性を解析してフィールドを持つオブジェクトを返しますまたは[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-169">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="d5ea2-170">Windows PowerShell ランタイムでは、返されたオブジェクトを使用して、パラメーターをコマンドレットに追加します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-170">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="d5ea2-171">この Windows PowerShell コンテナー プロバイダーは、このメソッドを実装していません。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-171">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="d5ea2-172">ただし、次のコードは、このメソッドの既定の実装です。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-172">However, the following code is the default implementation of this method.</span></span>

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a><span data-ttu-id="d5ea2-173">コンテンツのライターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-173">Retrieving the Content Writer</span></span>

<span data-ttu-id="d5ea2-174">コンテンツは、項目を書き込む、プロバイダーを実装する必要があります、 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)サポートするために、`Set-Content`と`Add-Content`コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-174">To write content to an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) to support the `Set-Content` and `Add-Content` cmdlets.</span></span> <span data-ttu-id="d5ea2-175">このメソッドは、指定されたパスにある項目のコンテンツのライターを返します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-175">This method returns the content writer for the item located at the specified path.</span></span>

<span data-ttu-id="d5ea2-176">実装を次に示します[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)このメソッドにします。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-176">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) for this method.</span></span>

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a><span data-ttu-id="d5ea2-177">GetContentWriter の実装に関する注意点</span><span class="sxs-lookup"><span data-stu-id="d5ea2-177">Things to Remember About Implementing GetContentWriter</span></span>

<span data-ttu-id="d5ea2-178">実装に、次の条件が適用[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span><span class="sxs-lookup"><span data-stu-id="d5ea2-178">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span></span>

- <span data-ttu-id="d5ea2-179">Windows PowerShell コンテンツ プロバイダーがから ExpandWildcards、フィルター、インクルード、または除外するには、プロバイダーの機能を宣言可能性があります、プロバイダー クラスを定義するときに、 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列挙体。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-179">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="d5ea2-180">これらのケースの実装で、 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)メソッドがメソッドに渡されたパスが指定した要件を満たしていることを確認する必要があります機能。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-180">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="d5ea2-181">これを行うには、メソッドがプロパティにアクセス適切なたとえば、 [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)と[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-181">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="d5ea2-182">既定では、このメソッドのオーバーライドを取得しないように、しない限り、ユーザーが非表示オブジェクトのライター、 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)プロパティに設定されて`true`します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-182">By default, overrides of this method should not retrieve a writer for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="d5ea2-183">パスが、ユーザーが非表示の項目を表すかどうかエラーを記述する必要がありますと[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)に設定されている`false`します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-183">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a><span data-ttu-id="d5ea2-184">動的パラメーター、Add-content、Set-content コマンドレットをアタッチ</span><span class="sxs-lookup"><span data-stu-id="d5ea2-184">Attaching Dynamic Parameters to the Add-Content and Set-Content Cmdlets</span></span>

<span data-ttu-id="d5ea2-185">`Add-Content`と`Set-Content`コマンドレットは、ランタイムに追加される追加の動的パラメーターを必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-185">The `Add-Content` and `Set-Content` cmdlets might require additional dynamic parameters that are added a runtime.</span></span> <span data-ttu-id="d5ea2-186">これらの動的パラメーターを提供する Windows PowerShell コンテンツ プロバイダーを実装する必要があります、 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)これらを処理するメソッドパラメーター。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-186">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="d5ea2-187">このメソッドは、指定されたパスにある項目の動的パラメーターを取得し、プロパティと、コマンドレット クラスのように属性を解析してフィールドを持つオブジェクトを返しますまたは[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-187">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="d5ea2-188">Windows PowerShell ランタイムでは、返されたオブジェクトを使用して、パラメーターをコマンドレットに追加します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-188">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlets.</span></span>

<span data-ttu-id="d5ea2-189">この Windows PowerShell コンテナー プロバイダーは、このメソッドを実装していません。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-189">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="d5ea2-190">ただし、次のコードは、このメソッドの既定の実装です。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-190">However, the following code is the default implementation of this method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a><span data-ttu-id="d5ea2-191">コンテンツをクリアします。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-191">Clearing Content</span></span>

<span data-ttu-id="d5ea2-192">コンテンツ プロバイダーの実装、 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)メソッドのサポート、`Clear-Content`コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-192">Your content provider implements the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method in support of the `Clear-Content` cmdlet.</span></span> <span data-ttu-id="d5ea2-193">このメソッドは、指定したパスにある項目の内容を削除しますが、項目をそのまま残されます。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-193">This method removes the contents of the item at the specified path, but leaves the item intact.</span></span>

<span data-ttu-id="d5ea2-194">実装をここでは、 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)このプロバイダーのメソッド。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-194">Here is the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method for this provider.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a><span data-ttu-id="d5ea2-195">ClearContent の実装に関する注意点</span><span class="sxs-lookup"><span data-stu-id="d5ea2-195">Things to Remember About Implementing ClearContent</span></span>

<span data-ttu-id="d5ea2-196">実装を次の条件が適用[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span><span class="sxs-lookup"><span data-stu-id="d5ea2-196">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span></span>

- <span data-ttu-id="d5ea2-197">Windows PowerShell コンテンツ プロバイダーがから ExpandWildcards、フィルター、インクルード、または除外するには、プロバイダーの機能を宣言可能性があります、プロバイダー クラスを定義するときに、 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列挙体。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-197">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="d5ea2-198">これらのケースの実装で、 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)メソッドがメソッドに渡されたパスが指定した要件を満たしていることを確認する必要があります機能。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-198">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="d5ea2-199">これを行うには、メソッドがプロパティにアクセス適切なたとえば、 [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)と[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-199">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="d5ea2-200">既定では、このメソッドのオーバーライドする必要がありますいないをオフにしない限り、ユーザーが非表示オブジェクトの内容、 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)プロパティに設定されて`true`します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-200">By default, overrides of this method should not clear the contents of objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="d5ea2-201">パスが、ユーザーが非表示の項目を表すかどうかエラーを記述する必要がありますと[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)に設定されている`false`します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-201">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

- <span data-ttu-id="d5ea2-202">実装、 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)メソッドを呼び出す必要があります[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)をデータ ストアに変更を加える前に、その戻り値を確認します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-202">Your implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and verify its return value before making any changes to the data store.</span></span> <span data-ttu-id="d5ea2-203">このメソッドは、コンテンツをクリアするなど、データ ストアに変更が行われる操作の実行の確認に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-203">This method is used to confirm execution of an operation when a change is made to the data store, such as clearing content.</span></span> <span data-ttu-id="d5ea2-204">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)メソッドは、任意のコマンドライン設定や基本設定処理の Windows PowerShell ランタイムと、ユーザーに変更するリソースの名前を送信します。何を表示するかを決定するのには変数。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-204">The [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) method sends the name of the resource to be changed to the user, with the Windows PowerShell runtime handling any command-line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="d5ea2-205">呼び出し後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返します`true`、 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)メソッドを呼び出す必要があります、 [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)メソッド。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-205">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="d5ea2-206">このメソッドは、ユーザーにフィードバックするかどうかは、操作を続行することを確認できるようにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-206">This method sends a message to the user to allow feedback to verify if the operation should be continued.</span></span> <span data-ttu-id="d5ea2-207">呼び出し[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)危険性のあるシステムの変更、追加のチェックを許可します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-207">The call to [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) allows an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a><span data-ttu-id="d5ea2-208">Clear-content コマンドレットへの動的パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5ea2-208">Attaching Dynamic Parameters to the Clear-Content Cmdlet</span></span>

<span data-ttu-id="d5ea2-209">`Clear-Content`コマンドレットは、実行時に追加される追加の動的パラメーターを必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-209">The `Clear-Content` cmdlet might require additional dynamic parameters that are added at runtime.</span></span> <span data-ttu-id="d5ea2-210">これらの動的パラメーターを提供する Windows PowerShell コンテンツ プロバイダーを実装する必要があります、 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)これらを処理するメソッドパラメーター。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-210">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="d5ea2-211">このメソッドは、指定されたパスにある項目のパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-211">This method retrieves the parameters for the item at the indicated path.</span></span> <span data-ttu-id="d5ea2-212">このメソッドは、指定されたパスにある項目の動的パラメーターを取得し、プロパティと、コマンドレット クラスのように属性を解析してフィールドを持つオブジェクトを返しますまたは[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-212">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="d5ea2-213">Windows PowerShell ランタイムでは、返されたオブジェクトを使用して、パラメーターをコマンドレットに追加します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-213">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="d5ea2-214">この Windows PowerShell コンテナー プロバイダーは、このメソッドを実装していません。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-214">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="d5ea2-215">ただし、次のコードは、このメソッドの既定の実装です。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-215">However, the following code is the default implementation of this method.</span></span>

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a><span data-ttu-id="d5ea2-216">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="d5ea2-216">Code Sample</span></span>

<span data-ttu-id="d5ea2-217">完全なサンプル コードでは、次を参照してください。 [AccessDbProviderSample06 コード サンプル](./accessdbprovidersample06-code-sample.md)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-217">For complete sample code, see [AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="d5ea2-218">オブジェクトの種類を定義して、書式設定</span><span class="sxs-lookup"><span data-stu-id="d5ea2-218">Defining Object Types and Formatting</span></span>

<span data-ttu-id="d5ea2-219">プロバイダーを記述する場合は、既存のオブジェクトにメンバーを追加または新しいオブジェクトを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-219">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="d5ea2-220">これが完了したら、Windows PowerShell がオブジェクトのメンバーを識別するために使用できる種類のファイルと、オブジェクトの表示方法を定義するフォーマット ファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-220">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="d5ea2-221">詳細については、次を参照してください。[を拡張するオブジェクトの種類と書式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-221">For more information, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="d5ea2-222">Windows PowerShell プロバイダーのビルド</span><span class="sxs-lookup"><span data-stu-id="d5ea2-222">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="d5ea2-223">参照してください[登録コマンドレット、プロバイダー、およびアプリケーションをホストする方法](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-223">See [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="d5ea2-224">Windows PowerShell プロバイダーのテスト</span><span class="sxs-lookup"><span data-stu-id="d5ea2-224">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="d5ea2-225">Windows PowerShell を使用した、Windows PowerShell プロバイダーを登録しているときに、コマンドラインでサポートされているコマンドレットを実行してテストできます。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-225">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="d5ea2-226">たとえば、サンプルのコンテンツ プロバイダーをテストします。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-226">For example, test the sample content provider.</span></span>

<span data-ttu-id="d5ea2-227">使用して、`Get-Content`によって指定されたパスにデータベース テーブル内の指定項目の内容を取得するコマンドレット、`Path`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-227">Use the `Get-Content` cmdlet to retrieve the contents of specified item in the database table at the path specified by the `Path` parameter.</span></span> <span data-ttu-id="d5ea2-228">`ReadCount`パラメーター (既定値は 1) の読み取りに定義されているコンテンツのリーダーの項目の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-228">The `ReadCount` parameter specifies the number of items for the defined content reader to read (default 1).</span></span> <span data-ttu-id="d5ea2-229">次のコマンドのエントリは、このコマンドレットは、テーブルから 2 つの行 (アイテム) を取得し、その内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-229">With the following command entry, the cmdlet retrieves two rows (items) from the table and displays their contents.</span></span> <span data-ttu-id="d5ea2-230">次の出力例は架空の Access データベースに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-230">Note that the following example output uses a fictitious Access database.</span></span>

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a><span data-ttu-id="d5ea2-231">参照</span><span class="sxs-lookup"><span data-stu-id="d5ea2-231">See Also</span></span>

[<span data-ttu-id="d5ea2-232">Windows PowerShell プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-232">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="d5ea2-233">デザイン、Windows PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d5ea2-233">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="d5ea2-234">オブジェクトの種類を拡張して、書式設定</span><span class="sxs-lookup"><span data-stu-id="d5ea2-234">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="d5ea2-235">ナビゲーションの Windows PowerShell プロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="d5ea2-235">Implement a Navigation Windows PowerShell provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

[<span data-ttu-id="d5ea2-236">登録のコマンドレット、プロバイダー、およびアプリケーションをホストする方法</span><span class="sxs-lookup"><span data-stu-id="d5ea2-236">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="d5ea2-237">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d5ea2-237">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="d5ea2-238">Windows PowerShell プログラマー ガイド</span><span class="sxs-lookup"><span data-stu-id="d5ea2-238">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)