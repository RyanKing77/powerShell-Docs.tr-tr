---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC ServiceSet kaynağı
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076846"
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet kaynağı

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

**ServiceSet** kaynak olarak Windows PowerShell Desired State Configuration (DSC), hedef düğümdeki hizmetleri yönetmek için bir mekanizma sağlar. Bu kaynak bir [bileşik kaynak](../../../resources/authoringResourceComposite.md) çağrılarının [hizmet kaynak](serviceResource.md) belirtilen her hizmet için `Name` özelliği.

Bu kaynak, bir dizi hizmet için aynı duruma yapılandırmak istediğinizde kullanın.

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
| Adı| Hizmet adlarını gösterir. Bazen bu görünen adları farklı olduğunu unutmayın. Hizmetler ve bunların geçerli durumunu içeren bir listesini alabilirsiniz [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet'i.|
| Başlangıç türü| Hizmet başlangıç türünü gösterir. Bu özellik için izin verilen değerler şunlardır: **Otomatik**, **devre dışı bırakılmış**, ve **el ile**|
| BuiltInAccount| Hizmetleri kullanmak için oturum açma hesabını belirtir. Bu özellik için izin verilen değerler şunlardır: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.|
| Durum| Hizmetler için sağlamak istediğiniz durumunu gösterir: **Durduruldu** veya **çalıştıran**.|
| Emin olun| Hizmetleri sisteminde mevcut olup olmadığını gösterir. Bu özellik kümesine **devamsızlık** Hizmetleri mevcut emin olmak için. Bu ayarın **mevcut** (varsayılan değer) hedef Hizmetleri mevcut olmasını sağlar.|
| Kimlik bilgisi| Hizmet kaynağı altında çalışacağı hesabın kimlik bilgilerini belirtir. Bu özellik ve **BuiltinAccount** özelliği birlikte kullanılamaz.|
| dependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise *ResourceName* ve kendi türünün *ResourceType*, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Örnek

Aşağıdaki yapılandırma, "Windows Ses" ve "Uzak Masaüstü Hizmetleri" Hizmetleri başlatılır.

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
