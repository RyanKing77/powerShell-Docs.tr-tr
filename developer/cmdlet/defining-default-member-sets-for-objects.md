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
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="deb53-102">Nesneler için Varsayılan Üye Kümeleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="deb53-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="deb53-103">PSStandardMembers üye kümesi, bir nesne için varsayılan özellik kümeleri tanımlamak için Windows PowerShell tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="deb53-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="deb53-104">Varsayılan özellik kümeleri biçimlendirme cmdlet'ler gibi komutlar tarafından ayarlanan özelliği tarafından tanımlanan özelliklerini görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="deb53-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="deb53-105">Varsayılan özellik kümeleri DefaultDisplayProperty DefaultDisplayPropertySet ve DefaultKeyPropertySet içerir.</span><span class="sxs-lookup"><span data-stu-id="deb53-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="deb53-106">Windows PowerShell, diğer tüm üye kümeleri ve PSStandardMembers üye kümeye eklenen diğer özellik kümeleri yok sayar.</span><span class="sxs-lookup"><span data-stu-id="deb53-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="deb53-107">Üye kümesi System.Diagnostics.Process için</span><span class="sxs-lookup"><span data-stu-id="deb53-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="deb53-108">Aşağıdaki örnekte, PSStandardMembers üye kümesi için DefaultDisplayPropertySet özelliği tanımlar. [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="deb53-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="deb53-109">Bu özellik kümesi tarafından kullanılan [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="deb53-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="deb53-110">Aşağıdaki çıktı tarafından döndürülen varsayılan özelliklerini gösterir [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="deb53-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="deb53-111">Yalnızca `Id`, `Handles`, `CPU`, ve `Name` özellikleri için her işlem nesnesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="deb53-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="deb53-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="deb53-112">See Also</span></span>

[<span data-ttu-id="deb53-113">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="deb53-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
