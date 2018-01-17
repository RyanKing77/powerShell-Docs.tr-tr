---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC dosya kaynağı"
ms.openlocfilehash: 54d01bf0769eeed0354606eb3543973b0f850a6f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-file-resource"></a>DSC dosya kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Dosya kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC) dosyaları ve klasörleri hedef düğümde bulunan yönetmek için bir mekanizma sağlar.

>**Not:** varsa **MatchSource** özelliği ayarlanmış **$false** (varsayılan değer olan), yapılandırma uygulanan ilk kez kopyalanacak içeriği önbelleğe alınır. 
>Yapılandırmanın sonraki uygulamalar için güncelleştirilmiş dosyaları ve/veya klasörleri tarafından belirtilen yoldaki kontrol etmez **KaynakYolu**. Dosyaları ve/veya klasörlerde güncelleştirmeleri denetlemek istiyorsanız **KaynakYolu** yapılandırmanın uygulanması her zaman ayarlamak **MatchSource** için **$true**. 

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
| HedefYolu| Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.| 
| Öznitelikler| Belirtilen istenen duruma hedeflenen dosya veya dizin özniteliklerini belirtir.| 
| Sağlama| İki dosya aynı olup olmadığını belirlerken kullanılacak sağlama türünü gösterir. Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı karşılaştırma için kullanılır. Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.| 
| İçerikler| Belirli bir dize gibi bir dosyanın içeriğini belirtir.| 
| kimlik bilgisi| Bu tür erişimi gerekiyorsa kaynak dosyaları gibi kaynaklara erişmek için gerekli kimlik bilgilerini gösterir.| 
| Emin olun| Dosya veya dizin var olup olmadığını gösterir. Bu özelliği dosya veya dizin yok emin olmak için "yok" olarak ayarlayın. "Dosya veya dizin var olmadığından emin olmak için mevcut" ayarlayın. "Var" varsayılandır.| 
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır. Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar. Varsayılan değer __$false__.| 
| Recurse| Alt dizinleri dahil olup olmadığını gösterir. Bu özelliği ayarlamak __$true__ dahil edilmesi için alt dizinler istediğinizi belirtmek için. Varsayılan değer __$false__. **Not**: Bu özellik yalnızca Type özelliği dizinine olarak ayarlandığında geçerlidir.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.| 
| Kaynak yolu| Dosya veya klasör kaynak kopyalanacak yolunu gösterir.| 
| Tür| Yapılandırılmakta kaynak bir dizin veya bir dosya olup olmadığını gösterir. Bu özelliği kaynak bir dizin olduğunu belirtmek için "dizin" olarak ayarlayın. "Kaynak dosya olduğunu belirtmek için dosyaya" ayarlayın. Varsayılan değer "Dosyası" dir.| 
| MatchSource| Varsa varsayılan değer olarak ayarlı __$false__, sonra tüm dosyalar (örneğin, A, B ve C dosyaları) kaynak üzerinde yapılandırma uygulanan ilk kez hedefe eklenir. Yeni bir dosya (D) kaynağına eklediyseniz, bile yapılandırmayı daha sonra yeniden uygulandığında, bu hedefe eklenmez. Değer ise __$true__, yapılandırma uygulanır, her zaman hedefe sonradan kaynak (örneğin, bu örnekte dosyası D) bulunan yeni dosyalar eklenirken sonra. Varsayılan değer **$false**.| 

## <a name="example"></a>Örnek

Aşağıdaki örnekte bir dizin yolu ile emin olmak için dosya kaynağı kullanmayı gösterir `C:\Users\Public\Documents\DSCDemo\DemoSource` üzerinde bir kaynağı (örneğin, "çekme" sunucu) de (yanı sıra tüm alt dizinler) mevcut bilgisayardır hedef düğümde bulunan. Ayrıca günlüğe tamamlandığında confirmatory bir ileti yazar ve dosyası denetleniyor işlemi önce günlüğe kaydetme işlemi çalıştığından emin olmak için bir ifade içerir.

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

