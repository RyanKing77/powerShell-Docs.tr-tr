---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell betik oluşturma
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094060"
---
# <a name="powershell"></a>PowerShell

PowerShell, .NET Framework üzerine oluşturulan bir görev tabanlı komut satırı kabuğu ve betik dilidir olur; Sistem yöneticileri ve ileri kullanıcılar, hızlı bir şekilde birden çok işletim sistemi (Linux, macOS, UNIX ve Windows) ve bu işletim sistemlerinde çalışan uygulamalar için ilgili işlemlerin yönetimini otomatik hale getirmek için özel olarak tasarlanmıştır.

## <a name="powershell-is-open-source"></a>PowerShell açık kaynaktır

PowerShell temel kaynak kodu github'da kullanılabilir ve topluluk Katkıları için açık sunulmuştur.
Bkz: [PowerShell GitHub üzerinde kaynak](https://github.com/powershell/powershell).

Gereksinim duyduğunuz, BITS ile başlayabilirsiniz [alma PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Veya belki de hızlı bir tura ile [kullanmaya başlama](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>PowerShell tasarım hedefleri
PowerShell, komut satırı ve betik ortamı değindiği sorunlarını ortadan kaldırılır ve yeni özellikler ekleyerek iyileştirmek için tasarlanmıştır.

### <a name="discoverability"></a>Bulunabilirlik
PowerShell özellikleri bulmak daha kolay hale getirir. Örneğin, görüntüle ve Değiştir Windows Hizmetleri cmdlet'lerinin listesini bulmak için şunu yazın:

```powershell
Get-Command *-Service
```

Hangi cmdlet'i bir görev gerçekleştirir keşfetme sonra cmdlet'i hakkında daha fazla kullanarak öğrenebilirsiniz `Get-Help` cmdlet'i.
Örneğin, hakkında Yardım görüntülemek için `Get-Service` cmdlet'i, türü:

```powershell
Get-Help Get-Service
```
Çoğu cmdlet, yönetilebilir ve ardından metin görüntülemek için işlenen nesneleri gösterin.
Bu cmdlet'in çıktısı, tam olarak anlamak için kendi çıktı için kanal `Get-Member` cmdlet'i.
Örneğin, aşağıdaki komut nesnesi çıktı tarafından üyeleri hakkında bilgi görüntüler `Get-Service` cmdlet'i.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Tutarlılık
Sistemlerini yönetmeyi karmaşık bir çaba olabilir ve tutarlı bir arabirim üzerinden erişir Araçlar'ın devralınmış karmaşıklığı denetlemek için yardımcı olur.
Ne yazık ki, komut satırı araçları ne kodlanabilir COM nesneleri için kendi tutarlılık bilinmektedir.

PowerShell tutarlılığını birincil varlıklarını biridir.
Örneğin nasıl kullanacağınızı öğrenin, `Sort-Object` cmdlet'i, herhangi bir cmdlet'in çıkışını sıralamak için bu bilgi kullanabilirsiniz.
Farklı bir sıralama yordamları her cmdlet'in öğrenmek zorunda değildir.

Ayrıca, cmdlet geliştiriciler kendi cmdlet'leri için sıralama özellikleri tasarım gerekmez.
PowerShell, bunları temel özellikleri sağlar ve bunları pek çok arabirimi yönleri hakkında tutarlı olmasını zorlar bir çerçeve sunar.
Framework bazı geliştiriciler için genellikle bırakılan seçeneklerin ortadan kaldırır, ancak buna karşılık, güçlü ve kullanımı kolay cmdlet'lerini geliştirmeyi çok daha kolay kolaylaştırır.

### <a name="interactive-and-scripting-environments"></a>Etkileşimli ve komut dosyası ortamlar
PowerShell komut satırı araçları ve COM nesneleri için erişmenizi ve ayrıca güç, .NET Framework Sınıf Kitaplığı'nı (FCL) kullanmanıza olanak sağlayan bir birleşik etkileşimli ve komut dosyası ortamıdır.

Bu ortama bağlı Windows komut birden fazla komut satırı araçlarıyla etkileşimli bir ortam sağlayan istemi artırır.
Olanak veren Windows komut dosyası sistemi (WSH) betikleri da artırır birden çok komut satırı araçları ve COM Otomasyon nesneleri kullanabilirsiniz, ancak etkileşimli bir ortam sağlamaz.

Bu özelliklerin tümü, erişim birleştirerek, PowerShell etkileşimli kullanıcı ve komut dosyası yazan yeteneklerini genişletir ve sistem yönetimini daha kolay yönetilebilir hale getirir.

### <a name="object-orientation"></a>Nesne yönü
PowerShell ile metinde komutları yazarak etkileşim olsa da, PowerShell metin olmayan nesneler üzerinde temel alır.
Komutun çıkışını bir nesnedir.
Başka bir komuta çıkış nesnesi, giriş olarak gönderebilir.
Sonuç olarak, PowerShell, yeni ve güçlü bir komut satırı paradigma tanıtırken diğer Kabuk ile karşılaşmış kişilere tanıdık bir arabirim sağlar.
Metin yerine, nesneleri göndermek için yoluyla komutları arasında veri gönderme kavramı genişletir.

### <a name="easy-transition-to-scripting"></a>Komut dosyası için kolay geçiş
Oluşturma ve çalıştırma komut dosyaları yazmalarını geçiş kolay, etkileşimli olarak çok komutları PowerShell yapar.
Bir görev gerçekleştiren komutları bulmak için PowerShell komut isteminde komutları yazabilirsiniz.
Ardından, bunları bir dosyaya bir komut dosyası olarak kullanılmak üzere kopyalamadan önce bir döküm veya bir geçmiş komutlarda kaydedebilirsiniz.
