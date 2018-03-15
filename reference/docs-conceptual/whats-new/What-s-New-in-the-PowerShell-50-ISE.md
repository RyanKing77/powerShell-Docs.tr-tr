---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: Hangi s yeni 50 PowerShell ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 9fd25a4759602bebf2b5df2c17d0c816a15e5e2b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Ne&#39;s Windows PowerShell ISE'deki yenilikler
Bu konu, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) sürümlerde sunulan yeni ve güncelleştirilmiş özelliklerin açıklar.

## <a name="feature-description"></a>Özellik açıklaması
Windows PowerShell ISE yazma, çalıştırma ve komut dosyaları ve modüller bir grafik ve sezgisel ortamında test etme olanak tanıyan bir ana bilgisayar uygulamasıdır. Sözdizimi renklendirmesi gibi anahtar özellikleri sekme tamamlama, visual hata ayıklama, Unicode uyumluluk ve bağlama duyarlı Yardım zengin bir komut dosyası deneyimi sağlar.

Windows PowerShell ISE genel bakış için bkz: [Windows PowerShell Tümleşik komut dosyası ortamı genel bakış](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Windows PowerShell ISE yeni ve değiştirilmiş işlevleri
Aşağıdaki tabloda, Windows PowerShell'de Windows PowerShell ISE bu sürümü için yeni ve değiştirilmiş özellikler listelenmektedir.

|Özellik/işlevsellik|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Snippets](#snippets)**|X|X||
|**[Eklenti araçları](#add-on-tools)**|X|X||
|**[Yeniden başlatma Yöneticisi ve otomatik kayıt](#restart-manager-and-auto-save)**|X|X||
|**[En son kullanılan listesi](#most-recently-used-list)**|X|X||
|**[Konsol bölmesinde](#console-pane)**|X|X||
|**[Komut satırı anahtarları](#command-line-switches)**|X|X||
|**[Yeni Düzenleyicisi özellikleri](#new-editor-features)**|X|X||
|**[Yeni Yardım Görüntüleyici](#new-help-viewer-window)**|X|X||
|**[Göster-Command cmdlet'i](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**ISE 3.0 eklendi**

IntelliSense Windows PowerShell ISE parçası olan bir otomatik tamamlama Yardım özelliğidir. IntelliSense, siz yazarken, büyük olasılıkla cmdlet'leri, parametreleri, parametre değerlerini, dosyalar veya klasörler eşleşen tıklanabilir menüleri görüntüler.

**Bu değişiklik hangi değeri ekler?**

IntelliSense eklenmesiyle, komut dosyaları oluşturmak için Windows PowerShell ISE kullandığınızda cmdlet'ler ve söz dizimine bulmak daha kolay olur. Yeni komut dosyası oluştururken, Windows PowerShell öğrenmek için Windows PowerShell ISE de kullanabilirsiniz.

**Neler farklı şekilde çalışır?**

Cmdlet'lerini Windows PowerShell ISE 3.0 veya daha yenisi yazdığınızda, göz atın ve uygun komutları seçim olanak tanıyan bir kaydırılabilir ve tıklatılabilir menüsünü görüntüler.

### <a name="snippets"></a>Kod parçacıkları
**ISE 3.0 eklendi**

*Kod parçacıkları* kısa bölümler Windows PowerShell kodunun, Windows PowerShell ISE oluşturduğunuz betikler ekleyebilirsiniz. Windows PowerShell ISE parçacıkları varsayılan kümesi ile birlikte gelir. Kullanarak parçacıkları ekleyebilirsiniz **yeni kod parçacığında** Windows PowerShell ISE çalışırken cmdlet'i.

**Bu değişiklik hangi değeri ekler?**

Parçacıkları kullanarak hızlı bir şekilde derleyecek ve ortamınızı yönetmek için betikler oluşturma.

**Neler farklı şekilde çalışır?**

Parçacıkları Windows PowerShell 3.0 veya üstü, üzerinde kullanmak için **Düzenle** menüsünde tıklatın **Başlat parçacıkları**, veya basın **Ctrl-J**.

### <a name="add-on-tools"></a>Eklenti araçları
**PowerShell 3.0 eklendi**

Windows PowerShell ISE artık nesne modelini kullanarak eklenen Windows Presentation Foundation (WPF) denetimler eklenti araçları destekler. Eklenti araçları konsol dikey veya yatay bölmesinde olarak görüntülenebilir. Birden fazla eklenti araçları bölmesinde sekmeli bir denetim olarak görüntülenir. Ayrıca, ekleyin veya Microsoft dışı taraflarca üretilen eklenti araçları kaldırın. Alma veya eklenti araçları kaldırma hakkında daha fazla bilgi için bkz: [Windows PowerShell ISE işlemleri](http://technet.microsoft.com/library/cc732148.aspx).

**Bu değişiklik hangi değeri ekler?**

Eklentiler genişletmenizi ve komut dosyası deneyiminizi iyileştirmek veya Windows PowerShell ISE işlevsellik ekleyen araçları ile Windows PowerShell ISE özelleştirmenizi sağlar.

**Neler farklı şekilde çalışır?**

Windows PowerShell ISE 3.0 ve sonraki sürümleri ile birlikte gelir **komutları** eklentisi. **Komutları** eklenti cmdlet'leri göz atarak cmdlet'leri yan yana ile ilgili yardıma erişmek verir **betik** ve **konsol** bölmeleri.

Ek eklentilerin kullanarak bulunabilir **açık eklenti araçları Web sitesi** komutunu **eklentileri** menüsü.

### <a name="restart-manager-and-auto-save"></a>Yöneticisi ve otomatik kayıt yeniden başlatın
**PowerShell 3.0 eklendi**

Windows PowerShell ISE artık otomatik olarak açık komut dosyalarınızı her iki dakikada ayrı bir konuma kaydeder.  Komut dosyalarını kaydedilmedi olsa bile Windows PowerShell ISE çalışmayı durduruyor ya da Windows PowerShell ISE yeniden başlatıldıktan sonra işletim sistemini yeniden başlatılırsa, kurtarır olan komut dosyaları son oturumu açın.

Otomatik kaydetme aralığını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.AutoSaveMinuteInterval**.

**Bu değişiklik hangi değeri ekler?**

Artık Windows PowerShell ISE açık komut dosyalarınızı beklenmeyen bir yeniden başlatma durumunda otomatik olarak kaydedilir bilerek içinde çalışabilirsiniz.

**Neler farklı şekilde çalışır?**

Windows PowerShell ISE 2.0 komut dosyaları otomatik olarak yeniden başlatma durumunda kaydetmez.

### <a name="most-recently-used-list"></a>En son kullanılan listesi
**PowerShell 3.0 eklendi**

Windows PowerShell ISE artık dosyalar için en son kullanılan bir listesi vardır. Windows PowerShell ISE'de bir dosyayı açtığınızda, dosyanın en son kullanılan listeye üzerinde eklenen **dosya** menüsü.

En son kullanılan listede yer alan dosyalar varsayılan sayısını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.MruCount**.

**Bu değişiklik hangi değeri ekler?**

Artık, en son kullanılan listesinde kolayca sık kullanılan dosyalarınıza erişmek için de kullanabilirsiniz.

**Neler farklı şekilde çalışır?**

Windows PowerShell ISE 2.0 en son kullanılan listesini yok.

### <a name="console-pane"></a>Konsol bölmesinde
**PowerShell 3.0 eklendi**

Tek bir konsol bölmesine birleştirilmiştir, ayrı komut ve çıktı bölmeleri, Windows PowerShell ISE ilk sürümünde kullanılabilir. Konsol bölmesinde işlevi ve tipik bir Windows PowerShell Konsolu görünümünü benzer, ancak (Bu konuda açıklanan çoğu) aşağıdaki geliştirmeleri içerir.

- Giriş metni (çıktı metin değil), XML sözdizimi dahil olmak üzere sözdizimi renklendirmesi

- IntelliSense

- Ayraç eşleştirme

- Hata göstergesi

- Tam Unicode desteği

- **F1** bağlama duyarlı Yardım

- **CTRL + F1** bağlama duyarlı Göster komutu

- Karmaşık komut dosyası ve sağdan sola desteği

- Yazı tipi desteği

- Yakınlaştır

- Satırı seçin ve blok seçim modları

- Yazılan içerik tuşuna bastığınızda komut satırında korunmasını **yukarı** konsolda geçmişini görüntülemek için oku

**Bu değişiklik hangi değeri ekler?**

Konsol bölmesinde değişikliklerin eklenmesi, konsol arabirimiyle daha tutarlı bir komut dosyası deneyimi sağlar.

**Neler farklı şekilde çalışır?**

Windows PowerShell ISE 2.0 ayrı komut ve çıktı bölmeleri vardır.

### <a name="command-line-switches"></a>Komut satırı anahtarları
**PowerShell 3.0 eklendi**

Komut satırından Windows PowerShell ISE başlatırsanız (yazarak **powershell_ise.exe**), aşağıdaki yeni komut satırı anahtarları ekleyebilirsiniz.

- *-NoProfile*: Windows PowerShell ISE çalıştırılmadan başlatır **$profile**

- *-Yardım*: Yardım penceresini görüntüler

- *-mta*: Windows PowerShell ISE birden çok iş parçacıklı grup modunda başlatır. Tek iş parçacıklı bölme modunda, Windows PowerShell ISE için varsayılan çalışma modu olan veya *- sta*.

**Bu değişiklik hangi değeri ekler?**

Bu komut satırı anahtarları eklenmesi, Windows PowerShell ISE çalıştığı ortam denetlemenizi sağlar.

**Neler farklı şekilde çalışır?**

Windows PowerShell ISE 2.0 Bu komut satırı anahtarları tanımıyor.

### <a name="new-editor-features"></a>Yeni Düzenleyicisi özellikleri
**PowerShell 3.0 eklendi**

Diğer Windows PowerShell ISE düzenleme özellikleri içerir:

- **XML sözdizimi renklendirmesi**Windows PowerShell ISE şimdi renkleri XML sözdizimi aynı şekilde Windows PowerShell sözdizimi renkleri gibi.

- **Ayraç eşleştirme** Windows PowerShell ISE eşleşen ayraç ve vurgulama içerir ve aşağıdaki şekillerde kullanılabilir: (örneğin, kullanarak **eşleşen Git** komut veya **Ctrl +]** bulur Seçili açılan parantez varsa, kapanış ayracı).

- **Anahat görünümü** betik bölmesine destekler daraltma veya kodun bölümlerini artı veya eksi tıklayarak genişletme imzalar sol kenar boşluğunda sağlayan anahat oluşturma,. Küme ayraçları kullanabilirsiniz veya **#region** ve **#endregion** başında ve sonunda daraltılabilir bölümünün işaretlemek için etiketler. Genişlet veya daralt tüm bölgeler için basın **Ctrl + M**.

- **Sürükle ve bırak metin düzenleme**destekler sürükleyip metin düzenleme artık Windows PowerShell ISE. Herhangi bir metin bloğunu seçin ve bu metin düzenleyicisi veya Konsolu metni taşımak için başka bir konuma sürükleyin. Ctrl tuşunu basılı tutarak fare düğmesini bıraktığınızda seçili metni sürükleyin, metin yeni bir konuma kopyalanır. Windows PowerShell ISE dosyalarını sürükleyip Windows PowerShell ISE bu sürümü, aynı zamanda Windows PowerShell ISE önceki sürümü, Windows PowerShell ISE dosyayı açar.

- **Hata ekranı ayrıştırma** ayrıştırma hatalarını kırmızı alt çizgi ile belirtilir. Belirtilen hata geldiğinizde, araç ipucu metni kodda bulundu sorun görüntüler.

- **Yakınlaştırma** konsol yakınlaştırma yüzdesini '™ s içeriğin (alt sağ köşesinde Windows PowerShell ISE penceresi) yakınlaştırma kaydırıcıyı kullanarak ya da komutu girerek ayarlanabilir **$psise.options.Zoom** Konsol bölmesinde.

- **Zengin Metin Kopyala ve Yapıştır** yazı tipi, boyut ve renk bilgilerini özgün seçimin içinde Windows PowerShell ISE korur Panoya kopyalama.

- **Blok Seçi** basarak veya betik bölmesine fareyi metin seçerken ALT tuşunu basılı tutarak bir metin bloğunu seçebileceğiniz **Alt + üst karakter + ok**.

**Bu değişiklik hangi değeri ekler?**

Ek düzenleme özellikleri daha tutarlı ve güçlü bir düzenleme ortamı sağlar.

**Neler farklı şekilde çalışır?**

Bu düzenleme iyileştirmeler Windows PowerShell ISE 2. 0 ' mevcut değil.

### <a name="new-help-viewer-window"></a>Yeni Yardım Görüntüleyici
**PowerShell 3.0 eklendi**

Basarsanız **F1** imlecinizi bir cmdlet veya vurgulanmış bir cmdlet parçası sahip olduğunda, bağlama duyarlı Yardım vurgulanan cmdlet'i hakkında yeni Yardım Görüntüleyicisi'ni açar. Windows PowerShell hakkında Yardım görüntülemek için şunu yazın **işleçleri** Konsol bölmesinde ve ENTER tuşuna basın **F1**.

Bu özelliği kullanmadan önce Windows PowerShell Yardım konularını en güncel sürümünü Microsoft Web sitesinden indirin. Yardım konuları indirme en basit yöntemi çalıştırmaktır **Update-Help** konsol Windows PowerShell ISE yönetici olarak çalıştırırken bölmesinde cmdlet'i.

Where alter **F1** anahtar yardımını arar. İçinde **Araçları**/**seçenekleri** menüsü, **genel ayarları** sekmesinde, altında **diğer ayarlar**, ayarlama veya temizleyin onay kutusu **yerel Yardım içeriği yerine çevrimiçi içerik kullanmak**. İşaretlendiğinde, cmdlet modülleri klasöründe bulunan indirilen Yardımı'nda Yardım istemci arar.  Onay kutusu işaretli değilse, istemci cmdlet Yardım için TechNet kitaplığında arar.

**Bu değişiklik hangi değeri ekler?**

Geçerli cmdlet veya betik ayrılmadan bağlama duyarlı Yardım sorunsuz öğrenme deneyimi sağlar.

**Neler farklı şekilde çalışır?**

Windows PowerShell ISE önceki sürümlerinde F1'e basarak Yardım dosyasını yerel bilgisayarda açıldı. Windows PowerShell ISE 3.0 ve sonraki sürümlerinde, aranabilir ve yapılandırılabilir cmdlet için Yardım içeren bir pencere açılır. Bu Yardım deneyimi için Windows PowerShell ISE 3.0 yenidir ve Windows PowerShell 3.0 için güncelleştirilebilir Yardımı yenidir.

### <a name="show-command-cmdlet"></a>Göster-Command cmdlet'i
**PowerShell 3.0 eklendi**

**Göster komutu** cmdlet oluşturun veya bir cmdlet veya işlevi bir grafik formda doldurarak çalıştırmak olanak sağlar. Form, kullanıcılar Windows PowerShell ile bir grafiksel ortamda iş olanak tanır. **Göster komutu** da hızlı bir Windows PowerShell tabanlı GUI oluşturmak için çalıştırıcılara Gelişmiş etkinleştirir.

**Bu değişiklik hangi değeri ekler?**

Kullanarak **Göster komutu** Windows PowerShell komut dosyalarınızı oldukları tanıdık grafik ortamıyla kullanıcılarınızın sağlayabilir. **Göster komutu** Windows PowerShell öğrenin giriş kullanıcılar da yardımcı olabilir.

**Neler farklı şekilde çalışır?**

Göster-yeni Windows PowerShell ISE 3.0 komuttur.

## <a name="see-also"></a>Ayrıca bkz:
Windows PowerShell'de Windows PowerShell ISE kullanma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.

- [Windows PowerShell Tümleşik komut dosyası ortamı keşfetme](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [TechNet Wiki'de işe](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Komut Merkezi](http://technet.microsoft.com/scriptcenter/default)

