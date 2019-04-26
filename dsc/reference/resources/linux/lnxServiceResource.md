---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxService kaynağı
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077702"
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

| Özellik | Açıklama |
|---|---|
| Adı| Yapılandırmak için hizmetin/daemon adı.|
| Denetleyici| Hizmeti yapılandırırken kullanılacak hizmet denetleyicisi türü.|
| Etkin| Hizmet önyükleme başlayıp başlamadığını gösterir.|
| Durum| Hizmetin çalışıp çalışmadığını gösterir. Bu özelliği hizmet çalışmadığından emin olmak için "Stopped" olarak ayarlayın. "Hizmet çalışmadığından emin olmak için çalışıyor" olarak ayarlayın.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

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