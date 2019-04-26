---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058735"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Bir yapılandırmada aynı kaynağa izin verme

DSC izin ver veya yapılandırması içindeki çakışan kaynak tanımlarını işlemek desteklemez. Çakışmayı çözmek çalışmak yerine, basitçe başarısız olur. Yapılandırma yeniden daha bileşik kaynaklarında kullanılan haline gelir gibi vb. çakışmaları daha sık meydana gelir. Çakışan kaynak tanımları aynı olduğunda, DSC Akıllı ve buna izin gerekir. Bu sürümle birlikte, aynı tanımlara sahip birden çok kaynak örneğini sahip destekliyoruz:

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

Önceki sürümlerde, sonuç WindowsFeature FE_IIS ve 'Web-Server' rolü emin olmak çalışırken WindowsFeature Worker_IIS örnekleri arasında bir çakışma nedeniyle başarısız bir derleme yüklü olacaktır. Dikkat *tüm* bu iki yapılandırmada yapılandırılmış olan özellikleri aynıdır. Bu yana *tüm* bu iki özellik kaynakların aynı olduğundan, bu artık başarılı bir derleme içinde neden olur.

Özelliklerinden herhangi birini iki kaynakları arasında farklıysa, bunlar aynı kabul edilmez ve derleme başarısız olur:

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

WindowsFeature FE_IIS WindowsFeature Worker_IIS kaynakları artık aynıdır ve bu nedenle çakışma nedeniyle bu çok benzer yapılandırmanız başarısız olur.
