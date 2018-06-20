---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxFileLine kaynak için
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219642"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC Linux nxFileLine kaynak için

**NxFileLine** kaynak olarak PowerShell istenen durum yapılandırması (DSC) yapılandırma dosyasında bir Linux düğümünde satırları yönetmek üzere bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| filePath| Hedef düğümde bulunan satırları yönetmek için dosyanın tam yolu.|
| ContainsLine| Dosyada emin olmak için bir satır var. Dosya yoksa, bu satırın dosyasına eklenir. **ContainsLine** zorunludur, ancak boş bir dize olarak ayarlanabilir ('ContainsLine = ''') değil gerekiyorsa.|
| DoesNotContainPattern| Normal ifade deseni dosyasında bulunmamalıdır satırlar için. Bu normal bir ifadeyle eşleşen dosyasında bulunan tüm satırlar için dosyadan satır kaldırılır.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Bu örnek kullanılmasını gösterir **nxFileLine** yapılandırmak için kaynak `/etc/sudoers` dosyası, kullanıcı sağlanarak: monuser değil requiretty için yapılandırılmış.

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```