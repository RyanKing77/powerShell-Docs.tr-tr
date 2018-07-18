---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxService kaynağı
ms.openlocfilehash: ab6544762862c9b2477e92f0d782b13afb96f2c9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093577"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC için Linux nxService kaynağı

**NxService** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümdeki hizmetleri yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Özellikler
|  Özellik |  Açıklama |
|---|---|
| Ad| Yapılandırmak için hizmetin/daemon adı.|
| Denetleyici| Hizmeti yapılandırırken kullanılacak hizmet denetleyicisi türü.|
| Etkin| Hizmet önyükleme başlayıp başlamadığını gösterir.|
| Durum| Hizmetin çalışıp çalışmadığını gösterir. Bu özelliği hizmet çalışmadığından emin olmak için "Stopped" olarak ayarlayın. "Hizmet çalışmadığından emin olmak için çalışıyor" olarak ayarlayın.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Ek Bilgi

**NxService** kaynak değil oluşturur bir hizmet tanımı veya hizmet için betik yok. PowerShell Desired State Configuration kullanabileceğiniz **nxFile** varlığını veya Hizmet tanım dosyası veya komut dosyasının içeriğini yönetmek için kaynak kaynak.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kayıtlı (için Apache HTTP Server), 'httpd' hizmetinin yapılandırmasını gösterir. **SystemD** hizmet denetleyicisi.

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```