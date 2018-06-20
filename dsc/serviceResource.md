---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Hizmet kaynağı
ms.openlocfilehash: 3e2db8999ab1db2964f88e1ee14c6ad6e641c5e3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222443"
---
# <a name="dsc-service-resource"></a>DSC Hizmet kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0


**Hizmet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), hedef düğümde bulunan hizmetleri yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Ad| Hizmet adını gösterir. Bazen bu görünen adından farklı olduğunu unutmayın. Hizmetler ve bunların geçerli durumu Get-Service cmdlet ile listesini elde edebilirsiniz.|
| BuiltInAccount| Hizmet için oturum açma hesabı belirtir. Bu özellik için izin verilen değerler: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.|
| kimlik bilgisi| Hizmet, altında çalışacağı hesabın kimlik bilgilerini gösterir. Bu özellik ve __BuiltinAccount__ özelliği birlikte kullanılamaz.|
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| StartupType| Hizmet başlangıç türünü gösterir. Bu özellik için izin verilen değerler: **otomatik**, **devre dışı**, ve **el ile**|
| Durum| Hizmet için sağlamak istediğiniz durumu gösterir.|
| Açıklama | Hedef hizmet açıklaması gösterir.|
| Görünen Ad | Hedef hizmet görünen adını belirtir.|
| Emin olun | Hedef hizmet sistemde var olup olmadığını gösterir. Bu özelliği ayarlamak **etmeksizin** hedef hizmet yok emin olmak için. Ayar **mevcut** hedef hizmetinin var olduğunu (varsayılan değer) sağlar.|
| Yol | Yeni bir hizmet için ikili dosya yolunu gösterir.|

## <a name="example"></a>Örnek

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```