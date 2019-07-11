---
title: Varsayılan yöntemler için nesneleri tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733985"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="4b78b-102">Nesneler için Varsayılan Yöntemleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="4b78b-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="4b78b-103">.NET Framework nesneleri genişlettiğinizde, kod ve betik yöntemleri nesneleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b78b-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="4b78b-104">Bu yöntemleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4b78b-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="4b78b-105">Aşağıdaki bölümlerde Windows PowerShell yükleme dizininde Types.ps1xml türleri dosyasından örnekler (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="4b78b-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="4b78b-106">Kod yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4b78b-106">Code Methods</span></span>

<span data-ttu-id="4b78b-107">Bir kod yöntemi statik bir yöntem .NET Framework nesnesi başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="4b78b-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="4b78b-108">Aşağıdaki örnekte, **ConvertLargeIntegerToInt64** yöntemi eklenir [System.Xml.Xmlnode? Displayproperty Fullname =](/dotnet/api/System.Xml.XmlNode) türü.</span><span class="sxs-lookup"><span data-stu-id="4b78b-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="4b78b-109">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) öğesi, kod yöntemi olarak genişletilmiş yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b78b-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="4b78b-110">[Adı](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi genişletilmiş yöntemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b78b-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="4b78b-111">Ve [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) öğesi statik yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b78b-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="4b78b-112">(Ayrıca ekleyebilirsiniz [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) üyelerinin öğesine [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="4b78b-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="4b78b-113">Betik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4b78b-113">Script Methods</span></span>

<span data-ttu-id="4b78b-114">Bir betik yöntemi, bir komut dosyası çıktısını değeri olan bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b78b-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="4b78b-115">Aşağıdaki örnekte, **ConvertToDateTime** yöntemi eklenir [System.Management.Managementobject? Displayproperty Fullname =](/dotnet/api/System.Management.ManagementObject) türü.</span><span class="sxs-lookup"><span data-stu-id="4b78b-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="4b78b-116">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) öğe betik yöntemi olarak genişletilmiş yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b78b-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="4b78b-117">[Adı](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi genişletilmiş yöntemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b78b-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="4b78b-118">Ve [betik](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) öğesi yöntemi değer üreten betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b78b-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="4b78b-119">(Ayrıca ekleyebilirsiniz [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) üyelerinin öğesine [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="4b78b-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4b78b-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4b78b-120">See Also</span></span>

[<span data-ttu-id="4b78b-121">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="4b78b-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
