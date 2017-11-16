---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: d3a625d05eaf4e7448b4abf90499f6a94e2f7718
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="384b2-102">Yapılandırmasında aynı yinelenen kaynaklar için izin verme</span><span class="sxs-lookup"><span data-stu-id="384b2-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="384b2-103">DSC vermek veya çakışan kaynak tanımları bir yapılandırma içinde işler.</span><span class="sxs-lookup"><span data-stu-id="384b2-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="384b2-104">Çakışmayı çözmek çalışırken yerine, yalnızca başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="384b2-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="384b2-105">Yapılandırma yeniden daha bileşik kaynaklara aracılığıyla kullanılan hale gibi vb. çakışmaları daha sık meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="384b2-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="384b2-106">Çakışan kaynak tanımları aynı olduğunda, DSC Akıllı ve bu, olanak gerekir.</span><span class="sxs-lookup"><span data-stu-id="384b2-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="384b2-107">Bu sürümle birlikte, aynı tanımlara sahip birden çok kaynak örneği sahip destekler:</span><span class="sxs-lookup"><span data-stu-id="384b2-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="384b2-108">Önceki sürümlerde, sonuç WindowsFeature FE_IIS ve 'Web sunucusu' rolü emin olmak çalışırken WindowsFeature Worker_IIS örnekleri arasında bir çakışma nedeniyle başarısız derleme yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="384b2-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="384b2-109">Dikkat *tüm* bu iki yapılandırmada yapılandırılan özelliklerini aynıdır.</span><span class="sxs-lookup"><span data-stu-id="384b2-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="384b2-110">Bu yana *tüm* bu iki özelliklerinin kaynakları aynıdır, bunu şimdi başarılı bir derlemede neden olur.</span><span class="sxs-lookup"><span data-stu-id="384b2-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span> 

<span data-ttu-id="384b2-111">Özelliklerinden herhangi birini iki kaynak arasında farklıysa, bunlar aynı kabul edilmez ve derleme başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="384b2-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="384b2-112">WindowsFeature FE_IIS WindowsFeature Worker_IIS kaynakları artık aynıdır ve bu nedenle çakışma nedeniyle bu çok benzer yapılandırma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="384b2-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>

