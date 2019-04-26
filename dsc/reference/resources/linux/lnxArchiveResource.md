---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxArchive kaynağı
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078053"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC için Linux nxArchive kaynağı

**NxArchive** kaynak içinde PowerShell Desired State Configuration (DSC), belirli bir yola Arşivi (.tar, .zip) dosyaları bir Linux düğümde açmak için bir mekanizma sağlar.

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
| Kaynak yolu| Arşiv dosyasının kaynak yolunu belirtir. Bu bir .tar olmalıdır, .zip veya. tar.gz dosyasını. |
| DestinationPath| Arşiv içeriğini ayıklanan sağlamak istediğiniz konumu belirtir.|
| Sağlama toplamı| Kaynak arşiv güncelleştirilip güncelleştirilmediğini belirlenirken kullanılacak türünü tanımlar. Değerler: "ctime", "mtime" veya "md5". Varsayılan değer "md5"'tir.|
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur. Kullanarak **zorla** özelliği, bu tür hatalar'ı geçersiz kılar. Varsayılan değer **$false**.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|
| Emin olun| Arşiv içeriğini, mevcut olup olmadığını denetleyin belirler **hedef**. Bu özelliği içeriği mevcut emin olmak için "var" olarak ayarlayın. "Eksik için" mevcut emin olmak için ayarlayın. "Var" varsayılan değerdir.|

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl kullanılacağını gösterir **nxArchive** Arşiv dosyasının içeriğini adlı emin olmak için kaynak `website.tar` var ve belirli bir hedefe ayıklanır.

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