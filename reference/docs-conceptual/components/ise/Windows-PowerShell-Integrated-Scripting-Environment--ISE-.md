---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell Tümleşik komut dosyası ortamı ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: a5fcc8c813349d0b85cc3af29047424fe787d168
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405679"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Tümleşik Komut Dosyası Ortamı (ISE)

Windows PowerShell Tümleşik komut dosyası ortamı (ISE), Windows PowerShell altyapısı ve dil için iki ana biridir. Yazabileceğiniz bunlarla çalıştırın ve test betikleri yollarla Windows PowerShell konsolunda kullanılabilir değil. ISE söz dizimi renklendirme, sekme tamamlama, IntelliSense, görsel hata ayıklama ve içerik duyarlı Yardım ekler.

ISE, komutları bir konsol bölmesinde çalıştırmanıza olanak tanır, ancak aynı anda betiğinizi ISE'ye takılabilir diğer araçlar ve kaynak kodunu görüntülemek için kullanabileceğiniz bölmeleri da destekler. Diğer betikleri ya da modül içinde tanımlanan işlevleri kullanan bir komut dosyası hata ayıklaması yapıyorsanız, özellikle yararlı olan aynı anda birden çok betik Windows'u bile açabilirsiniz.

## <a name="whats-new"></a>Yenilikler

En son sürümlerde PowerShell ISE eklenen özelliklerden bazıları aşağıda verilmiştir.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>PowerShell 3.0 (Windows Server 2012, Windows 8) eklendi

**IntelliSense** menüleri eşleşen cmdlet'leri, parametreleri, parametre değerleri, dosyaları veya klasörleri siz yazarken göstererek Komutlarınızın otomatik olarak tamamlar.

**Kod parçacıkları** kısa bölümler kod yazma, komut dosyalarına kolayca ekleyebilirsiniz. Faydalı kod parçacıkları koleksiyonu kutuya eklenir ve daha kullanarak yapabilirsiniz **yeni kod parçacığı** cmdlet'i.

**Eklenti Araçları** eklemek ISE Özellikleri ile etkileşime giren yazma kod tarafından oluşturulabilir [Windows PowerShell ISE betik oluşturma nesne modeli](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Bu araçlar, sekmeli bir bölmeye denetimlerini görüntülemek veya arka planda görünmez şekilde çalışır. **Komutları** eklenti iyi bir örnektir ve sürüm 3.0 ile bulunur ve daha sonra kullanılabilir komutları ve bunların Yardım listesini görüntüler.

**Yöneticisi ve Otomatik Kaydet yeniden** otomatik olarak bir kilitlenme veya beklenmeyen bir yeniden başlatma durumunda İş kaybını önlemek için her iki dakikada betiklerinizi kaydedin.

**En son kullanılan liste** Dosya Aç menüsünde en sık kullandığınız dosyaları almak daha kolay hale getirmek için artık parçasıdır.

**Birleştirilmiş bir konsol bölmesinde**. ISE önceki sürümlerinde ayrı komut ve çıkış bölmeleri vardı. Bunlar tek bir bölmesine daha doğrudan taklit eder, Windows Powershell konsolunda gördüğünüz birleştirildi.

**Komut satırı anahtarları**. Birkaç yeni komut satırı anahtarları ISE çalıştığı yolu üzerinde daha fazla denetim verir. -NoProfile profili betiği çalıştırmadan işe başlar. -Help ISE ile bir Yardım penceresini açar. -mta "çok iş parçacıklı bölme modunda" işe başlar. Tek iş parçacıklı varsayılandır.

**Yeni Düzenleyici Özellikleri** oluşturmak ve kodunuzun okumak kolaylaştırır:

- **XML sözdizimi renklendirme**. Windows PowerShell kod söz dizimi renkleri gibi ISE Düzenleyici artık aynı şekilde XML sözdizimi renkleri.

- **Ayraç eşleştirme**. Kapatma küme ayraçlarını açılış eşleşecek şekilde doğru sayısını sahip olmanıza yardımcı olmak için eşleşen küme ayraçlarını ISEWindows PowerShell ISE vurgular hizmetlerdir. CTRL - kullanma\[ imlecin bulunduğu açılış ayracından eşleşen kapanış ayracı bulunacak.

- **Anahat görünümü**. Daraltabilir veya artı işaretine tıklayarak ve eksi işaretlerine sol kenar boşluğunda, kod bölümlerini genişletin. Bu, uzun bir betikte aradığınız kodu bulmak kolaylaştırır.

- **Sürükle ve bırak metin düzenlemesini**. Metin bloğu seçin ve taşımak için başka bir konuma sürükleyin. Seçili metnin yerine kopyalama sürüklerken Ctrl tuşunu basılı tutun taşıyın.

- **Hata ekranı ayrıştırma**. Siz yazarken, Windows PowerShell komut dosyanızı inceler. Bir hata algılarsa bir kırmızı dalgalı sorunlu kod altında gösterilir. Belirtilen hata geldiğinizde, araç ipucu bulundu sorunu gösterir.

- **Yakınlaştırma**. Metninizi okumayı veya ISE penceresi sağ alt köşesinde bulunan kaydırıcıyı kullanarak büyük resmi görmek için daha kolay hale getirmek için yakınlaştırabilirsiniz.

- **Zengin Metin Kopyala ve Yapıştır**. Pano, yazı tipi, boyut ve renk bilgilerini seçili metnin ISE'den kopyaladığınızda dahil edilir.

- **Blok seçimi**. Betik bölmesindeki farenizi metin seçim sırasında ALT tuşunu basılı tutarak veya tuşuna basarak metin bloğu şeklinde bir öbek seçebilirsiniz **Alt + SHIFT + ok**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>PowerShell 2.0 (Windows Server 2008 R2, Windows 7) eklendi

ISE PowerShell v2.0 sunulmuştur.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Windows PowerShell ISE çalıştırmak için gereksinimler

ISE sonraki veya Windows PowerShell v2.0 çalıştırabilirsiniz herhangi bir Windows bilgisayarda kullanılabilir. Windows PowerShell ve ISE bir sürümünü her Windows ve Windows Server sürümünü içerir, ancak en son kullanılabilir Windows Management Framework (WMF) yükleyerek yükseltebilirsiniz. Bkz: [WMF](/powershell/wmf) daha fazla bilgi için belgelere bakın.

> [!NOTE]
> Windows PowerShell ISE'de bir grafik kullanıcı arabirimi gerektirdiğinden, Windows Server'ın Sunucu Çekirdeği seçeneğini üzerinde çalıştırılamaz.

## <a name="see-also"></a>Ayrıca bkz:

[Windows power shell ISE betik oluşturma nesne modelinin amacı](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)