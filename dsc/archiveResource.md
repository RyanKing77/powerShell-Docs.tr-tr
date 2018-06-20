---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC arşiv kaynak
ms.openlocfilehash: 458b4f0f20dc96dab62e709183c25ff57d971aae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219479"
---
# <a name="dsc-archive-resource"></a>DSC arşiv kaynak

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Arşiv kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) belirli bir yola arşiv (.zip) dosyalarını açmak için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Hedef| Arşiv içeriği ayıklanır sağlamak istediğiniz konumu belirtir.|
| Yol| Arşiv dosyasını kaynak yolunu belirtir.|
| __Sağlama toplamı__| İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar. Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı karşılaştırma için kullanılır. Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (varsayılan). Belirtirseniz __sağlama toplamı__ olmadan __doğrulama__, yapılandırma başarısız olur.|
| Emin olun| Arşiv içeriğini adresindeki var olup olmadığını denetlemek belirler __hedef__. Bu özelliği ayarlamak __mevcut__ içeriği mevcut emin olmak için. Ayarlamak __etmeksizin__ mevcut emin olmak için. Varsayılan değer __mevcut__.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğunda Kimliğini ilk KaynakAdı ve onun türü ise __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| Doğrula| Arşiv imza eşleşip eşleşmediğini belirlemek için sağlama özelliğini kullanır. Sağlama toplamı doğrulama olmadan belirtirseniz, yapılandırma başarısız olur. SHA-256 sağlama toplamı doğrulama sağlama toplamı olmadan belirtirseniz, varsayılan olarak kullanılır.|
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır. Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar. Varsayılan değer False olur.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, arşiv kaynak Test.zip adlı bir arşiv dosyasının içeriğini mevcut ve belirli bir hedefe ayıklanır emin olmak için nasıl kullanılacağını gösterir.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```