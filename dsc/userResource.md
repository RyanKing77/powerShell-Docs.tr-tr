---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kullanıcı kaynağı
ms.openlocfilehash: f2660933aec43967e3f4082a983ef328a5b93851
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
#<a name="dsc-user-resource"></a>DSC kullanıcı kaynak #


>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0


__Kullanıcı__ kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), hedef düğümde bulunan yerel kullanıcı hesaplarını yönetmek için bir mekanizma sağlar.


##<a name="syntax"></a>Sözdizimi ##

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Özellikler
|  Özellik  |  Açıklama   |
|---|---|
| UserName| Belirli bir durumu sağlamak istediğiniz hesap adını gösterir.|
| Açıklama| Kullanıcı hesabı için kullanmak istediğiniz açıklamayı belirtir.|
| Devre Dışı| Hesabın etkin olup olmadığını gösterir. Bu özelliği ayarlamak __$true__ bu hesap devre dışı ve ayarlamak olduğunu emin olmak için __$false__ için etkinleştirildiğinden emin olun.|
| Emin olun| Hesabının mevcut olup olmadığını gösterir. Bu hesabı var olduğundan emin olmak için "var" özelliğine ayarlayın ve "Mevcut için" hesap yok emin olmak için ayarlayın.|
| FullName| Kullanıcı hesabı için kullanmak istediğiniz tam adı bir dizeyle temsil eder.|
| Parola| Bu hesap için kullanmak istediğiniz parolayı gösterir. |
| PasswordChangeNotAllowed| Kullanıcının parolayı değiştirirseniz gösterir. Bu özelliği ayarlamak __$true__ kullanıcı olamaz parolasını değiştirmek ve ayarlamak emin olmak için __$false__ parola değiştirmeye izin vermek için. Varsayılan değer __$false__.|
| PasswordChangeRequired| Kullanıcı bir sonraki oturum açmada parola değiştirmeli gösterir. Bu özelliği ayarlamak __$true__ kullanıcı parolasını değiştirmeniz gerekiyorsa. Varsayılan değer __$true__.|
| PasswordNeverExpires| Parola sona erecek gösterir. Bu hesap süresiz için parola bu özelliği ayarlamak emin olmak için __$true__ve ayarlamak __$false__ parola süresi dolacak durumunda. Varsayılan değer __$false__.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```