---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxArchive kaynak için
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC Linux nxArchive kaynak için

**NxArchive** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), belirli bir yola Arşivi (.tar, .zip) dosyaları bir Linux düğümündeki açmak için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| Kaynak yolu| Arşiv dosyasını kaynak yolunu belirtir. Bu bir .tar olmalıdır .zip, veya. tar.gz dosyasını. |
| HedefYolu| Arşiv içeriği ayıklanır sağlamak istediğiniz konumu belirtir.|
| Sağlama| Kaynak arşiv güncelleştirilip güncelleştirilmediğini belirlenirken kullanılacak türünü tanımlar. Değerler: "ctime", "mtime" veya "md5". Varsayılan değer "md5" dir.|
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır. Kullanarak **zorla** özelliği gibi hataları geçersiz kılar. Varsayılan değer **$false**.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|
| Emin olun| Arşiv içeriğini adresindeki var olup olmadığını denetlemek belirler **hedef**. Bu özelliği içeriği mevcut emin olmak için "var" olarak ayarlayın. "Mevcut için" mevcut emin olmak için ayarlayın. "Var" varsayılan değerdir.|

## <a name="example"></a>Örnek

Aşağıdaki örnekte nasıl kullanılacağını gösterir **nxArchive** bir arşiv dosyasının içeriğini adlı emin olmak için kaynak `website.tar` var ve belirli bir hedefe ayıklanır.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```