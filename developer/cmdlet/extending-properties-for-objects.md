---
title: オブジェクトのプロパティの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986492"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="3f8b5-102">オブジェクトのプロパティを拡張する</span><span class="sxs-lookup"><span data-stu-id="3f8b5-102">Extending Properties for Objects</span></span>

<span data-ttu-id="3f8b5-103">.NET Framework オブジェクトを拡張すると、エイリアスプロパティ、コードプロパティ、メモプロパティ、スクリプトプロパティ、およびプロパティセットをオブジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="3f8b5-104">以下のセクションでは、これらのプロパティを定義する XML について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="3f8b5-105">次のセクションの例は、PowerShell インストールディレクトリ`Types.ps1xml` (`$PSHOME`) の既定の種類のファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="3f8b5-106">詳細については、「 [types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="3f8b5-107">エイリアスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3f8b5-107">Alias properties</span></span>

<span data-ttu-id="3f8b5-108">エイリアスプロパティは、既存のプロパティの新しい名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="3f8b5-109">次の例では、 **Count**プロパティが[system.string 型に](/dotnet/api/System.Array)追加されています。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="3f8b5-110">Alias[プロパティ](/dotnet/api/system.management.automation.psaliasproperty)要素は、拡張プロパティを別名プロパティとして定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="3f8b5-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)要素は、新しい名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="3f8b5-112">また、 [Referencedmembername](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername)要素は、エイリアスによって参照される既存のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="3f8b5-113">また`AliasProperty` [、要素](/dotnet/api/system.management.automation.psmemberset)をメンバーメンバーに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a><span data-ttu-id="3f8b5-114">コードのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3f8b5-114">Code properties</span></span>

<span data-ttu-id="3f8b5-115">コードプロパティは、.NET Framework オブジェクトの静的プロパティを参照します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="3f8b5-116">次の例では、 **Mode**プロパティが[DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)型に追加されています。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="3f8b5-117">[Codeproperty](/dotnet/api/system.management.automation.pscodeproperty)要素は、拡張プロパティをコードプロパティとして定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="3f8b5-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)要素は、拡張プロパティの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3f8b5-119">また、 [Getcodereference 参照](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference)要素は、拡張プロパティによって参照される静的メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="3f8b5-120">また`CodeProperty` [、要素](/dotnet/api/system.management.automation.psmemberset)をメンバーメンバーに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="3f8b5-121">メモのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3f8b5-121">Note properties</span></span>

<span data-ttu-id="3f8b5-122">Note プロパティは、静的な値を持つプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="3f8b5-123">次の例では、 **Status**プロパティの値が常に**Success**であるが、 [DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)型に追加されています。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="3f8b5-124">Note[プロパティ要素は、拡張](/dotnet/api/system.management.automation.psnoteproperty)プロパティを note プロパティとして定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="3f8b5-125">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)要素は、拡張プロパティの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3f8b5-126">[Value](/dotnet/api/system.management.automation.psnoteproperty.value)要素は、拡張プロパティの静的な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="3f8b5-127">要素`NoteProperty` [は、メンバー](/dotnet/api/system.management.automation.psmemberset)メンバーに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a><span data-ttu-id="3f8b5-128">スクリプトのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3f8b5-128">Script properties</span></span>

<span data-ttu-id="3f8b5-129">スクリプトプロパティは、スクリプトの出力を値として持つプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="3f8b5-130">次の例では、 **VersionInfo**プロパティ[が、system.string 型に](/dotnet/api/System.IO.FileInfo)追加されます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="3f8b5-131">[Scriptproperty](/dotnet/api/system.management.automation.psscriptproperty)要素は、拡張プロパティをスクリプトプロパティとして定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="3f8b5-132">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)要素は、拡張プロパティの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3f8b5-133">また、 [Getscriptblock](/dotnet/api/system.management.automation.psscriptproperty.getterscript)要素は、プロパティ値を生成するスクリプトを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="3f8b5-134">また`ScriptProperty` [、要素](/dotnet/api/system.management.automation.psmemberset)をメンバーメンバーに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a><span data-ttu-id="3f8b5-135">プロパティセット</span><span class="sxs-lookup"><span data-stu-id="3f8b5-135">Property sets</span></span>

<span data-ttu-id="3f8b5-136">プロパティセットは、セットの名前で参照できる拡張プロパティのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="3f8b5-137">たとえば、 [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**プロパティ**パラメーターでは、表示する特定のプロパティセットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="3f8b5-138">プロパティセットを指定すると、そのセットに属するプロパティだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="3f8b5-139">オブジェクトに対して定義できるプロパティセットの数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="3f8b5-140">ただし、オブジェクトの既定の表示プロパティを定義するために使用されるプロパティセットは、 **Psstandardmembers**メンバーセット内で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="3f8b5-141">型ファイルでは、既定のプロパティセット名に**defaultdisplayproperty**、 **DefaultDisplayPropertySet**、および DefaultKeyPropertySet が含まれます。 `Types.ps1xml`</span><span class="sxs-lookup"><span data-stu-id="3f8b5-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="3f8b5-142">**Psstandardmembers**メンバーセットに追加した追加のプロパティセットはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="3f8b5-143">次の例では、 **DefaultDisplayPropertySet**プロパティセットが[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)型の**psstandardmembers**メンバーセットに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="3f8b5-144">[PropertySet](/dotnet/api/system.management.automation.pspropertyset)要素は、プロパティのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="3f8b5-145">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)要素は、プロパティセットの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="3f8b5-146">また、 [Referencedproperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames)要素は、セットのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="3f8b5-147">`PropertySet`要素を[Type](/dotnet/api/system.management.automation.pstypename)要素のメンバーに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f8b5-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="3f8b5-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f8b5-148">See also</span></span>

[<span data-ttu-id="3f8b5-149">型について types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3f8b5-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="3f8b5-150">システムの管理</span><span class="sxs-lookup"><span data-stu-id="3f8b5-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="3f8b5-151">Windows PowerShell コマンドレットの記述</span><span class="sxs-lookup"><span data-stu-id="3f8b5-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
