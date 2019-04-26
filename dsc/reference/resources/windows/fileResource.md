---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC dosya kaynağı
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077339"
---
# <a name="dsc-file-resource"></a>DSC dosya kaynağı

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

Dosya kaynağı, Windows PowerShell Desired State Configuration (DSC) hedef düğüm üzerindeki dosya ve klasörleri yönetmek için bir mekanizma sağlar. **HedefYolu** ve **SourcePath** hem de hedef düğüm tarafından erişilebilir olması gerekir.

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

|Özellik       |Açıklama                                                                   |Gerekli|Varsayılan|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|Sağlamak istediğiniz hedef düğümde konumu olan `Present` veya `Absent`.|Evet|Hayır|
|Öznitelikler     |Hedef dosya veya dizin özniteliklerini istenen durum. Geçerli değerler **arşiv**, **gizli**, **salt okunur**, ve **sistem**.|Hayır|Yok|
|Sağlama toplamı      |İki dosya aynı olup olmadığını belirlerken kullanılacak sağlama türü. Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|Hayır|Yalnızca dosya veya dizin adı karşılaştırılır.|
|İçerikler       |İle kullanıldığında geçerli `File` türü. Olun içeriğini gösterir `Present` veya `Absent` hedeflenen dosyasından. |Hayır|Yok|
|Kimlik bilgisi     |Kaynak dosyaları gibi kaynaklarına erişmek için gerekli olan kimlik bilgileri.|Hayır|Hedef düğümün bilgisayar hesabı. (*bkz. Not*)|
|Emin olun         |Hedef dosya veya dizin istenen durumu. |Hayır|**Mevcut**|
|Force          |(Örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hata ile sonuçlandı erişim işlemleri geçersiz kılar.|Hayır|`$false`|
|Recurse        |İle kullanıldığında geçerli `Directory` türü. Durum işlem yinelemeli olarak tüm alt dizinler için gerçekleştirir.|Hayır|`$false`|
|dependsOn      |Belirtilen kaynaklar üzerinde bir bağımlılık ayarlar. Bu kaynak, yalnızca tüm bağımlı kaynakları başarılı yürütme sonrasında yürütülür. Bağımlı kaynaklar söz dizimini kullanarak belirttiğiniz `"[ResourceType]ResourceName"`. Bkz: [about_DependsOn](../../../configurations/resource-depends-on.md)|Hayır|Yok|
|Kaynak yolu     |Dosya veya klasör kaynak kopyalama kaynağı yolu.|Hayır|Yok|
|Tür           |Yapılandırılan kaynak türü. Geçerli değerler `Directory` ve `File`.|Hayır|`File`|
|MatchSource    |Kaynak ilk kopyayı sonra kaynak dizine eklenen yeni dosyalar için izlemeniz gerekir, belirler. Değerini `$true` ilk kopyalamadan sonra yeni kaynak dosyalarını hedefe kopyalanması gereken olduğunu belirtir. Varsa kümesine `$False`, kaynağın kaynak dizinin içeriğini önbelleğe alır ve ilk kopyalamadan sonra eklenen tüm dosyaları yok sayar.|Hayır|`$false`|

> [!WARNING]
> İçin bir değer belirtmezseniz `Credential` veya `PSRunAsCredential` (PS V.5), kaynak bilgisayar hesabını hedef düğüme erişmek için kullanacağı `SourcePath`.  Zaman `SourcePath` olduğu bir UNC paylaşımı, bu bir "Erişim reddedildi" hata neden olabilir. Lütfen izinlerinizi buna uygun olarak ayarlayın ya da kullanmak olun `Credential` veya `PSRunAsCredential` özellikler kullanılması gereken hesabı belirtin.

## <a name="present-vs-absent"></a>Mevcut vs. Yok

Her DSC kaynak için belirttiğiniz değere göre farklı işlemler gerçekleştiren `Ensure` özelliği. Yukarıdaki özelliklerini belirler durumu işlemi için belirttiğiniz değerleri gerçekleştirdi.

### <a name="existence"></a>Varlığı

Yalnızca belirttiğinizde bir `DestinationPath`, yolun var olduğundan kaynak sağlar (`Present`) veya yok (`Absent`).

### <a name="copy-operations"></a>Kopyalama işlemleri

Belirttiğinizde bir `SourcePath` ve `DestinationPath` ile bir `Type` değerini **dizin**, hedef yol için kaynak kopya kaynak dizini. Özellikleri `Recurse`, `Force`, ve `MatchSource` kopyalama işlemi türünü değiştirme gerçekleştirilirse, while `Credential` kaynak dizinine erişmek için kullanacağınız hesabı belirler.

### <a name="limitations"></a>Sınırlamalar

Değeri belirtilmişse `ReadOnly` için `Attributes` özelliğinin yanı sıra bir `DestinationPath`, `Ensure = "Present"` belirtilen yol oluşturacak sırada `Contents` dosyasının içeriğini ayarlamanız gerekir.  Bir `Absent` durumu işlemi yoksayacaktır `Attributes` özelliği tamamen ve belirtilen yoldaki tüm dosyayı kaldırın.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir dizin ve alt dizinlerinde çekme sunucusundan dosya kaynağı kullanan bir hedef düğüme kopyalar. İşlem başarılı olursa, Log kaynağı bir onay iletisi olay günlüğüne yazar.

Kaynak dizini UNC yoludur (`\\PullServer\DemoSource`) çekme sunucusundan paylaşılan. `Recurse` Özelliği sağlar tüm alt dizinler de kopyalanır.

> [!IMPORTANT]
> LCM hedef düğüm varsayılan olarak yerel sistem hesabı bağlamında çalışır. Erişim izni vermek için **SourcePath**, hedef düğümün bilgisayar hesabının uygun izinleri verin. **Kimlik bilgisi** ve **PSDSCRunAsCredential** (v5) hem de erişmek için kullandığı bağlam LCM değiştirme **SourcePath**. Kullanılacak hesap erişim vermek yine erişimi **SourcePath**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Daha fazla üzerinde kullanma **kimlik bilgilerini** DSC görüyor [kullanıcı olarak çalıştır](../../../configurations/runAsUser.md) veya [yapılandırma veri kimlik bilgileri](../../../configurations/configDataCredentials.md).
