---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC WaitForSome kaynağı
ms.openlocfilehash: 08a5b96bee0b1b4475470e0d857dca79dee2b02e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome kaynağı

> İçin geçerlidir: Windows PowerShell 5.0 ve sonraki sürümleri

**WaitForAny** istenen durum Yapılandırması'nı (DSC) kaynak, bir düğüm bloğu içinde kullanılabilir bir [DSC Yapılandırması](configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.

Kaynak tarafından belirtilmişse bu kaynak başarılı **ResourceName** özelliktir istenilen durumda düğüm sayısı alt sınırı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName**  özelliği.


## <a name="syntax"></a>Sözdizimi

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| NodeCount| Düğüm sayısı alt sınırı başarılı olması bu kaynak için istenen durumunda olması gerekir.|
| nodeName| Hedef düğümleri kaynağın bağlıdır.|
| resourceName| Bağımlı kaynak adı. Bu kaynak için farklı bir yapılandırma aitse, adı olarak biçim "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| RetryIntervalSec| Yeniden denemeden önce saniye sayısı. Minimum is 1.|
| retryCount| Yeniden deneneceğini maksimum sayısı.|
| ThrottleLimit| Makinelerin aynı anda bağlanmasına sayısı. Varsayılan yeni-cimsession varsayılandır.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](https://docs.microsoft.com/powershell/dsc/runasuser) |


## <a name="example"></a>Örnek

Bu kaynak kullanma örneği için bkz: [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md)