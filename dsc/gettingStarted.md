---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: İstenen durum yapılandırması PowerShell ile çalışmaya başlama
ms.openlocfilehash: b5aff5008db5a5e45b77d8094b0e48ad98dc63fa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a>İstenen durum yapılandırması PowerShell ile çalışmaya başlama #

Bu kılavuz, PowerShell istenen durum yapılandırması belgeleri oluşturmaya başlamak ve makinelere Uygula açıklar. PowerShell cmdlet'leri, modüller ve işlevleri temel olarak bilindiğini varsayar.


## <a name="create-a-configuration"></a>Bir yapılandırma oluşturmak ##

[**Yapılandırmaları** ](https://msdn.microsoft.com/powershell/dsc/configurations) bir ortam açıklamak belgelerdir. Ortamlar oluşur "**düğümleri**", olan yaygın olarak sanal veya fiziksel makineler.

Yapılandırmaları çeşitli formlarını gelebilir. Yeni bir yapılandırma oluşturmak için en kolay yolu, bir .ps1 (PowerShell) betiği oluşturmaktır. Bunu yapmak için tercih düzenleyicide açın. DSC yerel anladığı beri PowerShell ISE olduğunda iyi bir seçimdir. Aşağıdaki PS1 Kaydet:

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a>Bir yapılandırma bölümlerini ##
**Yapılandırma** PowerShell 4.0 eklenen bir anahtar sözcüktür. İstenen durum yapılandırması tarafından kullanılan PowerShell işlevi özel bir tür belirtir. Bu örnekte, işlev myFirstConfiguration olarak adlandırılır.

Sonraki satıra bir modülü içeri aktarmaya benzer bir içeri aktarma ifadesi olur. Daha sonra incelenecektir.

Bu yapılandırma üzerinde görecek makine adı "Düğümü" tanımlar. Bu yapılandırma yerel olarak düzenlenen rağmen yapılandırmaları uzak düğümlerine ulaşmak ve bunları yapılandırabilirsiniz.

Düğümler, makine adı veya IP adresleri olabilir. Birden çok düğüm tek yapılandırma belgede olabilir. Kullanarak [yapılandırma verilerini](https://msdn.microsoft.com/powershell/dsc/configdata), birden çok düğümlerine uygulamak aynı yapılandırmaya sahip olabilir. Bu durumda, "yerel bilgisayarda anlamı localhost" - düğümdür.

Sonraki öğe bir [ **kaynak**](https://msdn.microsoft.com/powershell/dsc/resources). Kaynaklar, yapılandırmaları yapı taşlarıdır. Her kaynak makinenin tek bir boyut uygulama mantığını tanımlayan bir modüldür. Her kaynak makinenize çalıştırarak görüntüleyebileceğiniz **Get-DscResource** PowerShell'de. Kaynaklar yerel makinede mevcut olması gerekir ve bir yapılandırmasında kullanılmadan önce içeri **alma DscResource** bu yapılandırma ikinci satırda olduğu.

**Bir yapılandırma ederek ilerlemesini kabul ederek**

Yukarıdaki komut dosyasını çalıştırın ve kaydedilir, hiçbir çıkış oluşturulur. Yalnızca bir işlevi bir yapılandırma olduğundan ve yukarıdaki betik işlevi tanımlanmış ancak çalışmıyor henüz bunu budur. İşlev tanımlandıktan sonra çağrılan gerekir:
```powershell
myFirstConfiguration
```

Çalıştırıldığında, yapılandırma işlevleri yapılandırmasını doğrulama geçerli değil. Sözdizimi hatası olmalıdır, kaynakları tanımlanan tüm zorunlu parametreler olmalıdır ve çalışmaya başlamadan önce tüm kaynakların aktarılmalıdır.

Yapılandırma yürütüldükten sonra içeren yapılandırma adı ile bir klasör oluşturur bir **. MOF dosyası** yapılandırma kümedeki her düğüm için. . MOF dosyasını ağ üzerinden iletişim kurmak için PowerShell DSC tarafından kullanılan Yönetimi standartlara dayalı bir biçimidir.

Yapılandırma yürürlüğe için:
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
Bu yapılandırma düğümlerin ulaşana ve bunları yapılandırır bir PowerShell iş oluşturur. İş çıkışını görmek için kullanın - bekleyin.
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```