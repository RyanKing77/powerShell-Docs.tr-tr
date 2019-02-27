---
title: Özellikleri genişletme nesneleri için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845783"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="6388f-102">Nesnelerin Özelliklerini Genişletme</span><span class="sxs-lookup"><span data-stu-id="6388f-102">Extending Properties for Objects</span></span>

<span data-ttu-id="6388f-103">.NET Framework nesneleri genişlettiğinizde, nesnelere özellikler, kod özellikleri, Not özellikleri, betik özellikleri ve özellik kümeleri diğer adı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6388f-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="6388f-104">Bu özellikleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6388f-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="6388f-105">Aşağıdaki bölümlerde Windows PowerShell yükleme dizinindeki varsayılan Types.ps1xml türleri dosyasından örnekler (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="6388f-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="6388f-106">Diğer özellikler</span><span class="sxs-lookup"><span data-stu-id="6388f-106">Alias Properties</span></span>

<span data-ttu-id="6388f-107">Varolan bir özellik için yeni bir ad bir diğer ad özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="6388f-108">Aşağıdaki örnekte, `Count` özelliği eklenir [System.Array? Displayproperty Fullname =](/dotnet/api/System.Array) türü.</span><span class="sxs-lookup"><span data-stu-id="6388f-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="6388f-109">[AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) öğe genişletilmiş özellik bir diğer ad özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="6388f-110">[Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi yeni adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="6388f-111">Ve [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) öğesi diğer adının başvurduğu var olan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="6388f-112">(Ayrıca ekleyebilirsiniz [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="6388f-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="6388f-113">Kod özellikleri</span><span class="sxs-lookup"><span data-stu-id="6388f-113">Code Properties</span></span>

<span data-ttu-id="6388f-114">Kod bir özelliği, bir statik özellik bir .NET Framework nesnesi başvurur.</span><span class="sxs-lookup"><span data-stu-id="6388f-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="6388f-115">Aşağıdaki örnekte, `Node` özelliği eklenir [System.IO.Directoryinfo? Displayproperty Fullname =](/dotnet/api/System.IO.DirectoryInfo) türü.</span><span class="sxs-lookup"><span data-stu-id="6388f-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="6388f-116">[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) öğe genişletilmiş özellik kod özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="6388f-117">[Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi, genişletilmiş özelliğin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="6388f-118">Ve [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) öğe genişletilmiş özelliği tarafından başvurulan statik yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="6388f-119">(Ayrıca ekleyebilirsiniz [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="6388f-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="6388f-120">Not özellikleri</span><span class="sxs-lookup"><span data-stu-id="6388f-120">Note Properties</span></span>

<span data-ttu-id="6388f-121">Bir not özelliğini statik bir değere sahip bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="6388f-122">Aşağıdaki örnekte, `Status` (değeri olan her zaman "Başarılı") özelliği eklenir [System.IO.Directoryinfo? Displayproperty Fullname =](/dotnet/api/System.IO.DirectoryInfo) türü.</span><span class="sxs-lookup"><span data-stu-id="6388f-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="6388f-123">[NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) öğe tanımlar genişletilmiş özellik Not özelliği olarak; [adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi genişletilmiş özelliğinin adını belirtir ve [değer](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) öğesi Genişletilmiş özellik statik değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="6388f-124">( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) öğesi üyelerine de eklenebilir [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="6388f-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="6388f-125">Komut dosyası özellikleri</span><span class="sxs-lookup"><span data-stu-id="6388f-125">Script Properties</span></span>

<span data-ttu-id="6388f-126">Bir komut dosyası özellik değeri olan bir komut dosyası çıktısını bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="6388f-127">Aşağıdaki örnekte, `VersionInfo` özelliği eklenir [System.IO.FileInfo? Displayproperty Fullname =](/dotnet/api/System.IO.FileInfo) türü.</span><span class="sxs-lookup"><span data-stu-id="6388f-127">In the following example, the `VersionInfo` property is added to the [System.IO.Fileinfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="6388f-128">[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) öğe genişletilmiş özellik bir betik özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="6388f-129">[Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi, genişletilmiş özelliğin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="6388f-130">Ve [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) öğesi özellik değerini üreten betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="6388f-131">(Ayrıca ekleyebilirsiniz [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="6388f-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="6388f-132">Özellik kümeleri</span><span class="sxs-lookup"><span data-stu-id="6388f-132">Property Sets</span></span>

<span data-ttu-id="6388f-133">Bir özellik kümesi, bir küme adı tarafından başvurulan genişletilmiş özellikler grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="6388f-134">Örneğin, `Property` parametresinin [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet'i, belirli bir özellik görüntülenecek kümesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6388f-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="6388f-135">Bir özellik kümesi belirtildiğinde, kümeye ait özellikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6388f-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>
<span data-ttu-id="6388f-136">Bir özellik kümesi, bir küme adı tarafından başvurulan genişletilmiş özellikler grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="6388f-137">Örneğin, `Property` parametresinin [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet'i, belirli bir özellik görüntülenecek kümesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6388f-137">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="6388f-138">Bir özellik kümesi belirtildiğinde, kümeye ait özellikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6388f-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="6388f-139">Bir nesne için tanımlanmış bir özellik kümeleri sayısına bir sınırlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="6388f-139">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="6388f-140">Ancak, bir nesnenin varsayılan görüntü özelliklerini tanımlamak için kullanılan özellik kümeleri PSStandardMembers üye kümesi içinde belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6388f-140">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="6388f-141">Types.ps1xml türleri dosyasında DefaultDisplayProperty DefaultDisplayPropertySet ve DefaultKeyPropertySet varsayılan özellik kümesinin adlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6388f-141">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="6388f-142">PSStandardMembers üye kümesine eklediğiniz herhangi bir ek özellik kümeleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="6388f-142">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="6388f-143">Aşağıdaki örnekte, DefaultDisplayPropertySet özellik kümesi PSStandardMembers üye kümesine eklenen [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) türü.</span><span class="sxs-lookup"><span data-stu-id="6388f-143">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="6388f-144">[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) öğe özellikler grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6388f-144">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="6388f-145">[Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi özellik kümesinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-145">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="6388f-146">Ve [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) öğesi kümesi özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6388f-146">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="6388f-147">(Ayrıca ekleyebilirsiniz [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) üyelerinin öğesine [türü](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="6388f-147">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6388f-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6388f-148">See Also</span></span>

[<span data-ttu-id="6388f-149">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="6388f-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
