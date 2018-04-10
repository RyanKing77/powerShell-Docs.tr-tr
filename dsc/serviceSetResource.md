---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC ServiceSet kaynağı
ms.openlocfilehash: a7516120f0c4bc1c91031adc8aabf6a59b845246
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0


**ServiceSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), hedef düğümde bulunan hizmetleri yönetmek için bir mekanizma sağlar. Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [hizmet kaynak](serviceResource.md) belirtilen her hizmet için `Name` özelliği.

Bu kaynak Hizmetleri aynı duruma sayısını yapılandırmak istediğinizde kullanın.

## <a name="syntax"></a>Sözdizimi

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Ad| Hizmet adlarını gösterir. Bazen bu görünen adları farklı olduğuna dikkat edin. Hizmetleri ve bunların geçerli durumu ile bir liste alabilir [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet'i.|
| StartupType| Hizmet başlangıç türünü gösterir. Bu özellik için izin verilen değerler: **otomatik**, **devre dışı**, ve **el ile**|
| BuiltInAccount| Hizmetler için kullanılacak oturum açma hesabını belirtir. Bu özellik için izin verilen değerler: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.|
| Durum| Hizmetler için sağlamak istediğiniz durumunu gösterir: **durduruldu** veya **çalıştıran**.|
| Emin olun| Hizmetleri sistemde var olup olmadığını gösterir. Bu özelliği ayarlamak **etmeksizin** Hizmetleri mevcut emin olmak için. Ayar **mevcut** hedef Hizmetleri mevcut olduğunu (varsayılan değer) sağlar.|
| kimlik bilgisi| Hizmet kaynağı altında çalışacağı hesabın kimlik bilgilerini gösterir. Bu özellik ve **BuiltinAccount** özelliği birlikte kullanılamaz.|
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise *ResourceName* ve türünü *ResourceType*, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Örnek

Aşağıdaki yapılandırma "Windows Ses" ve "Uzak Masaüstü Hizmetleri" hizmetlerini başlatır.

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```