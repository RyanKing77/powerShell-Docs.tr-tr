---
title: Nesneler için özellikleri genişletme | Microsoft Docs
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
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986480"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="3e2d3-102">Nesnelerin Özelliklerini Genişletme</span><span class="sxs-lookup"><span data-stu-id="3e2d3-102">Extending Properties for Objects</span></span>

<span data-ttu-id="3e2d3-103">Nesneleri .NET Framework genişlettiğinizde, nesnelere diğer ad özellikleri, kod özellikleri, Note özellikleri, betik özellikleri ve özellik kümeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="3e2d3-104">Bu özellikleri tanımlayan XML aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="3e2d3-105">Aşağıdaki bölümlerdeki örnekler, PowerShell yükleme dizinindeki ( `Types.ps1xml` `$PSHOME`) varsayılan türler dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="3e2d3-106">Daha fazla bilgi için bkz [. Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="3e2d3-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="3e2d3-107">Diğer ad özellikleri</span><span class="sxs-lookup"><span data-stu-id="3e2d3-107">Alias properties</span></span>

<span data-ttu-id="3e2d3-108">Bir Alias özelliği, var olan bir özellik için yeni bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="3e2d3-109">Aşağıdaki örnekte, **Count** özelliği [System. Array](/dotnet/api/System.Array) türüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="3e2d3-110">[Alias özelliği](/dotnet/api/system.management.automation.psaliasproperty) öğesi genişletilmiş özelliği bir diğer ad özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="3e2d3-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi yeni adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="3e2d3-112">Ve [Referencedmembername](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) öğesi, diğer ad tarafından başvurulan var olan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="3e2d3-113">Ayrıca, `AliasProperty` öğesini [membersets](/dotnet/api/system.management.automation.psmemberset) öğesinin üyelerine de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="3e2d3-114">Kod özellikleri</span><span class="sxs-lookup"><span data-stu-id="3e2d3-114">Code properties</span></span>

<span data-ttu-id="3e2d3-115">Bir kod özelliği bir .NET Framework nesnesinin statik özelliğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="3e2d3-116">Aşağıdaki örnekte, **Mode** özelliği [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) türüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="3e2d3-117">[CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) öğesi, Genişletilmiş özelliği bir kod özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="3e2d3-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi, genişletilmiş özelliğin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3e2d3-119">Ve, [Getcobaşvuru](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) öğesi, genişletilmiş özellik tarafından başvurulan statik yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="3e2d3-120">Ayrıca, `CodeProperty` öğesini [membersets](/dotnet/api/system.management.automation.psmemberset) öğesinin üyelerine de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="3e2d3-121">Notun özellikleri</span><span class="sxs-lookup"><span data-stu-id="3e2d3-121">Note properties</span></span>

<span data-ttu-id="3e2d3-122">Note özelliği statik değere sahip bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="3e2d3-123">Aşağıdaki örnekte, değeri her zaman **başarılı**olan **Status** özelliği [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) türüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="3e2d3-124">[Noteproperty](/dotnet/api/system.management.automation.psnoteproperty) öğesi genişletilmiş özelliği Not özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="3e2d3-125">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi, genişletilmiş özelliğin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3e2d3-126">[Value](/dotnet/api/system.management.automation.psnoteproperty.value) öğesi, genişletilmiş özelliğin statik değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="3e2d3-127">Öğesi membersets öğesinin üyelerine de eklenebilir. [](/dotnet/api/system.management.automation.psmemberset) `NoteProperty`</span><span class="sxs-lookup"><span data-stu-id="3e2d3-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="3e2d3-128">Betik özellikleri</span><span class="sxs-lookup"><span data-stu-id="3e2d3-128">Script properties</span></span>

<span data-ttu-id="3e2d3-129">Betik özelliği, değeri bir betiğin çıkışı olan bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="3e2d3-130">Aşağıdaki örnekte, **VersionInfo** özelliği [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) türüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="3e2d3-131">[ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) öğesi, Genişletilmiş özelliği bir betik özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="3e2d3-132">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi, genişletilmiş özelliğin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3e2d3-133">Ve [Getscriptblock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) öğesi, özellik değerini üreten betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="3e2d3-134">Ayrıca, `ScriptProperty` öğesini [membersets](/dotnet/api/system.management.automation.psmemberset) öğesinin üyelerine de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="3e2d3-135">Özellik kümeleri</span><span class="sxs-lookup"><span data-stu-id="3e2d3-135">Property sets</span></span>

<span data-ttu-id="3e2d3-136">Bir özellik kümesi, küme adı tarafından başvurulabilen genişletilmiş özellikler grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="3e2d3-137">Örneğin, [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**özelliği** parametresi, görüntülenmek üzere belirli bir özellik kümesi belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="3e2d3-138">Bir özellik kümesi belirtildiğinde, yalnızca kümesine ait özellikler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="3e2d3-139">Bir nesne için tanımlanabilir özellik kümesi sayısında kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="3e2d3-140">Ancak, bir nesnenin varsayılan görüntüleme özelliklerini tanımlamak için kullanılan özellik kümelerinin **Psstandardmembers** üye kümesi içinde belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="3e2d3-141">Türler dosyasında, varsayılan özellik kümesi adları **defaultdisplayproperty**, **defaultdisplaypropertyset**ve **defaultkeypropertyset**' i içerir. `Types.ps1xml`</span><span class="sxs-lookup"><span data-stu-id="3e2d3-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="3e2d3-142">**Psstandardmembers** üye kümesine eklediğiniz herhangi bir ek özellik kümesi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="3e2d3-143">Aşağıdaki örnekte, **Defaultdisplaypropertyset** özelliği kümesi, [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) türünün **psstandardmembers** üye kümesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="3e2d3-144">[PropertySet](/dotnet/api/system.management.automation.pspropertyset) öğesi Özellik grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="3e2d3-145">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi özellik kümesi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="3e2d3-146">Ve [Referencedproperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) öğesi, küme özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="3e2d3-147">Ayrıca, `PropertySet` öğesini [Type](/dotnet/api/system.management.automation.pstypename) öğesinin üyelerine de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3e2d3-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-148">See also</span></span>

[<span data-ttu-id="3e2d3-149">Türler. ps1xml hakkında</span><span class="sxs-lookup"><span data-stu-id="3e2d3-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="3e2d3-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="3e2d3-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="3e2d3-151">Windows PowerShell cmdlet 'ı yazma</span><span class="sxs-lookup"><span data-stu-id="3e2d3-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
