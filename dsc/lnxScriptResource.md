---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Linux nxScript kaynak için"
ms.openlocfilehash: c12fb3b405d84eedd13e4cbebf2b2bf0d7cfb4d3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="a8984-103">DSC Linux nxScript kaynak için</span><span class="sxs-lookup"><span data-stu-id="a8984-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="a8984-104">**NxScript** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümünde Linux komut dosyalarını çalıştırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8984-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8984-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8984-105">Syntax</span></span>

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="a8984-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a8984-106">Properties</span></span>

|  <span data-ttu-id="a8984-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="a8984-107">Property</span></span> |  <span data-ttu-id="a8984-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8984-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="a8984-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="a8984-109">GetScript</span></span>| <span data-ttu-id="a8984-110">Çağırdığınızda, çalıştırılan bir komut dosyası sağlar [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a8984-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="a8984-111">Komut dosyası # gibi bir shebang ile başlaması gerekir! / bin/bash.</span><span class="sxs-lookup"><span data-stu-id="a8984-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>| 
| <span data-ttu-id="a8984-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="a8984-112">SetScript</span></span>| <span data-ttu-id="a8984-113">Bir komut dosyası sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8984-113">Provides a script.</span></span> <span data-ttu-id="a8984-114">Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'ini **TestScript** ilk çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a8984-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="a8984-115">Varsa **TestScript** bloğu döndüren bir çıkış kodu 0 dışında **SetScript** bloğu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a8984-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="a8984-116">Varsa **TestScript** bir çıkış kodu 0 döndürür **SetScript** çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="a8984-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="a8984-117">Komut dosyası gibi bir shebang ile başlamalıdır `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="a8984-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>| 
| <span data-ttu-id="a8984-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="a8984-118">TestScript</span></span>| <span data-ttu-id="a8984-119">Bir komut dosyası sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8984-119">Provides a script.</span></span> <span data-ttu-id="a8984-120">Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i, bu komut dosyasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a8984-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="a8984-121">0 dışında bir çıkış kodu döndürürse, SetScript çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a8984-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="a8984-122">0, çıkış kodu döndürürse **SetScript** çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="a8984-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="a8984-123">**TestScript** çağırdığınızda, aynı zamanda çalıştırıyorsa [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a8984-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="a8984-124">Ancak, bu durumda, **SetScript** , hangi çıkış kodu öğesinden döndürülen olsun çalışmaz **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="a8984-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="a8984-125">**TestScript** geçerli istenen durum yapılandırması gerçek yapılandırmasıyla eşleşen ve bir çıkış kodu, diğer 0'dan, onu eşleşmiyorsa, 0 çıkış kodu döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8984-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="a8984-126">(Geçerli istenen durum yapılandırması, DSC kullanarak düğümde kamulaştırılmış son yapılandırmadır).</span><span class="sxs-lookup"><span data-stu-id="a8984-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="a8984-127">Komut dosyası 1#!/bin/bash.1 gibi bir shebang ile başlamalıdır</span><span class="sxs-lookup"><span data-stu-id="a8984-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>| 
| <span data-ttu-id="a8984-128">Kullanıcı</span><span class="sxs-lookup"><span data-stu-id="a8984-128">User</span></span>| <span data-ttu-id="a8984-129">Komut dosyası olarak çalıştırmak için kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="a8984-129">The user to run the script as.</span></span>| 
| <span data-ttu-id="a8984-130">Grup</span><span class="sxs-lookup"><span data-stu-id="a8984-130">Group</span></span>| <span data-ttu-id="a8984-131">Komut dosyası olarak çalıştırmak için Grup.</span><span class="sxs-lookup"><span data-stu-id="a8984-131">The group to run the script as.</span></span>| 
| <span data-ttu-id="a8984-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a8984-132">DependsOn</span></span> | <span data-ttu-id="a8984-133">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8984-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a8984-134">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a8984-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="a8984-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8984-135">Example</span></span>

<span data-ttu-id="a8984-136">Aşağıdaki örnek kullanımını gösteren **nxScript** ek yapılandırma yönetimi gerçekleştirmek için kaynak.</span><span class="sxs-lookup"><span data-stu-id="a8984-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
} 
}
```

