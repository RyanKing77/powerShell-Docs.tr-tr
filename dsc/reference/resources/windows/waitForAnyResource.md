---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WaitForAny kaynak
ms.openlocfilehash: 39e90f0df3459b8891ed46e02ae82c45a285e7f5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048688"
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny kaynak

> Şunun için geçerlidir: Windows PowerShell 5.1 ve üzeri

**WaitForSome** Desired State Configuration ' nı (DSC) kaynak, bir düğüm bloğunda içinde kullanılabilir bir [DSC Yapılandırması](../../../configurations/configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.

Bu kaynak tarafından belirtilen kaynağı, başarılı **ResourceName** özelliği içinde tanımlanan tüm hedef düğümler üzerinde istenen durumda **NodeName** özelliği.


## <a name="syntax"></a>Sözdizimi

```
WaitForAny [string] #ResourceName
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
| ResourceName| Bağımlı kaynak adı. Bu kaynak farklı bir yapılandırmaya aitse, adı olarak Biçimlendir "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| NodeName| Hedef düğümleri kaynak bağlıdır.|
| RetryIntervalSec| Yeniden denemeden önce saniye sayısı. Minimum is 1.|
| retryCount| Yeniden deneme sayısı.|
| ThrottleLimit| Aynı anda bağlanmak makineleri sayısı. Yeni-cimsession varsayılan varsayılandır.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Bu kaynağı kullanmaya ilişkin bir örnek için bkz: [çapraz düğüm bağımlılıklarını belirtme](../../../configurations/crossNodeDependencies.md)
