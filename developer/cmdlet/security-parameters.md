---
title: セキュリティのパラメーター |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: c8b3f907a80d1f6125a5ac04236245503db76ed0
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251304"
---
# <a name="security-parameters"></a><span data-ttu-id="78a37-102">セキュリティのパラメーター</span><span class="sxs-lookup"><span data-stu-id="78a37-102">Security Parameters</span></span>

<span data-ttu-id="78a37-103">次の表は、推奨される名前と証明書のキーと特権情報を指定するパラメーターなどの操作のセキュリティ情報を提供するためのパラメーターの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="78a37-103">The following table lists the recommended names and functionality for parameters used to provide security information for an operation, such as parameters that specify certificate key and privilege information.</span></span>

|<span data-ttu-id="78a37-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78a37-104">Parameter</span></span>|<span data-ttu-id="78a37-105">機能</span><span class="sxs-lookup"><span data-stu-id="78a37-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="78a37-106">**ACL**</span><span class="sxs-lookup"><span data-stu-id="78a37-106">**ACL**</span></span><br><span data-ttu-id="78a37-107">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-107">Data type: String</span></span>|<span data-ttu-id="78a37-108">カタログのまたはする Uniform Resource Identifier (URI) の保護のアクセス制御のレベルを指定するには、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-108">Implement this parameter to specify the access control level of protection for a catalog or for a Uniform Resource Identifier (URI).</span></span>|
|<span data-ttu-id="78a37-109">**CertFile**</span><span class="sxs-lookup"><span data-stu-id="78a37-109">**CertFile**</span></span><br><span data-ttu-id="78a37-110">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-110">Data type: String</span></span>|<span data-ttu-id="78a37-111">ユーザーは、次のいずれかを含むファイルの名前を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-111">Implement this parameter so that the user can specify the name of a file that contains one of the following:</span></span><br><span data-ttu-id="78a37-112">-Base64 または Distinguished Encoding Rules (DER) でエンコードされた x.509 証明書</span><span class="sxs-lookup"><span data-stu-id="78a37-112">- A Base64 or Distinguished Encoding Rules (DER) encoded x.509 certificate</span></span><br><span data-ttu-id="78a37-113">-少なくとも 1 つの証明書とキーを含む公開キー暗号化標準 (PKCS) #12 ファイル</span><span class="sxs-lookup"><span data-stu-id="78a37-113">- A Public Key Cryptography Standards (PKCS) #12 file that contains at least one certificate and key</span></span>|
|<span data-ttu-id="78a37-114">**CertIssuerName**</span><span class="sxs-lookup"><span data-stu-id="78a37-114">**CertIssuerName**</span></span><br><span data-ttu-id="78a37-115">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-115">Data type: String</span></span>|<span data-ttu-id="78a37-116">ユーザーが証明書の発行者の名前を指定できるように、または、ユーザーは、部分文字列を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-116">Implement this parameter so that the user can specify the name of the issuer of a certificate or so that the user can specify a substring.</span></span>|
|<span data-ttu-id="78a37-117">**CertRequestFile**</span><span class="sxs-lookup"><span data-stu-id="78a37-117">**CertRequestFile**</span></span><br><span data-ttu-id="78a37-118">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-118">Data type: String</span></span>|<span data-ttu-id="78a37-119">Base64 または DER でエンコードされた PKCS #10 証明書の要求を含むファイルの名前を指定するには、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-119">Implement this parameter to specify the name of a file that contains a Base64 or DER-encoded PKCS #10 certificate request.</span></span>|
|<span data-ttu-id="78a37-120">**CertSerialNumber**</span><span class="sxs-lookup"><span data-stu-id="78a37-120">**CertSerialNumber**</span></span><br><span data-ttu-id="78a37-121">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-121">Data type: String</span></span>|<span data-ttu-id="78a37-122">証明機関によって発行されたシリアル番号を指定するには、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-122">Implement this parameter to specify the serial number that was issued by the certification authority.</span></span>|
|<span data-ttu-id="78a37-123">**CertStoreLocation**</span><span class="sxs-lookup"><span data-stu-id="78a37-123">**CertStoreLocation**</span></span><br><span data-ttu-id="78a37-124">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-124">Data type: String</span></span>|<span data-ttu-id="78a37-125">ユーザーが証明書ストアの場所を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-125">Implement this parameter so that the user can specify the location of the certificate store.</span></span> <span data-ttu-id="78a37-126">場所は、通常、ファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="78a37-126">The location is typically a file path.</span></span>|
|<span data-ttu-id="78a37-127">**CertSubjectName**</span><span class="sxs-lookup"><span data-stu-id="78a37-127">**CertSubjectName**</span></span><br><span data-ttu-id="78a37-128">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-128">Data type: String</span></span>|<span data-ttu-id="78a37-129">ユーザーが証明書の発行者を指定できるように、または、ユーザーは、部分文字列を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-129">Implement this parameter so that the user can specify the issuer of a certificate or so that the user can specify a substring.</span></span>|
|<span data-ttu-id="78a37-130">**CertUsage**</span><span class="sxs-lookup"><span data-stu-id="78a37-130">**CertUsage**</span></span><br><span data-ttu-id="78a37-131">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-131">Data type: String</span></span>|<span data-ttu-id="78a37-132">キー使用法または拡張キー使用法を指定するには、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-132">Implement this parameter to specify the key usage or the enhanced key usage.</span></span> <span data-ttu-id="78a37-133">キーは、ビット マスクを少し、オブジェクト識別子 (OID) または文字列を表現できます。</span><span class="sxs-lookup"><span data-stu-id="78a37-133">The key can be represented as a bit mask, a bit, an object identifier (OID), or a string.</span></span>|
|<span data-ttu-id="78a37-134">**資格情報**</span><span class="sxs-lookup"><span data-stu-id="78a37-134">**Credential**</span></span><br><span data-ttu-id="78a37-135">データの種類:[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="78a37-135">Data type: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span></span>|<span data-ttu-id="78a37-136">このパラメーターを実装するは、コマンドレットによってユーザー名またはパスワードをユーザーが自動的に要求できるようにします。</span><span class="sxs-lookup"><span data-stu-id="78a37-136">Implement this parameter so that the cmdlet will automatically prompt the user for a user name or password.</span></span> <span data-ttu-id="78a37-137">完全な資格情報が直接指定されていない場合は、両方のプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="78a37-137">A prompt for both is displayed if a full credential is not supplied directly.</span></span>|
|<span data-ttu-id="78a37-138">**CSPName**</span><span class="sxs-lookup"><span data-stu-id="78a37-138">**CSPName**</span></span><br><span data-ttu-id="78a37-139">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-139">Data type: String</span></span>|<span data-ttu-id="78a37-140">ユーザーが証明書サービス プロバイダー (CSP) の名前を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-140">Implement this parameter so that the user can specify the name of the certificate service provider (CSP).</span></span>|
|<span data-ttu-id="78a37-141">**CSPType**</span><span class="sxs-lookup"><span data-stu-id="78a37-141">**CSPType**</span></span><br><span data-ttu-id="78a37-142">データの種類:整数</span><span class="sxs-lookup"><span data-stu-id="78a37-142">Data type: Integer</span></span>|<span data-ttu-id="78a37-143">ユーザーは、CSP の種類を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-143">Implement this parameter so that the user can specify the type of CSP.</span></span>|
|<span data-ttu-id="78a37-144">**グループ**</span><span class="sxs-lookup"><span data-stu-id="78a37-144">**Group**</span></span><br><span data-ttu-id="78a37-145">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-145">Data type: String</span></span>|<span data-ttu-id="78a37-146">ユーザーが使用するプリンシパルのアクセスのコレクションを指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-146">Implement this parameter so that the user can specify a collection of principals for access.</span></span> <span data-ttu-id="78a37-147">詳細については、の説明を参照して、**プリンシパル**パラメーター。</span><span class="sxs-lookup"><span data-stu-id="78a37-147">For more information, see the description of the **Principal** parameter.</span></span>|
|<span data-ttu-id="78a37-148">**KeyAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="78a37-148">**KeyAlgorithm**</span></span><br><span data-ttu-id="78a37-149">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-149">Data type: String</span></span>|<span data-ttu-id="78a37-150">ユーザーがセキュリティに使用するキーの生成アルゴリズムを指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-150">Implement this parameter so that the user can specify the key generation algorithm to use for security.</span></span>|
|<span data-ttu-id="78a37-151">**キーコンテナー名**</span><span class="sxs-lookup"><span data-stu-id="78a37-151">**KeyContainerName**</span></span><br><span data-ttu-id="78a37-152">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-152">Data type: String</span></span>|<span data-ttu-id="78a37-153">ユーザーがキー コンテナーの名前を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-153">Implement this parameter so that the user can specify the name of the key container.</span></span>|
|<span data-ttu-id="78a37-154">**KeyLength**</span><span class="sxs-lookup"><span data-stu-id="78a37-154">**KeyLength**</span></span><br><span data-ttu-id="78a37-155">データの種類:整数</span><span class="sxs-lookup"><span data-stu-id="78a37-155">Data type: Integer</span></span>|<span data-ttu-id="78a37-156">ユーザーは、キーの長さをビット単位で指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-156">Implement this parameter so that the user can specify the length of the key in bits.</span></span>|
|<span data-ttu-id="78a37-157">**操作**</span><span class="sxs-lookup"><span data-stu-id="78a37-157">**Operation**</span></span><br><span data-ttu-id="78a37-158">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-158">Data type: String</span></span>|<span data-ttu-id="78a37-159">ユーザーが保護されているオブジェクトで実行できるアクションを指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-159">Implement this parameter so that the user can specify an action that can be performed on a protected object.</span></span>|
|<span data-ttu-id="78a37-160">**プリンシパル**</span><span class="sxs-lookup"><span data-stu-id="78a37-160">**Principal**</span></span><br><span data-ttu-id="78a37-161">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-161">Data type: String</span></span>|<span data-ttu-id="78a37-162">このパラメーターを実装するは、ユーザーがアクセスを特定できる一意のエンティティを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="78a37-162">Implement this parameter so that the user can specify a unique identifiable entity for access.</span></span>|
|<span data-ttu-id="78a37-163">**特権**</span><span class="sxs-lookup"><span data-stu-id="78a37-163">**Privilege**</span></span><br><span data-ttu-id="78a37-164">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-164">Data type: String</span></span>|<span data-ttu-id="78a37-165">ユーザーは、右側のコマンドレットは、特定のエンティティの操作を実行する必要がありますを指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-165">Implement this parameter so that the user can specify the right a cmdlet needs to perform an operation for a particular entity.</span></span>|
|<span data-ttu-id="78a37-166">**権限**</span><span class="sxs-lookup"><span data-stu-id="78a37-166">**Privileges**</span></span><br><span data-ttu-id="78a37-167">データの種類:権限の配列</span><span class="sxs-lookup"><span data-stu-id="78a37-167">Data type: Array of privileges</span></span>|<span data-ttu-id="78a37-168">ユーザーが特定のエントリには、その操作を実行するコマンドレットが必要な権限を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-168">Implement this parameter so that the user can specify the rights that a cmdlet needs to perform its operation for a particular entry.</span></span>|
|<span data-ttu-id="78a37-169">**ロール**</span><span class="sxs-lookup"><span data-stu-id="78a37-169">**Role**</span></span><br><span data-ttu-id="78a37-170">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-170">Data type: String</span></span>|<span data-ttu-id="78a37-171">ユーザーは、一連のエンティティで実行できる操作を指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-171">Implement this parameter so that the user can specify a set of operations that can be performed by an entity.</span></span>|
|<span data-ttu-id="78a37-172">**SaveCred**</span><span class="sxs-lookup"><span data-stu-id="78a37-172">**SaveCred**</span></span><br><span data-ttu-id="78a37-173">データの種類:スイッチ パラメーター</span><span class="sxs-lookup"><span data-stu-id="78a37-173">Data type: SwitchParameter</span></span>|<span data-ttu-id="78a37-174">パラメーターを指定した場合、ユーザーが以前に保存された資格情報が使用できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-174">Implement this parameter so that credentials that were previously saved by the user will be used when the parameter is specified.</span></span>|
|<span data-ttu-id="78a37-175">**スコープ**</span><span class="sxs-lookup"><span data-stu-id="78a37-175">**Scope**</span></span><br><span data-ttu-id="78a37-176">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-176">Data type: String</span></span>|<span data-ttu-id="78a37-177">ユーザーが保護されているコマンドレットは、オブジェクトのグループを指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-177">Implement this parameter so that the user can specify the group of protected objects for the cmdlet.</span></span>|
|<span data-ttu-id="78a37-178">**SID**</span><span class="sxs-lookup"><span data-stu-id="78a37-178">**SID**</span></span><br><span data-ttu-id="78a37-179">データの種類:String</span><span class="sxs-lookup"><span data-stu-id="78a37-179">Data type: String</span></span>|<span data-ttu-id="78a37-180">このパラメーターを実装するは、ユーザーは、プリンシパルを表す一意の識別子を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="78a37-180">Implement this parameter so that the user can specify a unique identifier that represents a principal.</span></span>|
|<span data-ttu-id="78a37-181">**信頼されています。**</span><span class="sxs-lookup"><span data-stu-id="78a37-181">**Trusted**</span></span><br><span data-ttu-id="78a37-182">データの種類:スイッチ パラメーター</span><span class="sxs-lookup"><span data-stu-id="78a37-182">Data type: SwitchParameter</span></span>|<span data-ttu-id="78a37-183">このパラメーターを実装するは、パラメーターを指定した場合に、信頼レベルがサポートされているようにします。</span><span class="sxs-lookup"><span data-stu-id="78a37-183">Implement this parameter so that trust levels are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="78a37-184">**trustLevel**</span><span class="sxs-lookup"><span data-stu-id="78a37-184">**TrustLevel**</span></span><br><span data-ttu-id="78a37-185">データの種類:キーワード</span><span class="sxs-lookup"><span data-stu-id="78a37-185">Data type: Keyword</span></span>|<span data-ttu-id="78a37-186">ユーザーがサポートされている信頼レベルを指定できるように、このパラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="78a37-186">Implement this parameter so that the user can specify the trust level that is supported.</span></span> <span data-ttu-id="78a37-187">たとえば、使用可能な値には、インターネット、イントラネット、および fulltrust が含まれます。</span><span class="sxs-lookup"><span data-stu-id="78a37-187">For example, possible values include internet, intranet, and fulltrust.</span></span>|

## <a name="see-also"></a><span data-ttu-id="78a37-188">参照</span><span class="sxs-lookup"><span data-stu-id="78a37-188">See Also</span></span>

[<span data-ttu-id="78a37-189">コマンドレットのパラメーター</span><span class="sxs-lookup"><span data-stu-id="78a37-189">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="78a37-190">Windows PowerShell コマンドレットの記述</span><span class="sxs-lookup"><span data-stu-id="78a37-190">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="78a37-191">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="78a37-191">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)