---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Çapraz düğüm bağımlılıklarını belirtme
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734677"
---
# <a name="specifying-cross-node-dependencies"></a>Çapraz düğüm bağımlılıklarını belirtme

> Şunun için geçerlidir: Windows PowerShell 5.0

DSC özel kaynaklar sağlayan **WaitForAll**, **WaitForAny**, ve **WaitForSome** kullanılabilecek yapılandırmalarında diğer yapılandırmaları bağımlılıklarını belirtmek için düğümleri. Bu kaynakların davranış aşağıdaki gibidir:

- **WaitForAll**: Belirtilen kaynak tanımlanan tüm hedef düğümler üzerinde istenen durumda ise başarılı **NodeName** özelliği.
- **WaitForAny**: Belirtilen kaynak en az bir tanımlanmış hedef düğümler üzerinde istenen durumda ise başarılı **NodeName** özelliği.
- **WaitForSome**: Belirtir bir **NodeCount** özelliğine ek olarak bir **NodeName** özelliği. Kaynak düğüm sayısı alt sınırı üzerinde istenen durumda ise kaynak başarılı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName** özelliği.

## <a name="syntax"></a>Sözdizimi

**WaitForAll** ve **WaitForAny** aynı sözdizimini kaynakları paylaşır. Değiştirin \<ResourceType\> aşağıdaki örnekte ya da ile **WaitForAny** veya **WaitForAll**.
Gibi **DependsOn** anahtar sözcüğü, adı "[ResourceType] ResourceName" olarak biçimlendirmek gerekir. Kaynak için ayrı bir aitse [yapılandırma](configurations.md), dahil **ConfigurationName** biçimlendirilen dizesinde "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]". **NodeName** bilgisayar veya üzerinde geçerli kaynak beklemesi gereken düğümü.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

**WaitForSome** kaynak yukarıdaki örneğe benzer bir sözdizimi vardır, ancak ekler **NodeCount** anahtarı. **NodeCount** kaç düğümleri geçerli kaynak beklemesi belirtir.

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

Tüm **WaitForXXXX** aşağıdaki söz dizimini anahtarlarını paylaşın.

|Özellik|  Açıklama   |
|---------|---------------------|
| RetryIntervalSec| Yeniden denemeden önce saniye sayısı. Minimum is 1.|
| RetryCount| Yeniden deneme sayısı.|
| ThrottleLimit| Aynı anda bağlanmak makineleri sayısı. Varsayılan değer `New-CimSession` varsayılan.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Daha fazla bilgi için [DependsOn](resource-depends-on.md)|
| PsDscRunAsCredential | Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](./runAsUser.md) |

## <a name="using-waitforxxxx-resources"></a>WaitForXXXX kaynakları kullanma

Her **WaitForXXXX** belirtilen düğümde tamamlamak belirtilen kaynaklar için kaynak bekler.
Diğer kaynakları aynı yapılandırmayı, böylece *bağımlı* **WaitForXXXX** kaynak kullanarak **DependsOn** anahtarı.

Örneğin, aşağıdaki yapılandırmasında, hedef düğüm bekliyor **xADDomain** bitmesi için kaynak **MyDC** düğüm sayısı 30 ile yeniden deneme sayısı, 15 saniyelik aralıklarla önce Hedef düğüm, etki alanına katılmasını sağlayabilirsiniz.

Varsayılan olarak **WaitForXXX** kaynakları bir kez deneyin ve sonra başarısız. Gerekli olmamasına karşın, genellikle belirtmek istersiniz bir **RetryCount** ve **RetryIntervalSec**.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Yapılandırmayı derlemek, iki ".mof" dosya üretilir. Kullanarak hedef düğümler için her iki ".mof" dosyalara [Başlat-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i

> [!NOTE]
> **WaitForXXX** kaynakları diğer düğümlerinin durumunu denetlemek için Windows Uzaktan Yönetimi kullanın.
> WinRM bağlantı noktası ve güvenlik gereksinimleri hakkında daha fazla bilgi için bkz. [PowerShell uzaktan iletişim güvenlik konuları](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırmaları](configurations.md)
- [Kaynak bağımlılıkları kullanın](resource-depends-on.md)
- [DSC kaynakları](../resources/resources.md)
- [Yerel Configuration Manager'ı yapılandırma](../managing-nodes/metaConfig.md)
