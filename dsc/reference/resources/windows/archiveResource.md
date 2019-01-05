---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Archive kaynağı
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048684"
---
# <a name="dsc-archive-resource"></a>DSC Archive kaynağı

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Archive kaynağı, Windows PowerShell Desired State Configuration (DSC), belirli bir yola arşiv (.zip) dosyalarını açmak için bir mekanizma sağlar.

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
| Hedef| Arşiv içeriğini ayıklanan sağlamak istediğiniz konumu belirtir.|
| Yol| Arşiv dosyasının kaynak yolunu belirtir.|
| __Sağlama toplamı__| İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar. Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı, karşılaştırma için kullanılır. Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, Hiçbiri (varsayılan). Belirtirseniz __sağlama toplamı__ olmadan __doğrulama__, yapılandırmanız başarısız olur.|
| Emin olun| Arşiv içeriğini, mevcut olup olmadığını denetleyin belirler __hedef__. Bu özellik kümesine __mevcut__ içeriği mevcut emin olmak için. Ayarlayın __devamsızlık__ mevcut emin olmak için. Varsayılan değer __mevcut__.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğu Kimliğini ilk ResourceName ve onun türü ise __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| Doğrulama| Arşiv imza eşleşip eşleşmediğini belirlemek için sağlama toplamı özelliğini kullanır. Sağlama toplamı doğrulama olmadan belirtirseniz, yapılandırma başarısız olur. SHA-256'yı sağlama toplamı, olmadan sağlama toplamı doğrulama belirtirseniz, varsayılan olarak kullanılır.|
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur. Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar. Varsayılan değer False olur.|

## <a name="example"></a>Örnek

Aşağıdaki örnek Archive kaynağı Test.zip adlı bir arşiv dosyasının içeriğini mevcut ve belirli bir hedefe ayıklanan emin olmak için nasıl kullanılacağını gösterir.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```