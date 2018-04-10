---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
description: Hedef düğümde bulunan yerel grupları yönetmek için bir mekanizma sağlar.
title: DSC GroupSet kaynağı
ms.openlocfilehash: 4f8fc21806fdb4eb06e0d915d5b6ca229357a210
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-groupset-resource"></a>DSC GroupSet kaynağı

> İçin geçerlidir: Windows Windows PowerShell 5.0

**GroupSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), yerel gruplar hedef düğümde bulunan yönetmek için bir mekanizma sağlar. Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [kaynak grubunda](groupResource.md) belirtilen her grup için `GroupName` parametresi.

Bu kaynak ekleme ve/veya birden fazla gruba üye aynı listesi kaldırmak, birden fazla grubu kaldırmak veya üyeleri aynı listesiyle birden fazla grubu ekleme yapmak istediğinizde kullanın.

##<a name="syntax"></a>Sözdizimi ##
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
| MembersToExclude| Gruplar mevcut üyeliğinden üyeleri kaldırmak için bu özelliği kullanın. Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*. Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği. Bunun yapılması bir hata oluşturur.|
| kimlik bilgisi| Uzak kaynaklara erişmek için gerekli kimlik bilgileri. **Not**: Bu hesap tüm yerel olmayan hesapları grubuna eklemek için uygun Active Directory izinleri olması gerekir; aksi takdirde bir hata ortaya çıkar.
| Emin olun| Gruplar mevcut olup olmadığını gösterir. Bu özelliği grubu mevcut emin olmak için "yok" olarak ayarlayın. "(Varsayılan değer) sunmak için" olarak ayarlanması grupların bulunmasını sağlar.|
| Üyeler| Belirtilen üyeleriyle geçerli grup üyeliğini değiştirmek için bu özelliği kullanın. Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*. Bu özellik bir yapılandırmada ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği. Bunun yapılması bir hata oluşturur.|
| MembersToInclude| Grubun var olan üyeliğini üye eklemek için bu özelliği kullanın. Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*. Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği. Bunun yapılması bir hata oluşturur.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.|

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnekte, "myGroup" ve "myOtherGroup" adlı iki grup mevcut olduğundan emin olun gösterilmektedir.

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

>**Not:** Bu örnek düz metin kimlik bilgileri kolaylık sağlamak için kullanır. Yapılandırma MOF dosyasındaki kimlik bilgilerini şifrelemek hakkında daha fazla bilgi için bkz: [MOF dosyası güvenli hale getirme](secureMOF.md).