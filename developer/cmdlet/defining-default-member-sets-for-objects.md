---
title: Ayarlar nesneler için varsayılan üye tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794918"
---
# <a name="defining-default-member-sets-for-objects"></a>Nesneler için Varsayılan Üye Kümeleri Tanımlama

PSStandardMembers üye kümesi, bir nesne için varsayılan özellik kümeleri tanımlamak için Windows PowerShell tarafından kullanılır. Varsayılan özellik kümeleri biçimlendirme cmdlet'ler gibi komutlar tarafından ayarlanan özelliği tarafından tanımlanan özelliklerini görüntülemek için kullanılabilir. Varsayılan özellik kümeleri DefaultDisplayProperty DefaultDisplayPropertySet ve DefaultKeyPropertySet içerir. Windows PowerShell, diğer tüm üye kümeleri ve PSStandardMembers üye kümeye eklenen diğer özellik kümeleri yok sayar.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Üye kümesi System.Diagnostics.Process için

Aşağıdaki örnekte, PSStandardMembers üye kümesi için DefaultDisplayPropertySet özelliği tanımlar. [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesneleri. Bu özellik kümesi tarafından kullanılan [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet'i.

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

Aşağıdaki çıktı tarafından döndürülen varsayılan özelliklerini gösterir [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet'i. Yalnızca `Id`, `Handles`, `CPU`, ve `Name` özellikleri için her işlem nesnesi döndürülür.

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
