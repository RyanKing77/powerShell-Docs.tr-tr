---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687366"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="06a62-102">Bir yapılandırmada aynı kaynağa izin verme</span><span class="sxs-lookup"><span data-stu-id="06a62-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="06a62-103">DSC izin ver veya yapılandırması içindeki çakışan kaynak tanımlarını işlemek desteklemez.</span><span class="sxs-lookup"><span data-stu-id="06a62-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="06a62-104">Çakışmayı çözmek çalışmak yerine, basitçe başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="06a62-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="06a62-105">Yapılandırma yeniden daha bileşik kaynaklarında kullanılan haline gelir gibi vb. çakışmaları daha sık meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="06a62-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="06a62-106">Çakışan kaynak tanımları aynı olduğunda, DSC Akıllı ve buna izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="06a62-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="06a62-107">Bu sürümle birlikte, aynı tanımlara sahip birden çok kaynak örneğini sahip destekliyoruz:</span><span class="sxs-lookup"><span data-stu-id="06a62-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="06a62-108">Önceki sürümlerde, sonuç WindowsFeature FE_IIS ve 'Web-Server' rolü emin olmak çalışırken WindowsFeature Worker_IIS örnekleri arasında bir çakışma nedeniyle başarısız bir derleme yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="06a62-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="06a62-109">Dikkat *tüm* bu iki yapılandırmada yapılandırılmış olan özellikleri aynıdır.</span><span class="sxs-lookup"><span data-stu-id="06a62-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="06a62-110">Bu yana *tüm* bu iki özellik kaynakların aynı olduğundan, bu artık başarılı bir derleme içinde neden olur.</span><span class="sxs-lookup"><span data-stu-id="06a62-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="06a62-111">Özelliklerinden herhangi birini iki kaynakları arasında farklıysa, bunlar aynı kabul edilmez ve derleme başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="06a62-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

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

<span data-ttu-id="06a62-112">WindowsFeature FE_IIS WindowsFeature Worker_IIS kaynakları artık aynıdır ve bu nedenle çakışma nedeniyle bu çok benzer yapılandırmanız başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="06a62-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
