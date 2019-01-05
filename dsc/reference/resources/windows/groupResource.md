---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Group kaynağı
ms.openlocfilehash: 9894150f6f749fc23efd4ce2b155b18788557d1d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048648"
---
# <a name="dsc-group-resource"></a>DSC Group kaynağı

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Group kaynağı, Windows PowerShell Desired State Configuration (DSC), hedef düğümde yerel grupları yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| GroupName| Belirli bir durumu emin olmak istediğiniz grubun adı.|
| Kimlik bilgisi| Uzak kaynaklara erişmek için gerekli kimlik bilgileri. **Not**: Bu hesap, tüm yerel olmayan hesapları grubuna eklemek için Active Directory iznine sahip olmalıdır; Aksi takdirde, yapılandırmasını hedef düğümde yürütülürken bir hata oluşur.
| Açıklama| Grup açıklaması.|
| Emin olun| Grubun var olup olmadığını gösterir. "Yok" grubu yok sağlamak için bu özelliği ayarlayın. "(Varsayılan değer) sunmak için" ayarı, grubun var olmasını sağlar.|
| Üyeler| Belirtilen üye ile geçerli grup üyeliğini değiştirmek için bu özelliği kullanın. Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*. Bir yapılandırmada bu özelliği ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği. Bunun yapılması, bir hata oluşturur.|
| MembersToExclude| Grubun mevcut üyelikten üyeleri kaldırmak için bu özelliği kullanın. Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*. Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği. Bunun yapılması, bir hata oluşturur.|
| MembersToInclude| Mevcut üyelik grubunun üyeleri eklemek için bu özelliği kullanın. Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*. Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği. Bunun yapılması, bir hata oluşturur.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.|

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, "Testgrubu" adlı bir grup mevcut olduğundan emin olmak gösterilmektedir.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek, bir Active Directory kullanıcısı nerede zaten bir PSCredential yerel yönetici hesabı için kullandığınız birden çok makine Laboratuvar yapının bir parçası olarak yerel administrators grubuna eklemek gösterilmektedir.
Bu da etki alanı yönetici hesabı (etki alanı yükseltme sonrasında) kullanıldıkça, ardından bu mevcut PSCredential etki alanında kolay bir kimlik bilgisi ile dönüştürmek ihtiyacımız var.
Ardından yerel Yöneticiler grubuna üye sunucusunda bir etki alanı kullanıcısı ekleyebiliriz.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Örnek 3

Aşağıdaki örnek, yerel bir grup TigerTeamAdmins emin olmak gösterilmektedir, sunucuda bir özel etki alanı hesabı Contoso\JerryG TigerTeamSource.Contoso.Com içermiyor.

```powershell
Configuration SecureTigerTeamSrouce {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```