---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Linux nxPackage kaynak için"
ms.openlocfilehash: 11019b1cd12f23b0b498b7cb9a06e02c46c3c279
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC Linux nxPackage kaynak için

**NxPackage** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümünde paketlerini yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama | 
|---|---|
| Ad| Belirli bir durumu sağlamak istediğiniz paket adı.| 
| Emin olun| Paketin var olup olmadığını denetlemek belirler. Bu özelliği paketin varolduğundan emin olmak için "var" olarak ayarlayın. "Mevcut için" paketi yok emin olmak için ayarlayın. "Var" varsayılan değerdir.|  
| PackageManager| "Yum", "apt" ve "zypper" değerleri desteklenir. Paket Yöneticisi'ni paketleri yüklerken kullanılacak belirtir. Varsa **FilePath** belirtilirse, sağlanan yol, paketi yüklemek için kullanılacak. Aksi halde, bir paket Yöneticisi, önceden yapılandırılmış bir depodan paketi yüklemek için kullanılır. Ne **PackageManager** ya da **FilePath** sağlanır, varsayılan Paket Yöneticisi sistem kullanılacak için.| 
| filePath| Paketin bulunduğu dosya yolu| 
| PackageGroup| Varsa **$true**, **adı** ile kullanmak için bir paket grubunun adını olması beklenen bir **PackageManager**. **PacakgeGroup** sağlanırken geçersiz bir **FilePath**.| 
| Bağımsız değişkenler| Paketi tam olarak sağlanan gibi geçirilen bağımsız değişken bir dize.| 
| ReturnCode| Beklenen dönüş kodu. Gerçek kodu döndürmesi durumunda yapılandırma bir hata döndürecektir beklenen değer burada sağlanan adla eşleşmiyor.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Örnek

Aşağıdaki örnekte, "httpd" adlı paket "Yum" Paket Yöneticisi'ni kullanarak bir Linux bilgisayara yüklendiğini sağlar.

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```

