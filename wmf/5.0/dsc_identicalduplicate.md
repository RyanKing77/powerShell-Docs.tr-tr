---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ba6a5c5ba8ff54a4f4d6ba07cf04124baf65ef
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Yapılandırmasında aynı yinelenen kaynaklar için izin verme

DSC vermek veya çakışan kaynak tanımları bir yapılandırma içinde işler. Çakışmayı çözmek çalışırken yerine, yalnızca başarısız olur. Yapılandırma yeniden daha bileşik kaynaklara aracılığıyla kullanılan hale gibi vb. çakışmaları daha sık meydana gelir. Çakışan kaynak tanımları aynı olduğunda, DSC Akıllı ve bu, olanak gerekir. Bu sürümle birlikte, aynı tanımlara sahip birden çok kaynak örneği sahip destekler:

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

Önceki sürümlerde, sonuç WindowsFeature FE_IIS ve 'Web sunucusu' rolü emin olmak çalışırken WindowsFeature Worker_IIS örnekleri arasında bir çakışma nedeniyle başarısız derleme yüklü olacaktır. Dikkat *tüm* bu iki yapılandırmada yapılandırılan özelliklerini aynıdır. Bu yana *tüm* bu iki özelliklerinin kaynakları aynıdır, bunu şimdi başarılı bir derlemede neden olur.

Özelliklerinden herhangi birini iki kaynak arasında farklıysa, bunlar aynı kabul edilmez ve derleme başarısız olur:

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

WindowsFeature FE_IIS WindowsFeature Worker_IIS kaynakları artık aynıdır ve bu nedenle çakışma nedeniyle bu çok benzer yapılandırma başarısız olur.