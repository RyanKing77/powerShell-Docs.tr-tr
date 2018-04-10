---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma verileri kullanma
ms.openlocfilehash: 19544494a547a06d87701b38585844cb11d03e33
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="using-configuration-data-in-dsc"></a>DSC yapılandırma verileri kullanma

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Yerleşik DSC kullanarak **ConfigurationData** parametresi, içinde bir yapılandırması kullanılabilir veri tanımlayabilirsiniz.
Bu, farklı ortamlar için veya birden çok düğüm için kullanılan tek bir yapılandırma oluşturmanızı sağlar.
Örneğin, bir uygulama geliştiriyorsanız, geliştirme ve üretim ortamları için bir yapılandırma kullanın ve yapılandırma verilerini her ortam için verileri belirtmek için kullanın.

Bu konuda yapısını açıklayan **ConfigurationData** hashtable.
Yapılandırma verileri kullanma örnekleri için bkz: [yapılandırma ve ortam verilerin ayrılmasını](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>ConfigurationData ortak parametresi

DSC yapılandırması bir ortak parametresi alan **ConfigurationData**, yapılandırmayı derleme zaman belirtin.
Derleme yapılandırmaları hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md).

**ConfigurationData** parametredir adlı en az bir anahtar olmalıdır hasthtable **AllNodes**.
Bir veya daha fazla diğer anahtarlar da olabilir.

>**Not:** bu konudaki örnekler tek bir ek anahtar kullanır (adlandırılmış dışında **AllNodes** anahtarı) adlı `NonNodeData`, ancak herhangi bir ek anahtar içerir ve bunları istediğiniz ad.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

Değeri **AllNodes** bir dizi bir anahtardır. Her bu dizinin de adlı en az bir anahtar olmalıdır bir karma tablosu öğesidir **NodeName**:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

Diğer anahtarlar her karma tablosu da ekleyebilirsiniz:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

Bir özelliği tüm düğümlere uygulanacak üyesi oluşturabilirsiniz **AllNodes** sahip dizi bir **NodeName** , `*`.
Örneğin, her düğüme vermek için bir `LogPath` özelliği, bunu yapabilirsiniz:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Bu özellik adıyla ekleme eşdeğerdir `LogPath` değerini `"C:\Logs"` her bir diğer blokları (`VM-1`, `VM-2`, ve `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>ConfigurationData hashtable tanımlama

Tanımlayabileceğiniz **ConfigurationData** herhangi bir yapılandırma (olduğu gibi önceki örneklerde) ile aynı betiği içinde bir değişken olarak veya ayrı bir `.psd1` dosyası.
Tanımlamak için **ConfigurationData** içinde bir `.psd1` dosya, yapılandırma verilerini temsil eden hashtable içeren bir dosya oluşturun.

Örneğin, adında bir dosya oluşturabilirsiniz `MyData.psd1` aşağıdaki içeriğe sahip:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Yapılandırma verilerini bir yapılandırmayla derleme

Değeri olarak yapılandırma verilerini geçirdiğiniz yapılandırma verileri için tanımladığınız bir yapılandırma derlemek için **ConfigurationData** parametresi.

Bu her giriş için bir MOF dosyası oluşturacak **AllNodes** dizi.
Her MOF dosyası adında `NodeName` karşılık gelen bir dizi girişi özelliği.

Örneğin, yapılandırma verilerini de tanımlarsanız `MyData.psd1` bir yapılandırma derleme dosyası yukarıdaki her ikisi de oluşturmak `VM-1.mof` ve `VM-2.mof` dosyaları.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Bir yapılandırma ile yapılandırma verilerini bir değişken kullanarak derleme

Aynı değişken olarak tanımlanan yapılandırma verilerini kullanmak için `.ps1` dosya yapılandırma değeri olarak değişken adını geçişi **ConfigurationData** yapılandırması derlenirken parametre:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Bir yapılandırma ile yapılandırma verilerini bir veri dosyası kullanarak derleme

.Psd1 dosyasında tanımlanan yapılandırma verilerini kullanmak için bu dosyanın adını ve yolunu değeri olarak geçirdiğiniz **ConfigurationData** yapılandırması derlenirken parametre:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Bir yapılandırmada ConfigurationData değişkenlerini kullanma

DSC yapılandırma komut dosyasında kullanılan üç özel değişkenler sağlar: **$AllNodes**, **$Node**, ve **$ConfigurationData**.

- **$AllNodes** tanımlanan düğümlerinin tüm koleksiyon başvurduğu **ConfigurationData**. Filtre uygulayabilirsiniz **AllNodes** kullanarak koleksiyon **. WHERE()** ve **. ForEach()**.
- **Düğüm** belirli bir giriş başvurduğu **AllNodes** kullanarak filtre sonra koleksiyon **. WHERE()** veya **. ForEach()**.
- **ConfigurationData** bir yapılandırma derlerken parametre olarak geçirilen tüm karma tablosuna başvuruyor.

## <a name="using-non-node-data"></a>Düğümü olmayan verileri kullanma

Önceki örneklerde anlatıldığı gibi **ConfigurationData** hashtable ek olarak gerekli bir veya daha fazla anahtarları olabilir **AllNodes** anahtarı.
Bu konudaki örneklerde, biz yalnızca tek bir ek düğüm kullanılan ve onu adlı `NonNodeData`.
Ancak, herhangi bir ek anahtar sayısını tanımlayın ve bunları istediğiniz adı.

Düğümü olmayan verileri kullanarak bir örnek için bkz: [yapılandırma ve ortam verilerin ayrılmasını](separatingEnvData.md).

## <a name="see-also"></a>Ayrıca bkz:
- [Yapılandırma verilerini seçeneklerinde kimlik bilgileri](configDataCredentials.md)
- [DSC yapılandırmaları](configurations.md)