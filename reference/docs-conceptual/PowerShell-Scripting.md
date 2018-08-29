---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: PowerShell betik oluşturma
ms.openlocfilehash: 754805148dc815a12c5c77e4894fb598c6927f7e
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134002"
---
# <a name="powershell"></a>PowerShell

Bir görev tabanlı komut satırı kabuğu ve betik dilidir .NET Framework üzerine inşa edilmiş powershell'dir.
PowerShell, sistem yöneticileri yardımcı olur ve ileri kullanıcılar (Linux, macOS ve Windows) işletim sistemleri ve işlemleri yönetme görevleri hızlı bir şekilde otomatik hale getirebilirsiniz.

PowerShell komutları, komut satırından bilgisayarları yönetmenizi sağlar. PowerShell sağlayıcıları, kayıt defteri gibi veri depolarında erişmek ve sertifika deposunu, dosya sistemine erişmelerini olarak kolayca belirlemenizi sağlar. PowerShell, kapsamlı bir ifade ayrıştırıcısı ve tam olarak geliştirilen bir betik dilini içerir.

## <a name="powershell-is-open-source"></a>PowerShell açık kaynak

PowerShell temel kaynak kodu github'da kullanılabilir ve topluluk Katkıları için açık sunulmuştur.
Bkz: [PowerShell GitHub üzerinde kaynak](https://github.com/powershell/powershell).

Gereksinim duyduğunuz, BITS ile başlayabilirsiniz [alma PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Veya belki de hızlı bir tura ile [Başlarken](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>PowerShell tasarım hedefleri

PowerShell, komut satırı ve betik ortamı değindiği sorunlarını ortadan kaldırılır ve yeni özellikler ekleyerek iyileştirmek için tasarlanmıştır.

### <a name="discoverability"></a>Bulunabilirlik

PowerShell özellikleri bulmak daha kolay hale getirir. Örneğin, görüntüle ve Değiştir Windows Hizmetleri cmdlet'lerinin listesini bulmak için şunu yazın:

```powershell
Get-Command *-Service
```

Hangi cmdlet'i bir görev gerçekleştirir keşfetme sonra cmdlet'i hakkında daha fazla kullanarak öğrenebilirsiniz `Get-Help` cmdlet'i. Örneğin, hakkında Yardım görüntülemek için `Get-Service` cmdlet'i, türü:

```powershell
Get-Help Get-Service
```

Yönetilen ve ardından görüntülemek için metin olarak işlenen çoğu cmdlet'leri dönüş nesneleri. Bir cmdlet'in çıktısı, tam olarak anlamak için çıktı için kanal `Get-Member` cmdlet'i. Örneğin, aşağıdaki komut nesnesi çıktı tarafından üyeleri hakkında bilgi görüntüler `Get-Service` cmdlet'i.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Tutarlılık

Sistemlerini yönetmeye, karmaşık bir görev olabilir. Tutarlı bir arabirimi olan araçlar, devralınan karmaşıklığı denetlemek için yardımcı olur. Ne yazık ki, komut satırı araçları ve kodlanabilir COM nesneleri için kendi tutarlılık bilinen değildir.

PowerShell tutarlılığını birincil varlıklarını biridir. Örneğin nasıl kullanacağınızı öğrenin, `Sort-Object` cmdlet'i, herhangi bir cmdlet'in çıkışını sıralamak için bu bilgi kullanabilirsiniz. Farklı bir sıralama yordamları her cmdlet'in öğrenmeniz gerekmez.

Ayrıca, cmdlet geliştiriciler kendi cmdlet'leri için sıralama özellikleri tasarım gerekmez. PowerShell, tutarlılık zorlayan temel özelliklere sahip bir çerçeve sağlar. Framework, geliştiriciler için sol bazı seçenekler ortadan kaldırır. Ancak, cmdlet'leri geliştirilmesini çok daha kolay kolaylaştırır.

### <a name="interactive-and-scripting-environments"></a>Etkileşimli ve komut dosyası ortamlar

Windows komut istemi, etkileşimli bir kabuk komut satırı araçları ve temel betik erişmesini sağlar. Windows betik sistemi (WSH) kodlanabilir komut satırı araçları ve COM Otomasyon nesneleri var, ancak etkileşimli bir kabuk sağlamaz.

PowerShell, etkileşimli bir kabuk ve komut dosyası ortamı birleştirir. PowerShell komut satırı araçları, COM nesnelerini ve .NET sınıf kitaplıkları erişebilirsiniz. Bu özellik bileşimi etkileşimli kullanıcı, betik yazarı ve Sistem Yöneticisi yeteneklerini genişletir.

### <a name="object-orientation"></a>Nesne yönü

PowerShell değil metin nesnesinde temel alır. Komutun çıkışını bir nesnedir. İşlem hattı aracılığıyla çıkış nesnesi giriş olarak başka bir komut gönderebilirsiniz.

Bu işlem hattı ile diğer Kabukları deneyimli kişiler için tanıdık bir arabirim sağlar. PowerShell, metin yerine nesneleri göndererek bu kavramı genişletir.

### <a name="easy-transition-to-scripting"></a>Komut dosyası için kolay geçiş

Oluşturma ve çalıştırma komut dosyaları yazmalarını geçiş kolay, etkileşimli olarak çok komutları PowerShell'in komut bulunabilirliği yapar. PowerShell dökümleri ve geçmişi, komutları bir komut dosyası olarak kullanılmak üzere bir dosya kopyalamak kolaylaştırır.
