---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WaitForAll kaynağı"
ms.openlocfilehash: 2b6d9e11acd429eecb30926316d1033331524edc
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforall-resource"></a>DSC WaitForAll kaynağı

> İçin geçerlidir: Windows PowerShell 5.0 ve sonraki sürümleri

**WaitForAll** istenen durum Yapılandırması'nı (DSC) kaynak, bir düğüm bloğu içinde kullanılabilir bir [DSC Yapılandırması](configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.

Bu kaynak, başarılı kaynak tarafından belirtilmişse **ResourceName** özelliktir tanımlanan tüm hedef düğümleri üzerinde istenen durumda **NodeName** özelliği.


## <a name="syntax"></a>Sözdizimi

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   | 
|---|---| 
| resourceName| Bağımlı kaynak adı. Bu kaynak için farklı bir yapılandırma aitse, adı olarak biçim "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "| 
| nodeName| Hedef düğümleri kaynağın bağlıdır.| 
| RetryIntervalSec| Yeniden denemeden önce saniye sayısı. Minimum is 1.| 
| retryCount| Yeniden deneneceğini maksimum sayısı.| 
| ThrottleLimit| Makinelerin aynı anda bağlanmasına sayısı. Varsayılan yeni-cimsession varsayılandır.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Örnek

Bu kaynak kullanma örneği için bkz: [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md)

