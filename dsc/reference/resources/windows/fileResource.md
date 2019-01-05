---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC dosya kaynağı
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048749"
---
# <a name="dsc-file-resource"></a>DSC dosya kaynağı

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Dosya kaynağı, Windows PowerShell Desired State Configuration (DSC) hedef düğüm üzerindeki dosya ve klasörleri yönetmek için bir mekanizma sağlar.

>**Not:** Varsa **MatchSource** özelliği **$false** (varsayılan değer olan), yapılandırmanın geçerli olduğu ilk kez kopyalanacak içeriği önbelleğe alınır.
>Yapılandırmanın sonraki uygulamalar için güncelleştirilmiş dosyaları ve/veya klasörleri tarafından belirtilen yoldaki kontrol etmez **SourcePath**. Dosyaları ve/veya klasörleri güncelleştirmeleri denetlemesini istiyorsanız **SourcePath** yapılandırmanın uygulanması her zaman ayarlamak **MatchSource** için **$true**.

## <a name="syntax"></a>Sözdizimi
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| DestinationPath| Bir dosya veya dizin durumu sağlamak istediğiniz yeri gösterir.|
| Öznitelikler| İstenen durum hedeflenen dosya veya dizin özniteliklerini belirtir.|
| Sağlama| İki dosya aynı olup olmadığını belirlerken kullanılacak sağlama türünü gösterir. Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı, karşılaştırma için kullanılır. Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|
| İçerikler| Belirli bir dize gibi bir dosyanın içeriğini belirtir.|
| Kimlik bilgisi| Erişimi gerekiyorsa, kaynak dosyaları gibi kaynaklarına erişmek için gerekli kimlik bilgilerini gösterir.|
| Emin olun| Dosya veya dizin var olup olmadığını gösterir. "Yok" dosya veya dizin yok sağlamak için bu özelliği ayarlayın. "Dosya veya dizin var olmadığından emin olmak için mevcut" olarak ayarlayın. "Var" varsayılandır.|
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur. Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar. Varsayılan değer __$false__.|
| Recurse| Alt dizinleri dahil olup olmadığını gösterir. Bu özellik kümesine __$true__ dahil edilmesi için alt dizinler istediğinizi belirtmek için. Varsayılan değer __$false__. **Not**: Bu özellik yalnızca dizinine Type özelliği ayarlandığında geçerlidir.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| Kaynak yolu| Dosya veya klasör kaynak kopyalanacak yolunu gösterir.|
| Tür| Yapılandırılan kaynak bir dizin veya bir dosya olup olmadığını gösterir. Bu özelliği kaynak dizin olduğunu belirtmek için "dizin" olarak ayarlayın. "Kaynağı bir dosya olduğunu belirtmek üzere dosyaya" ayarlayın. "Dosya" varsayılan değerdir.|
| MatchSource| Varsayılan değerine ayarlanmasından __$false__, ardından yapılandırmanın geçerli olduğu ilk kez hedefe (örneğin, A, B ve C dosyaları) kaynak dosyaları eklenir. (D) yeni bir dosya için kaynak eklediyseniz, hatta yapılandırmayı daha sonra yeniden uygulandığında, bu hedefe eklenmeyecek. Değer ise __$true__, ardından yapılandırma uygulanır, her zaman sonradan kaynak (örneğin, bu örnekte dosyası D) bulunan yeni dosyaları hedefe eklenir. Varsayılan değer **$false**.|

## <a name="example"></a>Örnek

Aşağıdaki örnek bir dizin yolu ile emin olmak için dosyayı kaynak kullanmayı gösterir `C:\Users\Public\Documents\DSCDemo\DemoSource` bir kaynak bilgisayar (örneğin, "çekme" sunucusu) de (yanı sıra tüm alt dizinleri) varsa hedef düğümde bulunan. Ayrıca günlüğe tamamlandığında confirmatory bir ileti yazar ve dosya denetimini işlemi önce günlüğe kaydetme işlemi çalıştığından emin olmak için bir deyimi içerir.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```