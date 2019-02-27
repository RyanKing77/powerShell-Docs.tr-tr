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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850599"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="4bf96-102">Nesneler için Varsayılan Yöntemleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="4bf96-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="4bf96-103">.NET Framework nesneleri genişlettiğinizde, kod ve betik yöntemleri nesneleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bf96-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="4bf96-104">Bu yöntemleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4bf96-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="4bf96-105">Aşağıdaki bölümlerde Windows PowerShell yükleme dizininde Types.ps1xml türleri dosyasından örnekler (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="4bf96-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="4bf96-106">Kod yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4bf96-106">Code Methods</span></span>

<span data-ttu-id="4bf96-107">Bir kod yöntemi statik bir yöntem .NET Framework nesnesi başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="4bf96-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="4bf96-108">Aşağıdaki örnekte, **ConvertLargeIntegerToInt64** yöntemi eklenir [System.Xml.Xmlnode? Displayproperty Fullname =](/dotnet/api/System.Xml.XmlNode) türü.</span><span class="sxs-lookup"><span data-stu-id="4bf96-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="4bf96-109">[CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) öğesi, kod yöntemi olarak genişletilmiş yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4bf96-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="4bf96-110">[Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi genişletilmiş yöntemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bf96-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="4bf96-111">Ve [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) öğesi statik yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bf96-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="4bf96-112">(Ayrıca ekleyebilirsiniz [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="4bf96-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="4bf96-113">Betik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4bf96-113">Script Methods</span></span>

<span data-ttu-id="4bf96-114">Bir betik yöntemi, bir komut dosyası çıktısını değeri olan bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4bf96-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="4bf96-115">Aşağıdaki örnekte, **ConvertToDateTime** yöntemi eklenir [System.Management.Managementobject? Displayproperty Fullname =](/dotnet/api/System.Management.ManagementObject) türü.</span><span class="sxs-lookup"><span data-stu-id="4bf96-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="4bf96-116">[ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) öğe betik yöntemi olarak genişletilmiş yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4bf96-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="4bf96-117">[Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi genişletilmiş yöntemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bf96-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="4bf96-118">Ve [betik](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) öğesi yöntemi değer üreten betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bf96-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="4bf96-119">(Ayrıca ekleyebilirsiniz [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)</span><span class="sxs-lookup"><span data-stu-id="4bf96-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4bf96-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4bf96-120">See Also</span></span>

[<span data-ttu-id="4bf96-121">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="4bf96-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)