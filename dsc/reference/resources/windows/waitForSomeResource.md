---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WaitForSome kaynak
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726776"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome kaynak

> Şunun için geçerlidir: Windows PowerShell 5.0 ve üzeri

**WaitForSome** Desired State Configuration ' nı (DSC) kaynak, bir düğüm bloğunda içinde kullanılabilir bir [DSC Yapılandırması](../../../configurations/configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.

Bu kaynak tarafından belirtilen kaynağı, başarılı **ResourceName** özelliktir istenen durumda düğüm sayısı alt sınırı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName**  özelliği.

> [!NOTE]
> **WaitForSome** kaynak diğer düğümlerinin durumunu denetlemek için Windows Uzaktan Yönetimi kullanır.
> WinRM bağlantı noktası ve güvenlik gereksinimleri hakkında daha fazla bilgi için bkz. [PowerShell uzaktan iletişim güvenlik konuları](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

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
| NodeCount| Başarılı olması bu kaynak için istenen durumda olması gereken düğüm sayısı alt sınırı.|
| nodeName| Hedef düğümleri kaynak bağlıdır.|
| resourceName| Bağımlı kaynak adı. Bu kaynak farklı bir yapılandırmaya aitse, adı olarak Biçimlendir "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| RetryIntervalSec| Yeniden denemeden önce saniye sayısı. Minimum is 1.|
| RetryCount| Yeniden deneme sayısı.|
| ThrottleLimit| Aynı anda bağlanmak makineleri sayısı. Yeni-cimsession varsayılan varsayılandır.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](https://docs.microsoft.com/powershell/dsc/runasuser) |

## <a name="example"></a>Örnek

Bu kaynağı kullanmaya ilişkin bir örnek için bkz: [çapraz düğüm bağımlılıklarını belirtme](../../../configurations/crossNodeDependencies.md)
