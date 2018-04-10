---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxUser kaynak için
ms.openlocfilehash: 222bd2191cf5c5f0a90ba947275ffde47d22ec86
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC Linux nxUser kaynak için

**NxUser** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümde yerel kullanıcıları yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Belirli bir durumu sağlamak istediğiniz hesap adını gösterir. |
|---|---|
| UserName| Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.|
| Emin olun| Hesap var olup olmadığını belirtir. Bu hesabı var olduğundan emin olmak için "var" özelliğine ayarlayın ve "Mevcut için" hesap yok emin olmak için ayarlayın.|
| FullName| Kullanıcı hesabı için kullanılacak tam adını içeren dize.|
| Açıklama| Kullanıcı hesabı açıklaması.|
| Parola| Linux bilgisayar için uygun biçimde kullanıcılar parola karması. Genellikle, bir güvenlik SHA-256 ve SHA-512 karma budur. Debian ve Ubuntu Linux üzerinde bu değer mkpasswd komutuyla oluşturulabilir. Python'un Crypt kitaplığının crypt yöntemi diğer Linux distro'lar için karma değeri üretmek için kullanılır.|
| Devre Dışı| Hesabın etkin olup olmadığını gösterir. Bu özelliği ayarlamak **$true** bu hesap devre dışı ve ayarlamak olduğunu emin olmak için **$false** için etkinleştirildiğinden emin olun.|
| PasswordChangeRequired| Kullanıcı parolalarını değiştirip değiştiremeyeceğini gösterir. Bu özelliği ayarlamak **$true** kullanıcı olamaz parolasını değiştirmek ve ayarlamak emin olmak için **$false** parola değiştirmeye izin vermek için. Varsayılan değer **$false**. Bu özellik, yalnızca kullanıcı hesabını daha önce yoktu ve oluşturuldu değerlendirilir.|
| GirişDizini| Kullanıcı için giriş dizini.|
| GroupID| Kullanıcının birincil grup kimliği.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğunda Kimliğini ilk "ResourceName" ve "ResourceType" türü ise, bu özelliği kullanan sözdizimi ise `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnekte, kullanıcı "monuser" mevcut ve "DBusers" grubunun bir üyesi olduğundan sağlar.

```
Import-DSCResource -Module nx

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```