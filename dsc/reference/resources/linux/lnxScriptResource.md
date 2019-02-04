---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynak Linux nxScript için
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55689046"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="33328-103">DSC kaynak Linux nxScript için</span><span class="sxs-lookup"><span data-stu-id="33328-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="33328-104">**NxScript** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde Linux betiklerini çalıştırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="33328-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="33328-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33328-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="33328-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="33328-106">Properties</span></span>

|  <span data-ttu-id="33328-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="33328-107">Property</span></span> |  <span data-ttu-id="33328-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33328-108">Description</span></span> |
|---|---|
| <span data-ttu-id="33328-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="33328-109">GetScript</span></span>| <span data-ttu-id="33328-110">Çağırdığınızda, çalışan bir komut dosyası sağlar [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="33328-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="33328-111">Betik # gibi bir shebang'i başlamalıdır! / bin/bash.</span><span class="sxs-lookup"><span data-stu-id="33328-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="33328-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="33328-112">SetScript</span></span>| <span data-ttu-id="33328-113">Bir komut dosyası sağlar.</span><span class="sxs-lookup"><span data-stu-id="33328-113">Provides a script.</span></span> <span data-ttu-id="33328-114">Çağırdığınızda [Başlat-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'ini **TestScript** ilk çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="33328-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="33328-115">Varsa **TestScript** bloğu döndüren bir çıkış kodu 0 dışındaki **SetScript** bloğu çalışır.</span><span class="sxs-lookup"><span data-stu-id="33328-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="33328-116">Varsa **TestScript** 0 çıkış kodu döndürür **SetScript** çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="33328-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="33328-117">Betik gibi bir shebang'i ile başlamalıdır `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="33328-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="33328-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="33328-118">TestScript</span></span>| <span data-ttu-id="33328-119">Bir komut dosyası sağlar.</span><span class="sxs-lookup"><span data-stu-id="33328-119">Provides a script.</span></span> <span data-ttu-id="33328-120">Çağırdığınızda [Başlat-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i, bu betiği çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="33328-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="33328-121">0 dışında bir çıkış kodu döndürürse, SetScript çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="33328-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="33328-122">0 çıkış kodu döndürürse **SetScript** çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="33328-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="33328-123">**TestScript** çağırdığınızda, aynı zamanda çalıştırıyorsa [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="33328-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="33328-124">Ancak, bu durumda, **SetScript** , hangi çıkış kodu öğesinden döndürülen ne olursa olsun çalışmaz **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="33328-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="33328-125">**TestScript** gerçek yapılandırmasını geçerli istenen durum yapılandırması ile eşleşen ve bir çıkış kodu, diğer 0'dan, eşleşmiyorsa, 0 çıkış kodu döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="33328-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="33328-126">(Geçerli istenen durum yapılandırması, DSC kullanarak bir düğümde yapılandırmalara uygun koşullarda çalışıldığından son yapılandırmadır).</span><span class="sxs-lookup"><span data-stu-id="33328-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="33328-127">Betik 1#!/bin/bash.1 gibi bir shebang'i ile başlamalıdır</span><span class="sxs-lookup"><span data-stu-id="33328-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="33328-128">Kullanıcı</span><span class="sxs-lookup"><span data-stu-id="33328-128">User</span></span>| <span data-ttu-id="33328-129">Betik olarak çalıştırmak için kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="33328-129">The user to run the script as.</span></span>|
| <span data-ttu-id="33328-130">Grup</span><span class="sxs-lookup"><span data-stu-id="33328-130">Group</span></span>| <span data-ttu-id="33328-131">Betik olarak çalıştırmak için Grup.</span><span class="sxs-lookup"><span data-stu-id="33328-131">The group to run the script as.</span></span>|
| <span data-ttu-id="33328-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="33328-132">DependsOn</span></span> | <span data-ttu-id="33328-133">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="33328-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="33328-134">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="33328-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="33328-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="33328-135">Example</span></span>

<span data-ttu-id="33328-136">Aşağıdaki örnek, kullanımını gösterir **nxScript** ek yapılandırma yönetimi gerçekleştirmek için kaynak.</span><span class="sxs-lookup"><span data-stu-id="33328-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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