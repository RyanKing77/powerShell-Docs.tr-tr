---
ms.date: 09/06/2019
keywords: PowerShell, cmdlet
title: PowerShell 5,0 ıSE 'deki yenilikler
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746214"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Windows PowerShell 5,0 ıSE 'deki yenilikler

Bu konuda, Windows PowerShell Tümleşik komut dosyası ortamı (ıSE) sürümlerinde sunulan yeni ve güncelleştirilmiş özellikler açıklanmaktadır.

## <a name="feature-description"></a>Özellik açıklaması

Windows PowerShell ISE, bir grafik ve sezgisel bir ortamda betikleri ve modülleri yazmanızı, çalıştırmanızı ve test etmenizi sağlayan bir konak uygulamasıdır. Sözdizimi renklendirme, sekme tamamlama, görsel hata ayıklama, Unicode uyumluluğu ve bağlama duyarlı yardım gibi önemli özellikler, zengin bir betik deneyimi sağlar.

Daha fazla bilgi için bkz. [Windows PowerShell ISE tanıtımı](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

Aşağıdaki tabloda, Windows PowerShell 'de Windows PowerShell ISE bu sürümü için yeni ve değiştirilmiş özellikler listelenmiştir.

## <a name="intellisense"></a>IntelliSense

> ISE 3,0 eklendi

IntelliSense, Windows PowerShell ISE parçası olan bir otomatik tamamlama yardım özelliğidir.
IntelliSense, siz yazarken eşleşen cmdlet 'ler, parametreler, parametre değerleri, dosyalar veya klasörler için tıklatılabilir menüler görüntüler.

**Bu değişiklik hangi değeri ekler?**

IntelliSense 'in eklenmesiyle, betikleri oluşturmak için Windows PowerShell ISE kullandığınızda cmdlet 'leri ve sözdizimini bulmayı daha kolay hale gelir. Yeni betikler oluştururken Windows PowerShell 'i öğrenmek için Windows PowerShell ISE de kullanabilirsiniz.

**Ne farklı çalışır?**

Windows PowerShell ISE cmdlet 'leri yazdığınızda, kaydırılabilir ve tıklatılabilir bir menü görüntülenir ve ilgili komutlara gözatmanıza ve bunları seçmenize olanak sağlar.

## <a name="snippets"></a>Kod parçacıkları

> ISE 3,0 eklendi

Kod *parçacıkları* , Windows PowerShell ISE içinde oluşturduğunuz betiklere ekleyebileceğiniz Windows PowerShell kodunun kısa bölümleridir. Windows PowerShell ISE, varsayılan bir parçacık kümesiyle gelir. Windows PowerShell ISE çalışırken `New-Snippet` cmdlet 'ini kullanarak kod parçacığı ekleyebilirsiniz.

**Bu değişiklik hangi değeri ekler?**

Kod parçacıklarını kullanarak ortamınızı otomatik hale getirmek için hızlı bir şekilde komut dosyaları oluşturabilir ve oluşturabilirsiniz.

**Ne farklı çalışır?**

Windows PowerShell 3,0 veya sonrasında kod parçacıklarını kullanmak için, **Düzenle** menüsünde, **parçacıkları Başlat**' a tıklayın veya <kbd>CTRL</kbd>+<kbd>J</kbd>' ye basın.

## <a name="add-on-tools"></a>Eklenti araçları

> PowerShell 3,0 ' ye eklendi

Windows PowerShell ISE artık nesne modelini kullanan eklenti araçlarını desteklemektedir. Bu eklentiler, konsolunda dikey veya yatay bölme olarak görüntülenen Windows Presentation Foundation (WPF) denetimleridir. Bölmedeki çoklu eklenti araçları sekmeli Denetim olarak görüntülenir. Ayrıca, Microsoft dışı taraflar tarafından üretilen eklenti araçları ekleyebilir veya kaldırabilirsiniz. Daha fazla bilgi için [Windows PowerShell ISE betik nesnesi modelinin amacını](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)inceleyin.

**Bu değişiklik hangi değeri ekler?**

Eklentiler, işlevselliği ekleyen ve betik deneyiminizi geliştiren araçlarla Windows PowerShell ISE genişletmenize ve özelleştirmenize olanak tanır.

**Ne farklı çalışır?**

Windows PowerShell ISE 3,0 ve üzeri, **Komutlar** eklentisi ile birlikte gelir. **Komutlar** eklentisi, cmdlet 'lere gözatmanıza ve cmdlet 'Ler hakkında **komut dosyası** ve **konsol** bölmeleri ile yan yana erişim sağlamanıza olanak tanır.

Ek **Eklentiler, eklentiler menüsündeki** **eklenti araçları Web sitesini aç** komutu kullanılarak bulunabilir.

## <a name="restart-manager-and-auto-save"></a>Yeniden başlatma Yöneticisi ve otomatik kaydetme

> PowerShell 3,0 ' ye eklendi

Windows PowerShell ISE artık açık betiklerinizi her iki dakikada bir otomatik olarak ayrı bir konuma kaydeder. Beklenmeyen kilitlenme veya yeniden başlatma işleminden sonra Windows PowerShell ISE yeniden başlatıldığında, betikler kaydedilmese bile son oturumda açık olan betikleri kurtarır.

Otomatik kaydetme aralığını değiştirmek için Konsol bölmesinde aşağıdaki komutu çalıştırın: `$psise.Options.AutoSaveMinuteInterval`.

**Bu değişiklik hangi değeri ekler?**

Artık açık betiklerinizin otomatik olarak kaydedildiğini bilmenin Windows PowerShell ISE içinde çalışabilirsiniz.

**Ne farklı çalışır?**

Windows PowerShell ISE 2,0, betikleri otomatik olarak kaydetmez.

## <a name="most-recently-used-list"></a>En son kullanılan liste

> PowerShell 3,0 ' ye eklendi

Artık Windows PowerShell ISE dosyalar için en son kullanılanlar listesine sahiptir. Windows PowerShell ISE **bir dosyayı açtığınızda Dosya menüsündeki en** Son Kullanılanlar listesine eklenir.

En son kullanılan listedeki varsayılan dosya sayısını değiştirmek için Konsol bölmesinde aşağıdaki komutu çalıştırın: `$psise.Options.MruCount`.

**Bu değişiklik hangi değeri ekler?**

Artık sık kullanılan dosyalarınıza kolayca erişmek için en son kullanılan listesini kullanabilirsiniz.

**Ne farklı çalışır?**

Windows PowerShell ISE 2,0 en son kullanılanlar listesine sahip değil.

## <a name="console-pane"></a>Konsol bölmesi

> PowerShell 3,0 ' ye eklendi

İlk Windows PowerShell ISE sürümünde kullanılabilir olan ayrı komut ve çıkış bölmeleri tek bir Konsol bölmesinde birleştirilmiştir. Konsol bölmesi, tipik bir Windows PowerShell konsoluna işlev ve görünüm ile benzerdir, ancak aşağıdaki geliştirmeleri içerir:

- XML sözdizimi dahil olmak üzere giriş metni için sözdizimi renklendirme (çıkış metni değil)
- IntelliSense
- Ayraç eşleştirme
- Hata göstergesi
- Tam Unicode desteği
- <kbd>F1</kbd> bağlama duyarlı yardım
- <kbd></kbd>CTRL+<kbd>F1</kbd> bağlama duyarlı göster-komut
- Karmaşık betik ve sağdan sola destek
- Yazı tipi desteği
- Yakınlaştır
- Satır seçme ve blok seçme modları
- Konsolunda geçmişi görüntülemek için <kbd>yukarı oka</kbd> bastığınızda komut satırında yazılan içeriğin korunması

**Bu değişiklik hangi değeri ekler?**

Bu konsol bölmesi değişikliklerinin eklenmesi konsol arabirimiyle daha tutarlı bir betik deneyimi sağlar.

**Ne farklı çalışır?**

Windows PowerShell ISE 2,0 ayrı komut ve çıkış bölmeleri içerir.

## <a name="command-line-switches"></a>Komut satırı anahtarları

> PowerShell 3,0 ' ye eklendi

Komut satırından Windows PowerShell ISE başlatırsanız ( **powershell_ise. exe**yazarak) aşağıdaki yeni komut satırı anahtarlarını ekleyebilirsiniz.

- `-NoProfile`: Çalıştırmadan Windows PowerShell ISE başlatır`$profile`
- `-Help`: Yardım penceresini görüntüler
- `-mta`: Windows PowerShell ISE çoklu iş parçacıklı grup modunda başlatır. Windows PowerShell ISE için varsayılan işlem modu tek iş parçacıklı grup modu veya `-sta`' dir.

**Bu değişiklik hangi değeri ekler?**

Bu komut satırı anahtarlarının eklenmesi, Windows PowerShell ISE çalıştığı ortamı denetlemenize olanak tanır.

**Ne farklı çalışır?**

Windows PowerShell ISE 2,0, bu komut satırı anahtarlarını tanımıyor.

## <a name="new-editor-features"></a>Yeni Düzenleyici özellikleri

> PowerShell 3,0 ' ye eklendi

Diğer Windows PowerShell ISE düzenlemekte özellikleri şunlardır:

- **XML sözdizimi renklendirme** -Windows PowerShell ISE artık renkler XML söz dizimini BT renkleriyle Windows PowerShell söz dizimi ile aynı şekilde.
- **Ayraç eşleştirme** -Windows PowerShell ISE parantez ile eşleşen ve vurgulamaya sahiptir ve aşağıdaki yollarla kullanılabilir: (örneğin, **eşleşme komutuna git** komutu veya <kbd>CTRL</kbd>+<kbd>]</kbd> , varsa, kapatma küme ayracını bulur) bir açma ayracı seçili olmalıdır).
- **Ana hat görünümü** Betik bölmesi ana hattı destekler, böylece sol kenar boşluğunda artı veya eksi işareti tıklatılarak kod bölümlerinin daralmasına veya genişletildiğine izin verir. Daraltılabilir bir bölümün başlangıcını veya sonunu `#region` işaretlemek `#endregion` için küme ayracı veya ve etiketlerini kullanabilirsiniz. Tüm bölgeleri genişletmek veya daraltmak için <kbd>CTRL</kbd>+tuşuna<kbd>basın.</kbd>
- **Sürükle ve bırak metin düzenlemesi** -Windows PowerShell ISE artık sürükle ve bırak metin düzenlemesini destekliyor. Herhangi bir metin bloğunu seçebilir ve metni, düzenleyicide veya konsolda bulunan başka bir konuma sürükleyerek metnin taşınmasını sağlayabilirsiniz. Seçili metni sürüklerken <kbd>CTRL</kbd> tuşunu basılı tutarsanız, fare düğmesini serbest bırakırsanız metin yeni konuma kopyalanır. Bu Windows PowerShell ISE sürümünde, dosyaları Windows PowerShell ISE sürükleyip bıraktığınızda Windows PowerShell ISE dosyayı açar.
- **Ayrıştırma hatası görüntüleme** -Ayrıştırma hataları kırmızı alt çizgilerle gösterilir. Belirtilen bir hatanın üzerine geldiğinizde, araç ipucu metni kodda bulunan sorunu görüntüler.
- **Yakınlaştır** -konsol içeriğinin yakınlaştırma yüzdesi, Yakınlaştırma kaydırıcısı (Windows PowerShell ISE penceresinin sağ alt köşesinde) veya komut `$psise.options.Zoom` konsol bölmesine girilerek ayarlanabilir.
- **Zengin metin kopyalama ve yapıştırma** -Windows PowerShell ISE Pano 'ya kopyalama, özgün seçimin yazı tipi, boyut ve renk bilgilerini korur.
- **Seçimi engelle** - <kbd>alt</kbd> tuşunu basılı tutarak, farenizle betik bölmesinde metin seçerken veya <kbd>alt</kbd>+<kbd>kaydırma</kbd>+<kbd>okuna</kbd>basarak bir metin bloğunu seçebilirsiniz.

