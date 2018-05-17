---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC grubu kaynağı
ms.openlocfilehash: 68e0840eaeb116b92260ca697acd5796460a2909
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-group-resource"></a>DSC grubu kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Grup kaynağına, Windows PowerShell istenen durum yapılandırması (DSC) hedef düğümde bulunan yerel grupları yönetmek için bir mekanizma sağlar.

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
| GroupName| Belirli bir durumu sağlamak istediğiniz grubunun adı.|
| kimlik bilgisi| Uzak kaynaklara erişmek için gerekli kimlik bilgileri. **Not**: Bu hesabın tüm yerel olmayan hesapları grubuna eklemek için uygun Active Directory izinleri olması gerekir; aksi halde, yapılandırmasını hedef düğümde çalıştırıldığında bir hata oluşur.
| Açıklama| Grubun açıklaması.|
| Emin olun| Grubun var olup olmadığını gösterir. Bu özelliği grubu yok emin olmak için "yok" olarak ayarlayın. "(Varsayılan değer) sunmak için" olarak ayarlanması, grubun var olduğundan sağlar.|
| Üyeler| Belirtilen üyeleriyle geçerli grup üyeliğini değiştirmek için bu özelliği kullanın. Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*. Bu özellik bir yapılandırmada ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği. Bunun yapılması bir hata oluşturur.|
| MembersToExclude| Grup varolan üyeliğinden üyeleri kaldırmak için bu özelliği kullanın. Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*. Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği. Bunun yapılması bir hata oluşturur.|
| MembersToInclude| Grubun var olan üyeliğini üye eklemek için bu özelliği kullanın. Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*. Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği. Bunun yapılması bir hata oluşturur.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.|

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnekte, "TestGroup" adlı bir grup mevcut olduğundan emin olmak gösterilmiştir.

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

Aşağıdaki örnek, bir Active Directory kullanıcı zaten bir PSCredential yerel yönetici hesabı için kullandığınız birden çok makine Laboratuvar yapının parçası olarak yerel administrators grubuna eklemek gösterilmiştir.
Bu ayrıca etki alanı yönetici hesabını (etki alanı yükseltme sonrasında) kullanıldığından, biz sonra bu varolan PSCredential için etki alanı kolay bir kimlik bilgisi dönüştürmeniz gerekir.
Ardından biz üye sunucuda yerel Yöneticiler grubunun bir etki alanı kullanıcısı ekleyebilirsiniz.

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

Aşağıdaki örnek, yerel bir grup TigerTeamAdmins emin olmak gösterilmektedir, sunucu üzerinde belirli etki alanı hesabı, Contoso\JerryG TigerTeamSource.Contoso.Com içermiyor.

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