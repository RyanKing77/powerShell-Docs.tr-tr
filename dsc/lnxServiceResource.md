---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Linux nxService kaynak için"
ms.openlocfilehash: be9f1f090eacc38bcdb77e53020d559bab72c156
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC Linux nxService kaynak için

**NxService** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümü hizmetleri yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler
|  Özellik |  Açıklama | 
|---|---|
| Ad| Hizmeti/yapılandırmak için arka plan programı adı.| 
| Denetleyici| Hizmet yapılandırırken kullanmak için hizmet denetleyicisi türü.| 
| Etkin| Hizmet önyükleme başlayıp başlamadığını gösterir.| 
| Durum| Hizmetin çalışıp çalışmadığını gösterir. Bu özelliği hizmeti çalışmadığından emin olmak için "durduruldu" olarak ayarlayın. "Hizmet çalışmıyor emin olmak için çalışıyor" olarak ayarlayın.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.| 


## <a name="additional-information"></a>Ek Bilgi

**NxService** kaynak değil oluşturacak bir hizmet tanımı veya hizmet için komut dosyası henüz yoksa. PowerShell istenen durum yapılandırması kullanabilirsiniz **nxFile** varlığı ya da hizmet tanımı dosyası veya komut dosyası içeriğini yönetmek için kaynak kaynak.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kayıtlı yapılandırma (için Apache HTTP Server), "httpd" hizmetinin gösterir **SystemD** hizmet denetleyicisi.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

