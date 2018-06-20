---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell komut dosyası
ms.openlocfilehash: 7de5a3f3149d8d464b34101d94a5f9430d9b0f23
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222409"
---
# <a name="powershell"></a>PowerShell

.NET Framework üzerine oluşturulan bir görev tabanlı komut satırı kabuğu ve betik dilidir powershell'dir; Sistem yöneticileri ve güç-kullanıcılar, hızlı bir şekilde birden çok işletim sistemleri (Linux, macOS, UNIX ve Windows) ve bu işletim sisteminde çalışan uygulamaları ile ilgili işlemleri yönetimini otomatikleştirmek özel olarak tasarlanmıştır.

## <a name="powershell-is-open-source"></a>Açık kaynak Powershell'dir.

PowerShell temel kaynak kodu github'da kullanılabilir ve topluluk katkılarına açık sunulmuştur. Bkz: [github'da PowerShell kaynağı](https://github.com/powershell/powershell).

Gereksinim duyduğunuz adresindeki bitle başlatabilirsiniz [PowerShell get](https://github.com/PowerShell/PowerShell#get-powershell).
Veya, belki de hızlı bir tur [Başlarken](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>PowerShell tasarım hedefleri
Windows PowerShell komut satırı ve komut dosyası ortamı artırmanın uzun süredir bilinen sorunlar ortadan kaldırılır ve yeni özellikler ekleyerek iyileştirmek için tasarlanmıştır.

### <a name="discoverability"></a>Bulunabilirliği
Windows PowerShell özelliklerini Bul kolay hale getirir. Örneğin, görüntüle ve Değiştir Windows Hizmetleri cmdlet'lerinin listesini bulmak için şunu yazın:

```powershell
Get-Command *-Service
```

Hangi cmdlet'i bir görevi gerçekleştirir öğrendiğinizde Get-Help cmdlet'ini kullanarak cmdlet hakkında daha fazla bilgi edinebilirsiniz. Örneğin, Get-Service cmdlet'i hakkında Yardım görüntülemek için şunu yazın:

```powershell
Get-Help Get-Service
```
Çoğu cmdlet'leri yönetilebilir ve görüntülemek için metne çizilir nesneleri yayma. Bu cmdlet'in çıktısı, tam olarak anlamak için kendi çıktı Get-üye cmdlet'i için kanal oluşturun. Örneğin, aşağıdaki komut, Get-Service cmdlet tarafından nesne çıktısını üyeleri hakkında bilgi görüntüler.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Tutarlılık
Sistemleri yönetme karmaşık bir çaba olabilir ve tutarlı bir arayüz olan araçlarını devralınmış karmaşıklık denetlemek için yardımcı olur. Ne yazık ki, komut satırı araçları ne kodlanabilir COM nesneleri için kendi tutarlılık bilinmektedir.

Windows PowerShell tutarlılığını birincil varlıklarını biridir. Örneğin, Sort-Object cmdlet'i kullanmayı öğrenin, herhangi bir cmdlet'in çıkışını sıralamak için bu bilgi kullanabilirsiniz. Her cmdlet'in farklı sıralama yordamları öğrenin gerekmez.

Ayrıca, cmdlet geliştiricilerin kendi cmdlet'leri için sıralama özellikleri tasarım gerekmez. Windows PowerShell bunları temel özellikleri sağlar ve bunları arabirimi birçok yönleri hakkında tutarlı olacak şekilde zorlar bir çerçeve sağlar. Framework bazı geliştiriciler için genellikle sol seçimleri ortadan kaldırır, ancak buna karşılık, güçlü ve kullanımı kolay cmdlet'leri geliştirme daha kolay kolaylaştırır.

### <a name="interactive-and-scripting-environments"></a>Etkileşimli ve komut dosyası ortamlar
Windows PowerShell komut satırı araçları ve COM nesnelerine erişim verir ve ayrıca, .NET Framework Sınıf Kitaplığı'nı (FCL) güç kullanmanıza olanak sağlar birleştirilmiş etkileşimli ve komut dosyası ortamıdır.

Bu ortamın üzerine Windows birden çok komut satırı araçları ile etkileşimli bir ortam sağlayan komut, artırır. İzin veren Windows Komut Dosyası Sistemi'ni (WSH) komut dosyaları de geliştirir birden çok komut satırı araçları ve COM Otomasyon nesneleri kullanır, ancak etkileşimli bir ortam sağlamak değildir.

Bu özelliklerin tümü, erişimi birleştirerek, Windows PowerShell etkileşimli kullanıcı ve komut dosyası yazan yeteneklerini genişletir ve sistem yönetimini daha kolay yönetilebilir hale getirir.

### <a name="object-orientation"></a>Nesne yönü
Metinde komutları yazarak Windows PowerShell ile etkileşim karşın, Windows PowerShell nesnelerde, metin değil temel alır. Bir komutun çıktısını bir nesnedir. Çıkış nesnesi başka bir komuta kendi giriş gönderebilirsiniz. Sonuç olarak, Windows PowerShell yeni ve güçlü bir komut satırı kip tanıtırken diğer Kabukları ile karşılaştı kişilere bilinen bir arayüz sağlar. Metin yerine nesneleri göndermek için etkinleştirerek komutları arasında veri gönderme kavramını genişletmektedir.

### <a name="easy-transition-to-scripting"></a>Komut dosyası için kolay geçiş
Yazmasını geçiş kolay, etkileşimli olarak çok komut dosyası oluşturma ve çalıştırma komutları Windows PowerShell yapar. Bir görevi gerçekleştirmek komutları bulmak için Windows PowerShell komut isteminde komutları yazabilirsiniz. Sonra bunları bir komut dosyası olarak kullanmak için bir dosya için kopyalamadan önce bir dökümü veya bir geçmiş komutlarda kaydedebilirsiniz.
