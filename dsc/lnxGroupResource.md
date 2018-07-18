---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxGroup kaynağı
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093611"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC için Linux nxGroup kaynağı

**NxGroup** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde yerel grupları yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| GroupName| Belirli bir durumu emin olmak istediğiniz grubun adını belirtir.|
| Emin olun| Grubun mevcut olup olmadığını denetleyin belirler. "Var" grubu var. olmak için bu özelliği ayarlayın. Kümesi "Yok" grubu sağlamak için mevcut değil. "Var" varsayılan değerdir.|
| Üyeler| Bir grup oluşturacak olan üyeleri belirtir.|
| MembersToInclude| Sağlamak istediğiniz kullanıcıları grubunun bir üyesi belirtir.|
| MembersToExclude| Sağlamak istediğiniz kullanıcıları grup üyesi olmayan belirtir.|
| PreferredGroupID| Mümkünse, Grup Kimliği sağlanan değere ayarlar. Grup Kimliği şu anda kullanımda ise sonraki kullanılabilir grup kimliği kullanılır.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, kullanıcı 'monuser' var ve 'DBusers' grubunun bir üyesi olduğundan sağlar.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```