---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell Tümleşik komut dosyası ortamı ISE"
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 66f36371cbb8ad8523aa1e1e3cd791cc692194c9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Tümleşik Komut Dosyası Ortamı (ISE)
Windows PowerShell Tümleşik komut dosyası ortamı (ISE) Windows PowerShell altyapısı ve dil için iki ana biridir. Onunla yazabileceğiniz, çalıştırma ve komut dosyaları Windows PowerShell konsolunda kullanılabilir olmayan yollarla test etme. ISE söz dizimi renklendirme, sekme tamamlama, IntelliSense, visual hata ayıklama ve bağlama duyarlı Yardım ekler.

Konsol bölmesinde komutları çalıştırmak işe sağlar, ancak aynı anda komut dosyanızı ve işe takın başka araçlar kaynak kodunu görüntülemek için kullanabileceğiniz bölmeleri de destekler. Diğer komut veya modülleri tanımlı işlevlerini kullanan bir komut dosyası hata ayıklama sırasında özellikle yardımcı olan aynı anda birden çok komut dosyası windows Kurulumu bile açabilirsiniz.

## <a name="whats-new"></a>Yenilikler
En son sürümlerde PowerShell ISE eklenen özelliklerden bazıları aşağıda verilmiştir.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>PowerShell 3.0 (Windows Server 2012, Windows 8) eklendi
**IntelliSense** yazarken eşleşen cmdlet'leri, parametreleri, parametre değerlerini, dosya veya klasörleri menüleri görüntüleyerek komutlarınızı otomatik olarak tamamlar.

**Kod parçacıkları** kısa bölümler kod, yazma komut dosyalarına kolayca ekleyebilirsiniz. Yararlı parçacıkları koleksiyonu kutusuna eklenir ve daha kullanarak yapabilirsiniz **yeni kod parçacığında** cmdlet'i.

**Eklenti Araçları** eklemek işe özellikleri ile etkileşime giren yazma kodu tarafından oluşturulabilir [Windows PowerShell ISE komut dosyası nesne modeli](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md). Bu araçları denetimleri sekmeli bölmede görüntüleyebilir veya görünmez arka planda çalışır. **Komutları** eklenti iyi bir örnektir ve sürüm 3.0 bulunur ve daha sonra kullanılabilir komutlar ve kendilerine Yardım listesini görüntüler.

**Yöneticisi ve otomatik kayıt yeniden** otomatik olarak komut dosyalarınızı her iki dakikada bir kilitlenme veya beklenmeyen bir yeniden başlatma durumunda iş kaybı önlemenize yardımcı kaydedin.

**En kısa süre önce kullanılan liste** en sık kullandığınız dosyaları almak daha kolay hale getirmek için Dosya Aç menüsünde artık parçasıdır.

**Birleştirilmiş Konsol bölmesinde**. ISE önceki sürümlerinde ayrı komut ve çıktı bölmeleri vardı. Bunlar tek bir bölmesine daha doğrudan taklit eder, Windows Powershell konsolunda gördüğünüz birleştirildi.

**Komut satırı anahtarları**. Birkaç yeni komut satırı anahtarları hakkında daha fazla denetime işe çalışma şeklini verin. -NoProfile bir profil betiği çalıştırmadan işe başlatır. -Help ISE ile Yardım penceresini açar. -mta "birden çok iş parçacıklı modunda" ISE başlatır. Tek iş parçacıklı varsayılandır.

**Yeni Düzenleyicisi özellikleri** oluşturmak ve kodunuzu okuma kolaylaştırır:

- **XML sözdizimi renklendirmesi**. Windows PowerShell kodu sözdizimi renkleri gibi işe Düzenleyicisi'ni aynı şekilde şimdi XML sözdizimi renkleri.

- **Ayraç eşleştirme**. Açılış eşleşecek şekilde küme ayraçları kapatma sağ sayısı sahip olmanıza yardımcı olması için eşleşen küme parantezleri ISEWindows PowerShell ISE vurgular olanları. CTRL - kullanın\[ imlecin bulunduğu açılan parantez eşleşen kapanış ayracı bulunamadı.

- **Anahat görünümü**. Daraltma veya tıklatarak artı ve eksi işaretlerine sol kenar boşluğunda kodunuzu bölümleri genişletin. Bu, uzun bir komut dosyası aradığınız kod bulmayı kolaylaştırır.

- **Sürükle ve bırak metin düzenleme**. Bir metin bloğunu seçin ve taşımak için başka bir konuma sürükleyin. Ctrl tuşunu basılı tutarak yerine kopyalama seçili metni sürükleyin taşıyın.

- **Hata ekranı ayrıştırma**. Siz yazarken Windows PowerShell komut dosyanızı inceler. Bir hata tespit ederse, sorunlu kodu altında kırmızı dalgalı gösterir. Belirtilen hata geldiğinizde, bir araç ipucunu bulundu sorunu gösterir.

- **Yakınlaştırma**. Okuma veya işe penceresinin sağ alt köşesinde kaydırıcıyı kullanarak büyük resmi görmek için Uzaklaştır kolaylaştırmak için metin yakınlaştırabilirsiniz.

- **Zengin Metin Kopyala ve Yapıştır**. Pano, yazı tipi, boyut ve renk bilgilerini seçili metnin işe kopyaladığınızda dahil edilir.

- **Blok Seçi**. Metin bloğu şeklinde bir öbek basarak veya betik bölmesine fareyi metin seçerken ALT tuşunu basılı tutarak seçebilirsiniz **Alt + üst karakter + ok**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>PowerShell 2.0 (Windows Server 2008 R2, Windows 7) eklendi
ISE PowerShell v2.0 sunulmuştur.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Windows PowerShell ISE çalıştırmak için gereksinimler
İŞE Windows PowerShell v2.0 çalıştırabilirsiniz herhangi bir Windows bilgisayarda veya sonraki sürümlerinde kullanılabilir.
Her sürümü Windows ve Windows Server, Windows PowerShell ISE ve bir sürümünü içerir, ancak en son kullanılabilir Windows Management Framework yükleyerek yükseltebilirsiniz.
En son sürümünü bulmak için bu Ara'yı çalıştırın: [indirmeleri](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending).
"Önizleme" etiketli herhangi bir giriş yayın öncesi kodu ve özellik tam olmayan unutmayın.

> [!NOTE]
> Windows PowerShell ISE bir grafik kullanıcı arabirimi gerektirdiğinden, Windows Server'ın Sunucu Çekirdeği seçeneğini üzerinde çalıştırılamaz.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell Tümleşik komut dosyası ortamı'nı kullanma](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

