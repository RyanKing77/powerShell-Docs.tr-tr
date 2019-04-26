---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: "' Teki yenilikler 50 PowerShell ISE"
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 2d953bc4553de7720c590304d29750b84a1ef3b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058191"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Hangi&#39;yeni Windows PowerShell ıse'de s
Bu konuda, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) sürümlerinde sunulan yeni ve güncelleştirilmiş özellikler açıklanmaktadır.

## <a name="feature-description"></a>Özellik açıklaması
Windows PowerShell ISE yazma, çalıştırma ve betikler ve modüllerle grafik ve sezgisel bir ortamda test olanak tanıyan bir ana bilgisayar uygulamasıdır. Söz dizimi renklendirme gibi önemli özelliklerle sekme tamamlama, görsel hata ayıklama, Unicode uyumluluk ve bağlama duyarlı Yardım zengin bir kodlama deneyimi sunar.

Windows PowerShell ISE genel bakış için bkz. [Windows PowerShell Tümleşik komut dosyası ortamı genel bakış](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Windows PowerShell ıse'de yeni ve değiştirilen işlevsellik
Aşağıdaki tabloda, bu sürümü Windows PowerShell ISE'de Windows PowerShell için yeni ve değiştirilmiş özellikler listelenmektedir.

|Özellik/işlevsellik|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Kod parçacıkları](#snippets)**|X|X||
|**[Eklenti araçları](#add-on-tools)**|X|X||
|**[Yeniden başlatma Yöneticisi ve Otomatik Kaydet](#restart-manager-and-auto-save)**|X|X||
|**[En son kullanılan listesi](#most-recently-used-list)**|X|X||
|**[Konsol bölmesinde](#console-pane)**|X|X||
|**[Komut satırı anahtarları](#command-line-switches)**|X|X||
|**[Yeni Düzenleyici Özellikleri](#new-editor-features)**|X|X||
|**[Yeni Yardım Görüntüleyici penceresi](#new-help-viewer-window)**|X|X||
|**[Show-Command cmdlet'i](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**3.0 ISE'de eklendi**

IntelliSense Windows PowerShell ISE parçası olan bir otomatik tamamlama Yardım özelliğidir. IntelliSense, siz yazarken, potansiyel olarak cmdlet'leri, parametreleri, parametre değerleri, dosyaları veya klasörleri eşleşen tıklanabilir menü görüntüler.

**Bu değişiklik hangi değeri ekler?**

IntelliSense'nın eklenmesiyle, komut dosyaları oluşturmak için Windows PowerShell ISE kullandığınızda, cmdlet'ler ve söz dizimi bulmak daha kolay olur. Ayrıca, yeni komut dosyası oluştururken, Windows PowerShell öğrenmek için Windows PowerShell ISE kullanabilirsiniz.

**Farklı işleyen nedir?**

Cmdlet'lerini Windows PowerShell ISE 3.0 veya üzeri yazdığınızda, böylece ve uygun komutları seçmek kaydırılabilir ve tıklatılabilir bir menü görüntüler.

### <a name="snippets"></a>Kod parçacıkları
**3.0 ISE'de eklendi**

*Kod parçacıkları* Windows PowerShell ISE'de oluşturduğunuz betikler eklemek Windows PowerShell kodu kısa bölümler. Windows PowerShell ISE kod parçacıkları varsayılan kümesi ile birlikte gelir. Kod parçacıkları kullanarak ekleyebilirsiniz **yeni kod parçacığı** Windows PowerShell ISE'de çalışırken cmdlet'i.

**Bu değişiklik hangi değeri ekler?**

Kod parçacıkları kullanarak hızlı bir şekilde birleştirin ve ortamınızı otomatik hale getirmek için betikleri oluşturun.

**Farklı işleyen nedir?**

Windows PowerShell 3.0 veya sonraki kod parçacıkları kullanması için **Düzenle** menüsünde tıklayın **parçacıkları Başlat**, veya basın **Ctrl-J**.

### <a name="add-on-tools"></a>Eklenti araçları
**PowerShell 3.0 eklendi**

Windows PowerShell ISE nesne modeli kullanılarak eklenen denetimler Windows Presentation Foundation (WPF) eklenti araçları, artık desteklemektedir. Eklenti araçları, konsolda bir dikey veya yatay bölme olarak görüntülenebilir. Sekmeli denetim olarak birden fazla eklenti araçları bölmesinde görüntülenir. Ayrıca, ekleyebilir veya Microsoft dışı taraflarca oluşturulan eklenti araçları kaldırabilirsiniz. İçeri aktarma veya eklenti araçları kaldırma hakkında daha fazla bilgi için bkz. [Windows PowerShell ISE işlemleri](https://technet.microsoft.com/library/cc732148.aspx).

**Bu değişiklik hangi değeri ekler?**

Eklentiler, genişletme ve Windows PowerShell ISE betik oluşturma deneyiminizi geliştirin veya Windows PowerShell ISE'ye işlevsellik ekleyen araçlarla özelleştirme olanak tanır.

**Farklı işleyen nedir?**

Windows PowerShell ISE 3.0 ve sonraki sürümleri ile birlikte geldiğinden **komutları** eklenti. **Komutları** eklenti cmdlet'leri göz atın ve cmdlet'leri yan yana ile ilgili Yardım erişim olanak tanır **betik** ve **konsol** bölmeleri.

Ek Eklentiler kullanarak bulunabilir **eklenti araçları Web sitesi Aç** komutunu **eklentileri** menüsü.

### <a name="restart-manager-and-auto-save"></a>Yöneticisi yeniden Otomatik Kaydet
**PowerShell 3.0 eklendi**

Windows PowerShell ISE artık otomatik olarak açık betiklerinizi iki dakikada bir, ayrı bir konuma kaydeder.  Betikleri kaydedilmedi bile Windows PowerShell ISE çalışmayı durduruyor ya da Windows PowerShell ISE yeniden başlatıldıktan sonra işletim sistemini yeniden başlatılırsa bu kurtarır olan betikler son oturumunuzda açın.

Otomatik kaydetme aralığını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.AutoSaveMinuteInterval**.

**Bu değişiklik hangi değeri ekler?**

Artık Windows PowerShell ISE açık betiklerinizi beklenmeyen bir yeniden başlatma durumunda otomatik olarak kaydedilir bilerek içinde çalışabilirsiniz.

**Farklı işleyen nedir?**

Windows PowerShell ISE 2.0 komut dosyalarını otomatik olarak yeniden başlatma durumunda kaydetmez.

### <a name="most-recently-used-list"></a>En son kullanılan listesi
**PowerShell 3.0 eklendi**

Windows PowerShell ISE artık dosyalar için en son kullanılan bir listesi vardır. Windows PowerShell ISE'de bir dosyayı açtığınızda, dosyanın en son kullanılan listeye eklendiğini **dosya** menüsü.

En son kullanılan listede yer alan dosyalar varsayılan sayısını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.MruCount**.

**Bu değişiklik hangi değeri ekler?**

En Son Kullanılanlar listesi artık kolayca sık kullanılan dosyalarınıza erişmek için de kullanabilirsiniz.

**Farklı işleyen nedir?**

Windows PowerShell ISE 2.0 en son kullanılan liste yok.

### <a name="console-pane"></a>Konsol bölmesinde
**PowerShell 3.0 eklendi**

Tek bir konsol bölmesine ayrı komut ve Windows PowerShell ISE ilk sürümde kullanılabilir çıkış bölmeleri birleştirilmiştir. Konsol bölmesinde işlevi ve tipik bir Windows PowerShell Konsolu görünümünü benzer, ancak (çoğu bu konuda açıklandığı gibi) aşağıdaki geliştirmeleri içerir.

- Giriş metin (çıkış metin değil), XML sözdizimi de dahil olmak üzere söz dizimi renklendirmesi

- IntelliSense

- Ayraç eşleştirme

- Hata göstergesi

- Tam Unicode desteği

- **F1** bağlama duyarlı Yardım

- **CTRL + F1** bağlama duyarlı Göster komutu

- Karmaşık bir betik ve sağdan sola destek

- Yazı tipi desteği

- Yakınlaştır

- Satırı seçin ve blok seçim modları

- Yazılan içerik tuşuna bastığınızda komut satırında korunmasını **yukarı** konsolda geçmişini görüntülemek için oku

**Bu değişiklik hangi değeri ekler?**

Konsol bölmesinde değişikliklerin eklenmesini konsoluna arabirimle daha tutarlı bir kodlama deneyimi sağlar.

**Farklı işleyen nedir?**

Windows PowerShell ISE 2.0 ayrı komut ve çıkış bölmeleri vardır.

### <a name="command-line-switches"></a>Komut satırı anahtarları
**PowerShell 3.0 eklendi**

Komut satırından Windows PowerShell ISE başlatırsanız (yazarak **powershell_ise.exe**), aşağıdaki yeni komut satırı anahtarları ekleyebilirsiniz.

- *-NoProfile*: Windows PowerShell ISE verilmeden çalıştırılmasını başlatır **$profile**

- *-Help*: Yardım penceresini görüntüler

- *-mta*: Windows PowerShell ISE birden çok iş parçacıklı bölme modunda başlatır. Windows PowerShell ISE için varsayılan işlem modu tek iş parçacıklı bölme modunda olduğundan veya *- sta*.

**Bu değişiklik hangi değeri ekler?**

Bu komut satırı anahtarları eklenmesi, Windows PowerShell ISE çalıştığı ortam denetlemenize olanak tanır.

**Farklı işleyen nedir?**

Windows PowerShell ISE 2.0, bu komut satırı anahtarları kabul etmiyor.

### <a name="new-editor-features"></a>Yeni Düzenleyici Özellikleri
**PowerShell 3.0 eklendi**

Diğer Windows PowerShell ISE düzenleme özellikleri şunlardır:

- **XML sözdizimi renklendirme**Windows PowerShell ISE'de artık renkleri XML sözdizimini aynı şekilde Windows PowerShell söz dizimi renkleri gibi.

- **Ayraç eşleştirme** Windows PowerShell ISE vurgulama ve Ayraç eşleştirme içerir ve aşağıdaki şekillerde kullanılabilir: (örneğin, kullanarak **eşleşmeye Git** komutu veya **Ctrl +]** bulur Seçili bir açılış ayracı varsa, kapanış ayracı).

- **Anahat görünümü** betik bölmesine destekler anahat oluşturma, artı veya eksi tıklayarak kod bölümlerini genişletme veya daraltma imzalar sol kenar boşluğunda izin verir. Küme ayraçları kullanabilirsiniz veya **#region** ve **#endregion** başlangıcında veya daraltılabilir bir bölüm sonu işaretlemek için etiketleri. Genişlet veya daralt tüm bölgeler için basın **Ctrl + M**.

- **Sürükle ve bırak metin düzenlemesini**sürükle ve bırak metin düzenlemesini artık Windows PowerShell ISE. Herhangi bir metin bloğu seçin ve bu metin düzenleyicisi veya konsol metni taşımak için başka bir konuma sürükleyin. Fare düğmesini bıraktığınızda, seçili metni sürüklerken Ctrl tuşunu basılı tutun, metin yeni konuma kopyalanır. Windows PowerShell ISE'yi .iso dosyalarını sürükleyip Windows PowerShell ISE bu sürümü, aynı zamanda Windows PowerShell ISE önceki sürümünü, Windows PowerShell ISE dosyayı açar.

- **Hata ekranı ayrıştırma** ayrıştırma hataları kırmızı alt çizgi ile gösterilir. Belirtilen bir hata geldiğinizde, araç ipucu metni, kod içinde bulunan sorun görüntüler.

- **Yakınlaştırma** konsolun içeriği yakınlaştırma yüzdesi yakınlaştırma kaydırıcısı (alt sağ köşesinde Windows PowerShell ISE penceresi) kullanarak veya komutu girerek ayarlanabilir **$psise.options.Zoom** Konsol bölmesinde.

- **Zengin Metin Kopyala ve Yapıştır** yazı tipi, boyut ve renk bilgilerini özgün seçimin içinde Windows PowerShell ISE korur Panoya kopyalama.

- **Blok seçimi** betik bölmesine farenizi metin seçim sırasında ALT tuşunu basılı tutarak veya tuşuna basarak metin bloğu seçin **Alt + SHIFT + ok**.

**Bu değişiklik hangi değeri ekler?**

Ek düzenleme özellikleri, daha tutarlı ve güçlü bir düzenleme ortamı sağlar.

**Farklı işleyen nedir?**

Bu düzenleme geliştirmeleri, Windows PowerShell ISE 2.0 sürümünde bulunmamaktadır.

### <a name="new-help-viewer-window"></a>Yeni Yardım Görüntüleyici penceresi
**PowerShell 3.0 eklendi**

Basarsanız **F1** imlecinizi bir cmdlet'tir veya vurgulanmış bir cmdlet bir parçası olan, bağlama duyarlı Yardım vurgulanan cmdlet'i hakkında yeni Yardım Görüntüleyicisi'ni açar. Windows PowerShell hakkında Yardım görüntülemek üzere şunu yazın **işleçleri** ENTER tuşuna basın ve konsol bölmesinde **F1**.

Bu özelliği kullanmadan önce Windows PowerShell Yardım konularını en güncel sürümü Microsoft Web sitesinden indirin. Yardım konuları karşıdan yüklemek için en basit yöntem çalıştırmaktır **Update-Help** cmdlet'ini yönetici olarak Windows PowerShell ISE çalışırken Konsol bölmesinde.

Where değiştirebilirsiniz **F1** anahtar Yardım için arar. İçinde **Araçları**/**seçenekleri** menü, **genel ayarlar** sekmesindeki **diğer ayarlar**, ayarlama veya Temizle onay kutusu **yerel Yardım içeriğini kullanmak yerine çevrimiçi içerik**. Eğer işaretliyse, cmdlet modülleri klasöründe bulunan indirilen Yardımı'nda Yardım istemci arar.  Onay kutusu işaretli değilse, istemci için cmdlet yardımına TechNet kitaplığında arar.

**Bu değişiklik hangi değeri ekler?**

Geçerli bir cmdlet veya betik çıkmadan bağlama duyarlı Yardım sorunsuz öğrenme deneyimi sağlar.

**Farklı işleyen nedir?**

Windows PowerShell ISE önceki sürümlerinde F1 tuşuna bastığınızda, Yardım dosyasını yerel bilgisayarda açıldı. Windows PowerShell ISE 3.0 ve sonraki sürümlerinde, aranabilir ve yapılandırılabilir bir cmdlet için Yardım içeren bir pencere açılır. Bu Yardım deneyimi için Windows PowerShell ISE 3.0 yenidir ve Windows PowerShell 3.0 için güncelleştirilebilir Yardımı yenidir.

### <a name="show-command-cmdlet"></a>Show-Command cmdlet'i
**PowerShell 3.0 eklendi**

**Show komutunu** cmdlet'i oluşturun veya bir grafik biçiminde doldurarak bir cmdlet veya işlev çalıştırmanızı sağlar. Formu Windows PowerShell ile bir grafiksel ortamda çalışma olanağı sunar. **Show komutunu** ayrıca çalıştırıcılara hızlı bir Windows PowerShell tabanlı GUI oluşturmak için Gelişmiş etkinleştirir.

**Bu değişiklik hangi değeri ekler?**

Kullanarak **Show komutunu** , Windows PowerShell betiklerini, kullanıcılarınızın olduğu tanıdık grafik ortamıyla sağlayabilirsiniz. **Show komutunu** Windows PowerShell tanıtım kullanıcıların da yardımcı olabilir.

**Farklı işleyen nedir?**

Show-yeni Windows PowerShell ISE 3.0 komutudur.

## <a name="see-also"></a>Ayrıca bkz.
Windows PowerShell'de Windows PowerShell ISE'yi kullanma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.

- [Windows PowerShell Tümleşik komut dosyası ortamı keşfetme](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE TechNet Wiki](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Betik Merkezi](https://technet.microsoft.com/scriptcenter/default)