**Bu değişiklik hangi değeri ekler?**

Ek Düzenle özellikleri, daha tutarlı ve güçlü bir düzen ortamı sağlar.

**Ne farklı çalışır?**

Bu düzen geliştirmeleri Windows PowerShell ISE 2,0 ' de yoktu.

## <a name="new-help-viewer-window"></a>Yeni Yardım Görüntüleyici penceresi

> PowerShell 3,0 ' ye eklendi

İmlecinizin bir cmdlet 'deyken <kbd>F1</kbd> tuşuna basarsanız veya bir cmdlet 'in bir parçası vurgulandığında, yeni Yardım Görüntüleyicisi vurgulanan cmdlet hakkında bağlama duyarlı yardım açar. Yardım **hakkında** Windows PowerShell 'i göstermek için konsol `operators` bölmesine yazın ve <kbd>F1</kbd>tuşuna basın.

Bu özelliği kullanmadan önce, Microsoft Web sitesindeki Windows PowerShell yardım konuları 'nın en güncel sürümünü indirin. Yardım konularını indirmek için en basit yöntem, Windows PowerShell ISE yönetici olarak çalıştırırken `Update-Help` , cmdlet 'ini Konsol bölmesinde çalıştırkullanmaktır.

<kbd>F1</kbd> tuşunun yardım için nerede göründüğünü değiştirebilirsiniz. **Araçlar**/Seçenekler menüsünde, **Genel ayarlar** sekmesinde, **diğer ayarlar**' ın altında, **çevrimiçi içerik yerine yerel yardım içeriğini kullan**onay kutusunu ayarlayabilir veya temizleyebilirsiniz. İşaretlendiğinde, istemci, modüller klasöründe bulunan indirilen yardım 'da cmdlet yardımına bakar. Onay kutusu silinirse, istemci yardım çevrimiçi olarak arar.

