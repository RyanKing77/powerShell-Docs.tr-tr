---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxPackage kaynağı
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685686"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC için Linux nxPackage kaynağı

**NxPackage** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde paketlerini yönetmek için bir mekanizma sağlar.

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
| Adı| Belirli bir durumu sağlamak istediğiniz paketin adı.|
| Emin olun| Paket mevcut olup olmadığını denetleyin belirler. "Var" Paket var. olmak için bu özelliği ayarlayın. Kümesi "Yok" Paket sağlamak için mevcut değil. "Var" varsayılan değerdir.|
| PackageManager| Desteklenen değerler şunlardır: "yum", "apt" ve "zypper". Paket Yöneticisi paketleri yüklerken kullanılacak belirtir. Varsa **FilePath** belirtilirse, sağlanan yol, paketi yüklemek için kullanılır. Aksi takdirde, bir paket Yöneticisi, önceden yapılandırılmış bir depodan paketini yüklemek için kullanılır. Kullanılmazsa **PackageManager** ya da **FilePath** sağlanır, varsayılan Paket Yöneticisi için sistem kullanılır.|
| Dosya yolu| Paketin bulunduğu dosya yolu|
| PackageGroup| Varsa **$true**, **adı** ile kullanmak için bir paket grubu adını olması beklenen bir **PackageManager**. **PacakgeGroup** sağlanırken geçersiz bir **FilePath**.|
| Bağımsız değişkenler| Paketi tam olarak sağlanan şekilde geçirilecek bağımsız değişken bir dize.|
| ReturnCode| Beklenen dönüş kodu. Gerçek kodu döndürmesi durumunda beklenen değer, burada, yapılandırma, bir hata döndürür sağlanan eşleşmiyor.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, "httpd" adlı bir paket "ı Yum" Paket Yöneticisi'ni kullanarak bir Linux bilgisayara yüklendiğini sağlar.

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