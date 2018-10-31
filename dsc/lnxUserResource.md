---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxUser kaynağı
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226041"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC için Linux nxUser kaynağı

**NxUser** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde yerel kullanıcıları yönetmek için bir mekanizma sağlar.

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
| Emin olun| Hesap mevcut olup olmadığını belirtir. Bu hesabı var olduğundan emin olmak için "var" özelliğini ayarlayın ve "Eksik için" hesabı yok emin olmak için ayarlayın.|
| Tam adı| Kullanıcı hesabı için kullanılacak tam adını içeren bir dize.|
| Açıklama| Kullanıcı hesabı için açıklama.|
| Parola| Linux bilgisayar için uygun biçimde kullanıcılar parola karması. Genellikle, bir salted SHA-256 veya SHA-512 karma budur. Bu değer, Debian ve Ubuntu Linux üzerinde mkpasswd komutu ile oluşturulabilir. Diğer Linux dağıtımları için crypt yöntemi Python'un Crypt Kitaplığı'nın karmasını oluşturmak için kullanılabilir.|
| Devre Dışı| Hesabın etkin olup olmadığını gösterir. Bu özellik kümesine **$true** bu hesabı devre dışı ayarlamanız gerektiğini ve emin olmak için **$false** etkinleştirildiğinden emin olmak için.|
| PasswordChangeRequired| Kullanıcının parola değiştirip değiştiremeyeceğini belirtir. Bu özellik kümesine **$true** kullanıcı olamaz parolasını değiştirmek, ayarlayın sağlamak ve **$false** parolayı değiştirmek izin vermek için. Varsayılan değer **$false**. Bu özellik yalnızca kullanıcı hesabını daha önce yok ve oluşturulan değerlendirilir.|
| GirişDizini| Kullanıcı için giriş dizini.|
| GroupID| Kullanıcının birincil grup kimliği.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğu Kimliğini ilk "ResourceName" ve "ResourceType" kendi türü ise, bu özelliği kullanmaya ilişkin sözdizimini ise `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, "monuser" kullanıcı var ve "DBusers" grubunun bir üyesi olduğundan sağlar.

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