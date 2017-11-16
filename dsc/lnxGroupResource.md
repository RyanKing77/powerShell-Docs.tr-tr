---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Linux nxGroup kaynak için"
ms.openlocfilehash: fcd1dfd3110b1358ed7ef9ca8d57154186b271f6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC Linux nxGroup kaynak için

**NxGroup** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümde yerel grupları yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama | 
|---|---|
| GroupName| Belirli bir durumu sağlamak istediğiniz grubun adını belirtir.| 
| Emin olun| Grubun var olup olmadığını denetlemek belirler. Bu özelliği Grup mevcut emin olmak için "var" olarak ayarlayın. "Mevcut için" grubu yok emin olmak için ayarlayın. "Var" varsayılan değerdir.| 
| Üyeler| Grup form üyeleri belirtir.| 
| MembersToInclude| Sağlamak istediğiniz kullanıcıları grubunun bir üyesi belirtir.| 
| MembersToExclude| Sağlamak istediğiniz kullanıcıları grubunun üyesi olmayan belirtir.| 
| PreferredGroupID| Grup Kimliği için sağlanan değer mümkünse ayarlar. Grup Kimliği şu anda kullanımda ise, bir sonraki kullanılabilir grup kimliği kullanılır.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.| 

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

