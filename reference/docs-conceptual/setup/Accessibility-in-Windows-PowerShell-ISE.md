---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell ISE’de erişilebilirlik"
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 7f758a46bdc722482b9e8a9baaff0a075f64ece9
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="accessibility-in-windows-powershell-ise"></a>Windows PowerShell ISE’de erişilebilirlik
Bu konu, Windows PowerShell Tümleşik komut dosyası ortamı (yararlı bulabileceğiniz ISE)'ın erişilebilirlik özelliklerini açıklar.

* [Konsol ve komut dosyası bölmeleri konumunu ve boyutunu değiştirme](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Metin düzenleme için klavye kısayolları](#keyboard-shortcuts-for-editing-text)
* [Komut dosyaları çalıştırmak için klavye kısayolları](#keyboard-shortcuts-for-running-scripts)
* [Görünümünü özelleştirmek için klavye kısayolları](#keyboard-shortcuts-for-customizing-the-view)
* [Komut dosyaları hata ayıklama için klavye kısayolları](#keyboard-shortcuts-for-debugging-scripts)
* [Windows PowerShell sekmeler için klavye kısayolları](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Başlatma ve çıkma için klavye kısayolları](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft, ürünlerinin ve hizmetlerinin kullanımını herkes için kolaylaştıracağını taahhüt eder. Aşağıdaki konular, özellikler, ürünler ve Windows PowerShell ISE engelli kişiler için daha erişilebilir hale hizmetler hakkında bilgi sağlar.

Windows PowerShell ISE yüksek karşıtlık modunu destekler. Görme engelli için kesme noktaları, gibi yönetmek için cmdlet'leri aracılığıyla kesme noktası bilgisi kullanılabilir [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) ve [kümesi PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Daha fazla bilgi için lütfen ' kesme noktaları yönetmek ' nda bkz. [hata ayıklama komut dosyalarında Windows PowerShell ISE nasıl](../core-powershell/ise/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Erişilebilirlik özellikleri ve Microsoft Windows yardımcı programlara ek olarak, aşağıdaki özellikler Windows PowerShell ISE daha engelli kişiler için erişilebilir:

- Klavye kısayolları

- Sözdizimi renkleri tablo ve birkaç kullanarak diğer renk ayarlarını değiştirme yeteneğini [$psISE.Options](https://technet.microsoft.com/en-us/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) komut dosyası nesnesi.

- Metin boyutu Değiştir

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Konsol ve komut dosyası bölmeleri konumunu ve boyutunu değiştirme
Konsol bölmesinde ve betik bölmesine konumunu ve boyutunu değiştirmek için aşağıdaki adımları kullanın. Windows PowerShell ISE yeniden açtığınızda, boyut ve konum değişikliklerinin korunur.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Komut dosyası ve konsol bölmesinde yeniden boyutlandırmak için

1. Komut dosyası ve konsol bölmesinde arasında bölünmüş satırındaki işaretçi duraklatın.

2. Fare işaretçisini iki yönlü oka değiştiğinde bölmesinin boyutunu değiştirmek için kenarlığı sürükleyin.

### <a name="to-move-the-script-pane-and-console-pane"></a>Komut dosyası ve konsol bölmesinde taşımak için
Aşağıdakilerden birini yapın:

- Yukarıda Konsol bölmesinde betik bölmesini taşımak için tuşuna basın **CTRL + 1** veya araç çubuğunda tıklatın **betik bölmesinde üstü Göster** simgesi veya **Görünüm** menüsünde tıklatın **Göster Betik bölmesinde üst**.

- Betik bölmesine Konsol bölmesinde sağa taşıma için basın **CTRL + 2** veya araç çubuğunda tıklatın **Göster betik bölmesinde sağ** simgesi, veya **Görünüm** menüsünde tıklatın**Betik bölmesine sağ Göster getirin**.

- Betik bölmesine en üst düzeye çıkarmak için basın **CTRL + 3** veya araç çubuğunda tıklatın **Göster betik bölmesinde ekranı** simgesi veya **görünümü** menüsünde'ı tıklatın **komut dosyasını Göster Tam ekran bölmesinde**.

- Konsol bölmesinde en üst düzeye çıkarmak ve betik bölmesinde sekmeler, satırın sağ kenar gizlemek için tıklatın **betik Bölmesini Gizle** simgesi, **Görünüm** menüsü, seçimini kaldırmak için tıklatın **betik bölmesini göster** menü seçeneği.

- Konsol bölmesinde, en sağdaki kenarın sekmeler, satırın ekranı betik bölmesine görüntülemek için tıklatın **betik bölmesini göster** simge veya **Görünüm** menüsü, seçmek için tıklatın **komut dosyasını Göster Bölmesinde** menü seçeneği.

## <a name="keyboard-shortcuts-for-editing-text"></a>Metin düzenleme için klavye kısayolları
Metin düzenlediğinizde, aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye kısayolları|Kullanın.|
|----------|----------------------|----------|
|**Kopyalama**|CTRL+C|Betik bölmesi, konsol bölmesi|
|**Kes**|CTRL+X|Betik bölmesi, konsol bölmesi|
|**Komut dosyasında bulunamadı**|CTRL+F|Komut dosyası bölmesi|
|**Komut dosyasında Sonrakini Bul**|F3|Komut dosyası bölmesi|
|**Komut dosyasında Öncekini Bul**|SHIFT+F3|Komut dosyası bölmesi|
|**Yapıştır**|CTRL+V|Betik bölmesi, konsol bölmesi|
|**Yinele**|CTRL+Y|Betik bölmesi, konsol bölmesi|
|**Komut dosyasında değiştirin**|CTRL + H|Komut dosyası bölmesi|
|**Kaydet**|CTRL+S|Komut dosyası bölmesi|
|**Tümünü Seç**|CTRL+A|Betik bölmesi, konsol bölmesi|
|**Geri alma**|CTRL+Z|Betik bölmesi, konsol bölmesi|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Komut dosyaları çalıştırmak için klavye kısayolları
Betik bölmesinde komut dosyalarını çalıştırdığınızda, aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye kısayolu|
|----------|---------------------|
|**Yeni**|CTRL+N|
|**Açık**|CTRL+O|
|**çalıştırma**|F5|
|**Seçimi Çalıştır**|F8|
|**Yürütme Durdur**|CTRL + BREAK. CTRL + C (metin seçili olduğunda) bağlamı anlaşılır olduğunda kullanılabilir.|
|**Sekme** (için sonraki komut dosyası)|CTRL + SEKME **Not:** sonraki komut dosyası sekmesine çalışır yalnızca açın, tek bir PowerShell sekme sahip veya ne zaman, birden fazla PowerShell sekmesini açmak varsa, ancak betik bölmesinde odak noktasıdır.|
|**Sekme** (için önceki komut dosyası)|CTRL + SHIFT + SEKME **Not:** önceki betik sekmesine çalışır, yalnızca bir PowerShell sekme açık olduğunda ya da birden fazla PowerShell sekmesini açmak varsa ve betik bölmesinde odak noktasıdır.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Görünümünü özelleştirmek için klavye kısayolları
Windows PowerShell ISE görünümünde özelleştirmek için aşağıdaki klavye kısayollarını kullanabilirsiniz. Bunlar, uygulamadaki tüm bölmeleri erişilebilir.

|Eylem|Klavye kısayolu|
|----------|---------------------|
|**Konsol bölmesinde gidin**|CTRL+D|
|**Betik bölmesine gidin**|CTRL+I|
|**Betik bölmesini göster**|CTRL+R|
|**Betik Bölmesini Gizle**|CTRL+R|
||
|**Betik bölmesine Yukarı Taşı**|CTRL+1|
|**Betik bölmesine sağa taşır**|CTRL+2|
|**Betik bölmesine en üst düzeye çıkarmak**|CTRL+3|
|**Yakınlaştır**|CTRL + ARTI İŞARETİ|
|**Uzaklaştır**|CTRL + EKSİ İŞARETİ|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Komut dosyaları hata ayıklama için klavye kısayolları
Komut dosyaları ayıklarken aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye kısayolu|Kullanın.|
|----------|---------------------|----------|
|**Çalıştırma ve devam**|F5|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Girme**|F11|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Adımlama**|F10|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Dışarı Adım**|SHIFT+F11|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Görüntü çağrı yığını**|CTRL+SHIFT+D|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Liste kesme noktaları**|CTRL+SHIFT+L|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Kesme**|F9|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Tüm kesme noktalarını kaldırır**|CTRL+SHIFT+F9|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Hata ayıklayıcıyı**|SHIFT+F5|Betik bölmesinde, bir komut dosyası hata ayıklaması|

> ![Not](../core-powershell/web-access/images/Note.jpeg)**Not**
>
> İçin Windows PowerShell Konsolu komut dosyalarında Windows PowerShell ISE ayıklarken tasarlanmış klavye kısayollarını da kullanabilirsiniz. Bu kısayolları kullanmak için konsol bölmesinde kısayol yazın ve ENTER tuşuna basın.

|Eylem|Klavye kısayolu|Kullanın.|
|----------|---------------------|----------|
|**Devam etmek**|C|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Girme**|S|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Adımlama**|V|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Dışarı Adım**|O|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Son komutu yineleyin** (için adımla veya Adımlama)|ENTER|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Görüntü çağrı yığını**|K|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Hata ayıklamayı durdurun**|Q|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Komut dosyası listeler**|L|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Görüntü Konsolu komutları hata ayıklama**|H veya?|Konsol bölmesinde, bir komut dosyası hata ayıklaması|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell sekmeler için klavye kısayolları
Windows PowerShell sekmeleri kullandığınızda aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye kısayolu|
|----------|---------------------|
|**PowerShell sekmesini kapatın**|CTRL+W|
|**Yeni bir PowerShell sekmesi**|CTRL+T|
|**Önceki PowerShell sekmesi**|CTRL + SHIFT + SEKME. Hiçbir dosya herhangi bir PowerShell sekmede açık olduğunda bu kısayol çalışır.|
|**Sonraki Windows PowerShell sekmesi**|CTRL + SEKME. Hiçbir dosya herhangi bir PowerShell sekmede açık olduğunda bu kısayol çalışır.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Başlatma ve çıkma için klavye kısayolları
Windows PowerShell konsolunda (PowerShell.exe) başlatmak veya Windows PowerShell ISE çıkmak için aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye kısayolu|
|----------|---------------------|
|**Exit**|ALT+F4|
|**PowerShell.exe Başlat** (Windows PowerShell Konsolu)|CTRL+SHIFT+P|

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell ISE’yi Kullanma](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

