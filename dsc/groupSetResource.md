---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
description: Hedef düğüm üzerindeki yerel grupların yönetmek için bir mekanizma sağlar.
title: DSC GroupSet kaynağı
ms.openlocfilehash: 487a76ca7703b2c57b940b4c5bd176eada6c8019
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892435"
---
# <a name="dsc-groupset-resource"></a>DSC GroupSet kaynağı

> Uygulama hedefi: Windows Windows PowerShell 5.0

**GroupSet** kaynak olarak Windows PowerShell Desired State Configuration (DSC) hedef düğümde yerel grupları yönetmek için bir mekanizma sağlar. Bu kaynak bir [bileşik kaynak](authoringResourceComposite.md) çağrılarının [kaynak grubunda](groupResource.md) belirtilen her grup için `GroupName` parametresi.

Bu kaynak, ekleme ve/veya aynı birden fazla gruba üye listesini Kaldır, birden fazla grubunu kaldırın veya aynı listesiyle birden fazla Grup üyeleri eklemek istediğinizde kullanın.

## <a name="syntax"></a>Sözdizimi

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| GroupName| Belirli bir durumu sağlamak istediğiniz grupların adları.|
| MembersToExclude| Gruplar mevcut üyelikten üyeleri kaldırmak için bu özelliği kullanın. Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*. Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği. Bunun yapılması, bir hata oluşturur.|
| Kimlik bilgisi| Uzak kaynaklara erişmek için gerekli kimlik bilgileri. **Not**: Bu hesabın tüm yerel olmayan hesapları grubuna eklemek için uygun Active Directory izinlerinin olması gerekir; aksi takdirde bir hata meydana gelir.
| Emin olun| Gruplar mevcut olup olmadığını gösterir. "Yok" grubu mevcut sağlamak için bu özelliği ayarlayın. "(Varsayılan değer) sunmak için" ayar grupları mevcut olmasını sağlar.|
| Üyeler| Belirtilen üye ile geçerli grup üyeliğini değiştirmek için bu özelliği kullanın. Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*. Bir yapılandırmada bu özelliği ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği. Bunun yapılması, bir hata oluşturur.|
| MembersToInclude| Mevcut üyelik grubunun üyeleri eklemek için bu özelliği kullanın. Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*. Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği. Bunun yapılması, bir hata oluşturur.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.|

## <a name="example-1-ensuring-groups-are-present"></a>Örnek 1: Kalmasını sağlama grup yok

Aşağıdaki örnek, "myGroup" ve "myOtherGroup" adlı iki grup mevcut olduğundan emin olun gösterilmektedir.

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE] 
> Bu örnekte, kolaylık olması için düz metin kimlik bilgileri kullanır. Yapılandırma MOF dosyasının kimlik bilgilerini şifreleme hakkında daha fazla bilgi için bkz: [MOF dosyasının güvenliğini sağlama](secureMOF.md).
