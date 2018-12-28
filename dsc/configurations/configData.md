---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma verilerini kullanma
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405740"
---
# <a name="using-configuration-data-in-dsc"></a>DSC yapılandırma verilerini kullanma

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Yerleşik DSC kullanarak **ConfigurationData** parametresi bir yapılandırması içinde kullanılabilir verileri tanımlayabilirsiniz.
Bu farklı ortamlar için veya birden çok düğüm için kullanılabilecek tek bir yapılandırma oluşturmanızı sağlar.
Örneğin, bir uygulama geliştiriyorsanız geliştirme ve üretim ortamları için bir yapılandırma kullanma ve yapılandırma verilerini, her ortam için verileri belirtmek için kullanın.

Bu konuda yapısını açıklayan **ConfigurationData** karma tablo.
Yapılandırma verilerini kullanma örnekleri için bkz. [yapılandırma ve ortam verilerini ayırma](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>ConfigurationData ortak parametresi

DSC yapılandırması ortak bir parametre alır **ConfigurationData**, yapılandırmayı derleme yaptığınızda belirtin.
Derleme yapılandırmaları hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md).

**ConfigurationData** parametredir adlı en az bir anahtar olması gerektiğini bir hashtable **AllNodes**.
Bir veya daha fazla diğer anahtarlar da olabilir.

> [!NOTE]
> Bu konudaki örnekler tek bir ek anahtar kullanır (adlandırılmış dışında **AllNodes** anahtarı) adlı `NonNodeData`, ancak herhangi bir sayıda ek anahtarlar eklemek ve bunları istediğiniz adı.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

Değerini **AllNodes** dizi anahtardır. Bu dizinin her öğesinin de en az bir anahtar adında gereken bir karma tablodur **NodeName**:

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

Bir özelliği tüm düğümlere uygulanacak bir üye oluşturabilirsiniz **AllNodes** sahip dizi bir **NodeName** , `*`.
Örneğin, her düğüm vermek için bir `LogPath` özelliği, bunu yapabilirsiniz:

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

Bu özellik adıyla ekleme eşdeğerdir `LogPath` değeriyle `"C:\Logs"` her birine diğer bloklardan (`VM-1`, `VM-2`, ve `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>ConfigurationData hashtable tanımlama

Tanımlayabileceğiniz **ConfigurationData** olarak aynı betiği yapılandırması (olduğu gibi önceki örneklerimizde) içinde bir değişken veya ayrı bir `.psd1` dosya.
Tanımlamak için **ConfigurationData** içinde bir `.psd1` dosya, yapılandırma verilerini temsil eden karma tablosu içeren bir dosya oluşturun.

Örneğin, adında bir dosya oluşturabilirsiniz `MyData.psd1` aşağıdaki içeriklerle:

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

## <a name="compiling-a-configuration-with-configuration-data"></a>Yapılandırma verilerini içeren bir yapılandırma derleme

Yapılandırma verilerini, tanımladığınız bir yapılandırmayı derlemek için yapılandırma verilerini değeri olarak geçirirsiniz **ConfigurationData** parametresi.

Bu her giriş için bir MOF dosyası oluşturacak **AllNodes** dizisi.
Her bir MOF dosyası adında `NodeName` karşılık gelen bir dizi giriş özelliği.

Örneğin, yapılandırma verilerini olarak tanımlarsanız `MyData.psd1` yapılandırma derleme dosyası yukarıdaki oluşturulacak hem de `VM-1.mof` ve `VM-2.mof` dosyaları.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Bir değişken kullanarak yapılandırma verilerini bir yapılandırma derleme

Aynı bir değişken olarak tanımlanan yapılandırma verilerini kullanmak için `.ps1` dosya yapılandırma, değeri olarak değişken adını geçişi **ConfigurationData** yapılandırması derlenirken parametresi:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Bir veri dosyası kullanarak yapılandırma verilerini bir yapılandırma derleme

.Psd1 dosyasında tanımlanan yapılandırma verilerini kullanmak için bu dosyanın adını ve yolunu değeri olarak geçirdiğiniz **ConfigurationData** yapılandırması derlenirken parametresi:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Bir yapılandırmada ConfigurationData değişkenleri kullanma

DSC yapılandırma komut dosyasında kullanılabilen aşağıdaki özel değişkenler sağlar:

- **$AllNodes** tüm koleksiyon içinde tanımlanan düğümlerinin başvurduğu **ConfigurationData**. Filtre uygulayabilirsiniz **AllNodes** kullanarak koleksiyon **. Birlikte WHERE()** ve **. ForEach()**.
- **ConfigurationData** bir yapılandırması derlenirken parametre olarak geçirilen tüm karma tablosuna başvuruyor.
- **MyTypeName** içeren [yapılandırma](configurations.md) adı değişkeni kullanılır. Örneğin, yapılandırmada `MyDscConfiguration`, `$MyTypeName` değerine sahip `MyDscConfiguration`.
- **Düğüm** belirli bir giriş başvurduğu **AllNodes** kullanarak filtrelenmiştir sonra koleksiyonu **. Birlikte WHERE()** veya **. ForEach()**.
  - Daha fazla bilgi bu yöntemleri hakkında [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

## <a name="using-non-node-data"></a>Düğümü olmayan verileri kullanma

Önceki örneklerde anlatıldığı gibi **ConfigurationData** hashtable ek olarak gerekli bir veya daha fazla anahtar sağlayabilirsiniz **AllNodes** anahtarı.
Bu konudaki örneklerde, biz yalnızca tek bir ek düğüm kullanılan ve ona `NonNodeData`.
Ancak, herhangi bir sayıda ek anahtarlar tanımlayın ve bunları istediğiniz adı.

Düğümü olmayan verileri kullanan bir örnek için bkz: [yapılandırma ve ortam verilerini ayırma](separatingEnvData.md).

## <a name="see-also"></a>Ayrıca bkz:

- [Yapılandırma verilerinde kimlik bilgisi seçeneklerinden](configDataCredentials.md)
- [DSC yapılandırmaları](configurations.md)