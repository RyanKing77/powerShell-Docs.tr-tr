---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kullanıcı kaynağı
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892534"
---
# <a name="dsc-user-resource"></a>DSC kullanıcı kaynağı

Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

**Kullanıcı** kaynak olarak Windows PowerShell Desired State Configuration (DSC) hedef düğümde yerel kullanıcı hesaplarını yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

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
| Açıklama| Kullanıcı hesabı için kullanmak istediğiniz açıklamayı gösterir.|
| Devre Dışı| Hesabın etkin olup olmadığını gösterir. Bu özellik kümesine `$true` bu hesabı devre dışı ayarlamanız gerektiğini ve emin olmak için `$false` etkinleştirildiğinden emin olmak için.|
| Emin olun| Hesap var olup olmadığını gösterir. Bu hesabı var olduğundan emin olmak için "var" özelliğini ayarlayın ve "Eksik için" hesabı yok emin olmak için ayarlayın.|
| Tam adı| Kullanıcı hesabı için kullanmak istediğiniz tam ada sahip bir dizeyi temsil eder.|
| Parola| Bu hesap için kullanmak istediğiniz parolayı gösterir. |
| PasswordChangeNotAllowed| Kullanıcı parola değiştirip değiştiremeyeceğini belirtir. Bu özellik kümesine `$true` kullanıcı olamaz parolasını değiştirmek, ayarlayın sağlamak ve `$false` parolayı değiştirmek izin vermek için. Varsayılan değer `$false`.|
| PasswordChangeRequired| Kullanıcı bir sonraki oturum açma sırasında parola değiştirmeli gösterir. Bu özellik kümesine `$true` kullanıcı parolasını değiştirmeniz gerekiyorsa. Varsayılan değer `$true`.|
| PasswordNeverExpires| Parola dolacak gösterir. Bu hesap süresi asla sona için parolayı bu özelliği ayarlayın emin olmak için `$true`ve `$false` parola doluyorsa. Varsayılan değer `$false`.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|

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