**Bu değişiklik hangi değeri ekler?**

Geçerli cmdlet 'inizden veya betikten çıkmadan bağlama duyarlı yardım tümleşik bir öğrenme deneyimi sağlar.

**Ne farklı çalışır?**

Önceki Windows PowerShell ISE <kbd>F1</kbd> tuşlarına basmak, yerel bilgisayardaki yardım dosyasını açtı. Windows PowerShell ISE 3,0 ve üzeri sürümlerde, aranabilir ve yapılandırılabilir cmdlet 'inin yardımını içeren bir pencere açılır. Bu yardım deneyimi Windows PowerShell ISE 3,0 ' de yenidir ve Windows PowerShell 3,0 için güncelleştirilebilir yardım yenidir.

## <a name="show-command-cmdlet"></a>Show-Command cmdlet 'i

> PowerShell 3,0 ' ye eklendi

`Show-Command` Cmdlet 'i bir grafik formu doldurarak bir cmdlet veya işlev oluşturabilir veya çalıştırmanıza olanak sağlar. Form, kullanıcıların bir grafik ortamında Windows PowerShell ile çalışmasına olanak tanır.
`Show-Command`Ayrıca Gelişmiş betikler 'in hızlı Windows PowerShell tabanlı GUI oluşturmasına olanak sağlar.

**Bu değişiklik hangi değeri ekler?**

Windows PowerShell `Show-Command` betiklerinizde kullanarak kullanıcılarınıza tanıdık oldukları grafiksel bir ortam sağlayabilirsiniz. `Show-Command`Ayrıca, giriş kullanıcılarına Windows PowerShell 'i Öğrende yardımcı olabilir.

**Ne farklı çalışır?**

`Show-Command`Yeni Windows PowerShell ISE 3,0 ' dir.

## <a name="see-also"></a>Ayrıca bkz.

Windows PowerShell ISE kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell Tümleşik komut dosyası ortamını keşfetme](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).
