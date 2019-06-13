---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de erişilebilirlik
ms.openlocfilehash: 416b18dd492ca04d98b5adf9f7f0f88ea495740a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030642"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Windows PowerShell ISE’de erişilebilirlik

Bu konu, Windows PowerShell Tümleşik komut dosyası ortamı (yararlı bulabileceğiniz ISE) erişilebilirlik özelliklerini açıklar.

* [Betik bölmesi ve konsol konumunu ve boyutunu değiştirme](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Metin düzenleme için klavye kısayolları](#keyboard-shortcuts-for-editing-text)
* [Komut dosyaları çalıştırmak için klavye kısayolları](#keyboard-shortcuts-for-running-scripts)
* [Görünümü özelleştirme için klavye kısayolları](#keyboard-shortcuts-for-customizing-the-view)
* [Hata ayıklama betikleri için klavye kısayolları](#keyboard-shortcuts-for-debugging-scripts)
* [Windows PowerShell sekmeler için klavye kısayolları](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Başlangıç ve çıkma için klavye kısayolları](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft, ürünlerinin ve hizmetlerinin kullanımını herkes için kolaylaştıracağını taahhüt eder. Aşağıdaki konular, özellikler, ürünler ve Windows PowerShell ISE engelli kişiler için daha erişilebilir hale getiren hizmetleri hakkında bilgi sağlar.

Windows PowerShell ISE yüksek karşıtlık modunu destekler. Görme engelli için kesme noktası bilgileri, kesme noktaları, gibi yönetmek için cmdlet'leri aracılığıyla sunulur [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) ve [kümesi PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Daha fazla bilgi için lütfen ' kesme noktalarını yönetin ' içinde bakın [Windows PowerShell ISE'de betiklerde hata ayıklama nasıl](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Erişilebilirlik özelliklerine ve Microsoft Windows yardımcı programları ek olarak, aşağıdaki özellikler Windows PowerShell ISE daha erişilebilir engelli kişiler için hale getirir:

- Klavye Kısayolları

- Söz dizimi renklerini tablo ve birkaç kullanarak diğer renk ayarlarını değiştirme olanağı [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) betik oluşturma nesne.

- Metin boyutunu değiştir

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Betik bölmesi ve konsol konumunu ve boyutunu değiştirme

Konsol bölmesinde ve betik bölmesini konumunu ve boyutunu değiştirmek için aşağıdaki adımları kullanabilirsiniz. Windows PowerShell ISE yeniden açtığınızda yaptığınız değişiklikleri boyut ve konum korunur.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Betik bölmesi ve konsol bölmesinde yeniden boyutlandırmak için

1. Betik bölmesi ve konsol bölmesinde arasında bölünmüş satıra işaretçi duraklatın.

2. Kenarlık bölmesinin boyutunu değiştirmek için fare işaretçisini bir iki başlı oka dönüştüğünde sürükleyin.

### <a name="to-move-the-script-pane-and-console-pane"></a>Betik bölmesi ve konsol bölmesinde taşımak için

Aşağıdakilerden birini yapın:

- Konsolunda bölmesinin üstündeki betik bölmesine taşımak için basın **CTRL + 1** veya araç çubuğunda **Göster betik bölmesinde üst** simgesini veya **görünümü** menüsünde tıklayın **Göster Betik bölmesindeki ilk**.

- Betik bölmesini konsolunda bölmesinin sağa taşımak için basın **CTRL + 2** veya araç çubuğunda **Göster betik bölmesinde sağ** simgesini veya **görünümü** menüsünde tıklayın**Betik bölmesine sağ Göster getirin**.

- Betik bölmesini en üst düzeye çıkarmak için basın **CTRL + 3** veya araç çubuğunda **betik bölmesine ekranı göster** simgesini veya **görünümü** menüsünde tıklayın **komut dosyasını Göster Tam ekran bölmesinde**.

- Konsol bölmesinde en üst düzeye çıkarmak ve sekme, satır sağ kenarında betik Bölmesini Gizle **betik Bölmesini Gizle** simgesi, **görünümü** menüsü, seçimini kaldırmak için tıklayın **betikbölmesinigöster** menü seçeneği.

- Konsol bölmesinde, sekme, satır sağ kenarında büyütüldüğünde betik bölmesini görüntülemek için tıklatın **betik bölmesini göster** simgesini veya **görünümü** menüsü, seçmek için tıklatın **komut dosyasını Göster Bölmesinde** menü seçeneği.

## <a name="keyboard-shortcuts-for-editing-text"></a>Metin düzenleme için klavye kısayolları

Metin düzenlerken aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye Kısayolları|Kullanın|
|----------|----------------------|----------|
|**Kopyala**|CTRL+C|Betik bölmesi, konsolu bölmesi|
|**Kes**|CTRL+X|Betik bölmesi, konsolu bölmesi|
|**Betikte Bul**|CTRL+F|Betik bölmesi|
|**Betikte Sonrakini Bul**|F3|Betik bölmesi|
|**Betikte Öncekini Bul**|SHIFT+F3|Betik bölmesi|
|**Yapıştır**|CTRL+V|Betik bölmesi, konsolu bölmesi|
|**Yinele**|CTRL+Y|Betik bölmesi, konsolu bölmesi|
|**Betikte değiştirin**|CTRL+H|Betik bölmesi|
|**Kaydet**|CTRL+S|Betik bölmesi|
|**Tümünü Seç**|CTRL+A|Betik bölmesi, konsolu bölmesi|
|**Geri alma**|CTRL+Z|Betik bölmesi, konsolu bölmesi|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Komut dosyaları çalıştırmak için klavye kısayolları

Betik bölmesinde komut dosyalarını çalıştırdığınızda, aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye Kısayolu|
|----------|---------------------|
|**Yeni**|CTRL+N|
|**açın**|CTRL+O|
|**Çalıştırma**|F5|
|**Seçimi Çalıştır**|F8|
|**Yürütmeyi durdur**|CTRL + BREAK. CTRL + C (hiçbir metin seçili olduğunda) bağlam belirsiz olduğunda kullanılabilir.|
|**Sekme** (için sonraki komut dosyası)|CTRL + SEKME **Not:** Sonraki komut dosyası için sekmesinde yalnızca tek bir PowerShell sekmesi açın varsa ya da birden fazla PowerShell sekmeyi Aç varsa, ancak betik bölmesinde odağı olan çalışır.|
|**Sekme** (için önceki betik)|CTRL + SHIFT + SEKME **Not:** Önceki komut dosyası için sekmesinde, yalnızca bir PowerShell sekmesi açın sahip olduğunuzda veya sahip olduğunuz birden fazla PowerShell sekmesini açın ve odağı betik bölmesinde ise çalışır.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Görünümü özelleştirme için klavye kısayolları

Windows PowerShell ıse'de görünümünü özelleştirmek için aşağıdaki klavye kısayollarını kullanabilirsiniz. Uygulamanın tüm bölmelerde bunlara erişilebilir.

|Eylem|Klavye Kısayolu|
|----------|---------------------|
|**Konsol bölmesine gidin**|CTRL+D|
|**Betik bölmesine gidin**|CTRL+I|
|**Betik bölmesini göster**|CTRL+R|
|**Betik Bölmesini Gizle**|CTRL+R|
||
|**Betik bölmesine Yukarı Taşı**|CTRL+1|
|**Betik bölmesine Sağa Taşı**|CTRL+2|
|**Betik bölmesine en üst düzeye çıkarın**|CTRL+3|
|**Yakınlaştır**|CTRL + ARTI İŞARETİ|
|**Uzaklaştır**|CTRL + EKSİ İŞARETİ|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Hata ayıklama betikleri için klavye kısayolları

Betik hata ayıklaması yaparken, aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye Kısayolu|Kullanın|
|----------|---------------------|----------|
|**Çalıştırma ve devam**|F5|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Adımla**|F11|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Üzerinden adımla**|F10|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Dışına adımla**|SHIFT + F11|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Çağrı yığınını görüntüleme**|CTRL+SHIFT+D|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Liste kesme noktaları**|CTRL+SHIFT+L|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**İki durumlu kesme noktası**|F9|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Tüm kesme noktalarını Kaldır**|CTRL+SHIFT+F9|Betik bölmesinde, bir komut dosyası hata ayıklaması|
|**Hata ayıklayıcıyı durdurun**|SHIFT + F5|Betik bölmesinde, bir komut dosyası hata ayıklaması|

> [!NOTE]
>
> Ayrıca, Windows PowerShell ISE'de betiklerde hata ayıklaması yaparken Windows PowerShell Konsolu için tasarlanan klavye kısayollarını kullanabilirsiniz. Bu kısayollar kullanmak için konsol bölmesinde kısayolunu yazın ve ENTER'a basın.

|Eylem|Klavye Kısayolu|Kullanın|
|----------|---------------------|----------|
|**Continue**|C|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Adımla**|S|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Üzerinden adımla**|V|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Dışına adımla**|O|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Son komutu yineleyin** (için adımla veya Adımlama)|ENTER|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Çağrı yığınını görüntüleme**|K|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Hata ayıklamayı Durdur**|Q|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Komut listesi**|M|Konsol bölmesinde, bir komut dosyası hata ayıklaması|
|**Konsolu komutları hata ayıklama**|H veya?|Konsol bölmesinde, bir komut dosyası hata ayıklaması|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell sekmeler için klavye kısayolları

Windows PowerShell sekmeleri kullandığınızda aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye Kısayolu|
|----------|---------------------|
|**PowerShell sekmesini kapatın**|CTRL+W|
|**Yeni bir PowerShell sekmesi**|CTRL+T|
|**Önceki PowerShell sekmesi**|CTRL+SHIFT+TAB. Bu kısayol, hiçbir dosya herhangi bir PowerShell sekme üzerinde açık olduğunda çalışır.|
|**Sonraki Windows PowerShell sekmesi**|CTRL+TAB. Bu kısayol, hiçbir dosya herhangi bir PowerShell sekme üzerinde açık olduğunda çalışır.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Başlangıç ve çıkma için klavye kısayolları

(PowerShell.exe) Windows PowerShell Konsolu başlatın veya Windows PowerShell ISE çıkmak için aşağıdaki klavye kısayollarını kullanabilirsiniz.

|Eylem|Klavye Kısayolu|
|----------|---------------------|
|**Çıkış**|ALT+F4|
|**PowerShell.exe Başlat** (Windows PowerShell Konsolu)|CTRL+SHIFT+P|

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell ISE Tanıtımı](Introducing-the-Windows-PowerShell-ISE.md)
