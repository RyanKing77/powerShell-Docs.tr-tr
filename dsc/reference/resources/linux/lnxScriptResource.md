---
ms.date: 06/12/2017
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Linux nxScript kaynağı için DSC
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372156"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="81c44-103">Linux nxScript kaynağı için DSC</span><span class="sxs-lookup"><span data-stu-id="81c44-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="81c44-104">PowerShell Istenen durum yapılandırması (DSC) içindeki **Nxscript** kaynağı bir Linux düğümünde Linux betikleri çalıştırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="81c44-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="81c44-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81c44-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="81c44-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="81c44-106">Properties</span></span>

|  <span data-ttu-id="81c44-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="81c44-107">Property</span></span> |  <span data-ttu-id="81c44-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81c44-108">Description</span></span> |
|---|---|
| <span data-ttu-id="81c44-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="81c44-109">GetScript</span></span>| <span data-ttu-id="81c44-110">Makinenin geçerli durumunu döndürmek için bir betik sağlar.</span><span class="sxs-lookup"><span data-stu-id="81c44-110">Provides a script to return current status of the machine.</span></span>  <span data-ttu-id="81c44-111">Bu betik, [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda çalışır.</span><span class="sxs-lookup"><span data-stu-id="81c44-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="81c44-112">Betiğin #!/bin/Bash. gibi bir shebang ile başlaması gerekir</span><span class="sxs-lookup"><span data-stu-id="81c44-112">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="81c44-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="81c44-113">SetScript</span></span>| <span data-ttu-id="81c44-114">Makineyi doğru duruma koyan bir betik sağlar.</span><span class="sxs-lookup"><span data-stu-id="81c44-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="81c44-115">[StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda **TestScript** önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="81c44-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="81c44-116">**TestScript** bloğu 0 dışında bir çıkış kodu döndürürse, **setscript** bloğu çalışır.</span><span class="sxs-lookup"><span data-stu-id="81c44-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="81c44-117">**Testscrıpt** 0 çıkış kodu döndürürse, **setscript** çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="81c44-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="81c44-118">Betiğin gibi bir shebang `#!/bin/bash`ile başlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="81c44-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="81c44-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="81c44-119">TestScript</span></span>| <span data-ttu-id="81c44-120">Düğümün Şu anda doğru durumda olup olmadığını değerlendiren bir betik sağlar.</span><span class="sxs-lookup"><span data-stu-id="81c44-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="81c44-121">[StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda, bu betik çalışır.</span><span class="sxs-lookup"><span data-stu-id="81c44-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="81c44-122">0 dışında bir çıkış kodu döndürürse, SetScript çalışır.</span><span class="sxs-lookup"><span data-stu-id="81c44-122">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="81c44-123">0 çıkış kodu döndürürse, **Setscript** çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="81c44-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="81c44-124">**TestScript** , [testdscconfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda de çalışır.</span><span class="sxs-lookup"><span data-stu-id="81c44-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="81c44-125">Ancak, bu durumda, **TestScript**'ten çıkış kodu Döndürülmeksizin, **setscript** çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="81c44-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="81c44-126">**Test betiği** içerik içermeli ve gerçek yapılandırma geçerli durum yapılandırmasıyla eşleşiyorsa 0 çıkış kodu ve eşleşmezse 0 dışında bir çıkış kodu döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="81c44-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="81c44-127">(Geçerli istenen durum yapılandırması, DSC kullanan düğümde kullanılan son yapılandırmadır).</span><span class="sxs-lookup"><span data-stu-id="81c44-127">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="81c44-128">Betiğin, 1 #!/bin/Bash.1 gibi bir shebang ile başlaması gerekir</span><span class="sxs-lookup"><span data-stu-id="81c44-128">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="81c44-129">Kullanıcı</span><span class="sxs-lookup"><span data-stu-id="81c44-129">User</span></span>| <span data-ttu-id="81c44-130">Betiği çalıştıran kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="81c44-130">The user to run the script as.</span></span>|
| <span data-ttu-id="81c44-131">Grup</span><span class="sxs-lookup"><span data-stu-id="81c44-131">Group</span></span>| <span data-ttu-id="81c44-132">Betiği çalıştırmak için Grup.</span><span class="sxs-lookup"><span data-stu-id="81c44-132">The group to run the script as.</span></span>|
| <span data-ttu-id="81c44-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="81c44-133">DependsOn</span></span> | <span data-ttu-id="81c44-134">Bu kaynak yapılandırıldıktan önce başka bir kaynağın yapılandırmasının çalıştırılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="81c44-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="81c44-135">Örneğin, önce çalıştırmak istediğiniz kaynak yapılandırma betiği bloğunun **kimliği** **resourceName** ise ve türü **ResourceType**ise, bu özelliği kullanmak için sözdizimi olur `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="81c44-135">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="81c44-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="81c44-136">Example</span></span>

<span data-ttu-id="81c44-137">Aşağıdaki örnek, ek yapılandırma yönetimi gerçekleştirmek için **Nxscript** kaynağının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="81c44-137">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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
