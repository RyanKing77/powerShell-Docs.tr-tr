---
title: Nesneler için varsayılan yöntemleri tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215279"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="7ef7e-102">Nesneler için Varsayılan Yöntemleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="7ef7e-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="7ef7e-103">Nesneleri .NET Framework genişlettiğinizde, nesnelere kod yöntemleri ve betik yöntemleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="7ef7e-104">Bu yöntemleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="7ef7e-105">Aşağıdaki bölümlerdeki `Types.ps1xml` örnekler, Windows PowerShell yükleme dizinindeki (`$PSHOME`) türler dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="7ef7e-106">Daha fazla bilgi için bkz [. Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="7ef7e-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="7ef7e-107">Kod yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7ef7e-107">Code methods</span></span>

<span data-ttu-id="7ef7e-108">Kod yöntemi bir .NET Framework nesnesinin statik yöntemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="7ef7e-109">Aşağıdaki örnekte, **ToString** yöntemi [System. xml. XMLNode](/dotnet/api/System.Xml.XmlNode) türüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="7ef7e-110">[Pscodemethod](/dotnet/api/system.management.automation.pscodemethod) öğesi, genişletilmiş yöntemi bir kod yöntemi olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="7ef7e-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi, genişletilmiş yöntemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="7ef7e-112">[Cobaşvuru](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) öğesi de statik yöntemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="7ef7e-113">[Pscodemethod](/dotnet/api/system.management.automation.pscodemethod) öğesini de [psmembersets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesinin üyelerine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="7ef7e-114">Betik metotları</span><span class="sxs-lookup"><span data-stu-id="7ef7e-114">Script methods</span></span>

<span data-ttu-id="7ef7e-115">Betik yöntemi, bir betiğin çıkışı olan bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="7ef7e-116">Aşağıdaki örnekte, **Converttodatetime** yöntemi [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) türüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="7ef7e-117">[Psscriptmethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) öğesi, genişletilmiş yöntemi bir betik yöntemi olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="7ef7e-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi, genişletilmiş yöntemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="7ef7e-119">Ve [komut dosyası](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) öğesi, yöntem değerini üreten betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="7ef7e-120">[Psscriptmethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) öğesini de [psmembersets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesinin üyelerine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="7ef7e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ef7e-121">See also</span></span>

[<span data-ttu-id="7ef7e-122">Windows PowerShell cmdlet 'ı yazma</span><span class="sxs-lookup"><span data-stu-id="7ef7e-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
