---
ms.date: 08/14/2018
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Betik Yazma ve Çalıştırma
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405782"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Windows PowerShell ISE’de Betik Yazma ve Çalıştırma

Bu makalede, oluşturma, düzenleme, çalıştırma ve betikler betik bölmesinde Kaydet açıklar.

## <a name="how-to-create-and-run-scripts"></a>Oluşturma ve betikleri çalıştırın

Açın ve Windows PowerShell dosyaları betik bölmesine düzenleyin. Belirli dosya türleri ilgilendiğiniz Windows PowerShell komut dosyaları (.ps1), komut veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) var. Betik bölmesine Düzenleyicisi'nde renkli söz dizimi bu dosya türleridir. Betik bölmesinde açılabilir ortak diğer dosya türleri, yapılandırma dosyalarını (.ps1xml), XML dosyalarını ve metin dosyaları olan.

> [!NOTE]
> Windows PowerShell yürütme İlkesi betikleri çalıştırabilir ve Windows PowerShell profilleri ve yapılandırma dosyalarını yükleme olup olmadığını belirler. Varsayılan yürütme ilkesini kısıtlı, tüm komut dosyalarının çalışmasını engeller ve yükleme profilleri önler. Yürütme İlkesi yüklenmesi ve kullanılması profilleri izin verecek şekilde değiştirmek için bkz [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) ve [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Yeni betik dosyası oluşturmak için

Araç çubuğunda **yeni**, veya **dosya** menüsünü tıklatın **yeni**. Oluşturulan dosyanın yeni bir dosya sekmesinde geçerli bir PowerShell sekmesi altında görünür. Olduğunda birden fazla PowerShell sekmeleri yalnızca görünür olduğunu unutmayın. Bir dosya türü betik (.ps1), varsayılan olarak oluşturulur, ancak yeni bir ad ve uzantı ile kaydedilebilir. Birden çok komut dosyalarını aynı PowerShell sekmede oluşturulabilir.

### <a name="to-open-an-existing-script"></a>Varolan bir komut dosyasını açmak için

Araç çubuğunda **açık**, veya **dosya** menüsünü tıklatın **açık**. İçinde **açın** iletişim kutusunda, açmak istediğiniz dosyayı seçin. Açılan dosyayı yeni bir sekmede görünür.

### <a name="to-close-a-script-tab"></a>Bir komut dosyası sekmesini kapatmak için

Tıklayın **kapatmak** simgesini (X) Dosya sekmesini kapatın veya istediğiniz seçin **dosya** menüsüne ve ardından **kapatmak**.

Dosyanın son kez kaydedildiğinden beri değiştirilmişse kaydetmek veya atmak istenir.

### <a name="to-display-the-file-path"></a>Dosya yolu görüntülemek için

Dosya sekmesinde dosya adının üzerine gelin. Komut dosyasının tam yolu, bir araç ipucu olarak görüntülenir.

### <a name="to-run-a-script"></a>Bir betiği çalıştırmak için

Araç çubuğunda **betiğini Çalıştır**, veya **dosya** menüsünde tıklatın **çalıştırma**.

### <a name="to-run-a-portion-of-a-script"></a>Bir bölümü bir komut çalıştırmak için

1. Betik bölmesinde bir komut dosyasının bir kısmını seçin.
2. Üzerinde **dosya** menüsünü tıklatın **Seçimi Çalıştır**, veya araç çubuğunda **Seçimi Çalıştır**.

### <a name="to-stop-a-running-script"></a>Çalışan bir komut dosyası durdurmak için

Çalışan bir komut dosyası durdurmak için birkaç yolu vardır.

- Tıklayın **durdurma işlemi** araç
- CTRL + BREAK tuşlarına basın.
- Seçin **dosya** menüsüne ve ardından **durdurma işlemi**.

Tuşuna basarak **CTRL + C** metindir, bu durumda seçili olan sürece de çalışır **CTRL + C** kopyalama işlevi için seçili metni eşleştirir.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Yazma ve düzenleme metin betik bölmesine

Kopyalama, kesme, yapıştırın, bulmak ve metin betik bölmesine değiştirin. Ayrıca Al ve az önce gerçekleştirdiğiniz son eylemi yineleyin. Bu eylemler için klavye kısayolları tüm Windows uygulamaları için kullanılan aynı kısayollarıdır.

### <a name="to-enter-text-in-the-script-pane"></a>Betik bölmesinde metin girmek için

1. İmleci betik bölmesine bir betik bölmesinde herhangi bir yere tıklayarak veya tıklayarak taşıma **betik bölmesine gidin** içinde **görünümü** menüsü.
2. Bir komut dosyası oluşturun. Söz dizimi renklendirme ve sekme tamamlama, Windows PowerShell ıse'de daha zengin bir düzenleme deneyimi sağlar.
3. Bkz: [betik bölmesi ve konsol bölmesinde sekme tamamlamayı kullanma nasıl](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) metin yardımcı olmak için sekmesinde Tamamlama özelliğini kullanmayla ilgili ayrıntılar için.

### <a name="to-find-text-in-the-script-pane"></a>Betik bölmesinde metni bulmak için

1. Herhangi bir metni bulmak için basın **CTRL + F** veya **Düzenle** menüsünde tıklayın **betikte Bul**.
2. İmleci sonra metni bulmak için basın **F3** veya **Düzenle** menüsünde tıklatın **betiğinde Sonrakini Bul**.
3. İmleç önce metni bulmak için basın **SHIFT + F3** veya **Düzenle** menüsünde tıklatın **betiğinde Öncekini Bul**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Betik bölmesine metin bulma ve değiştirme için

Tuşuna **CTRL + H** veya **Düzenle** menüsünde tıklatın **betikte değiştirin**. İstediğiniz metin bulma ve değiştirme metnini girin tuşuna **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Betik bölmesindeki metnin belirli bir satıra Git

1. Betik bölmesinde basın **CTRL + g'tuşlarını** veya **Düzenle** menüsünde tıklatın **satıra Git**.

2. Bir satır numarası girin.

### <a name="to-copy-text-in-the-script-pane"></a>Betik bölmesinde metin kopyalamak için

1. Betik bölmesinde kopyalamak istediğiniz metni seçin.

2. Tuşuna **CTRL + C** veya araç çubuğunda **kopyalama** simgesini veya **Düzenle** menüsünde tıklayın **kopyalama**.

### <a name="to-cut-text-in-the-script-pane"></a>Betik bölmesinde metni kesmek için

1. Betik bölmesinde kesmek istediğiniz metni seçin.
2. Tuşuna **CTRL + X** veya araç çubuğunda **Kes** simgesini veya **Düzenle** menüsünde tıklayın **Kes**.

### <a name="to-paste-text-into-the-script-pane"></a>Betik bölmesine metni yapıştırmak için

Tuşuna **CTRL + V** veya araç çubuğunda **Yapıştır** simgesini veya **Düzenle** menüsünde tıklayın **Yapıştır**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Betik bölmesine bir eylemi geri almak için

Tuşuna **CTRL + Z** veya araç çubuğunda **geri** simgesini veya **Düzenle** menüsünde tıklayın **geri**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Betik bölmesine bir eylemi yinelemek için

Tuşuna **CTRL + Y** veya araç çubuğunda **Yinele** simgesini veya **Düzenle** menüsünde tıklayın **Yinele**.

## <a name="how-to-save-a-script"></a>Bir komut dosyasını kaydetme

Bunu değiştirilmesinden bu yana kaydedilmemiş bir dosyayı işaretlemek için betik adının yanında bir yıldız işareti görünür. Dosya kaydedildiğinde yıldız işareti kaybolur.

### <a name="to-save-a-script"></a>Bir betiği kaydetmek için

Basın **CTRL + S** veya araç çubuğunda **Kaydet** simgesi veya **dosya** menüsünde tıklayın **Kaydet**.

### <a name="to-save-and-name-a-script"></a>Kaydet ve bir betik adı

1. Üzerinde **dosya** menüsünde tıklatın **Kaydet**. **Kaydet** iletişim kutusu görüntülenir.
2. İçinde **dosya adı** kutusuna, dosya için bir ad girin.
3. İçinde **farklı kaydetme türü** kutusunda, bir dosya türünü seçin. Örneğin, **farklı kaydetme türü** kutusunda ' PowerShell betikleri (\*.ps1)'.
4. **Kaydet**'e tıklayın.

### <a name="to-save-a-script-in-ascii-encoding"></a>ASCII kodlaması bir komut dosyası kaydetmek için

Varsayılan olarak, Windows PowerShell ISE yeni komut dosyaları (.ps1), komut veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) Unicode (BigEndianUnicode) olarak varsayılan olarak kaydeder. Â için başka bir kodlama, bir komut dosyası kaydetme ASCII (ANSI gibi), kullanın **Kaydet** veya **Farklı Kaydet** yöntemlerde [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) nesne.

Aşağıdaki komut, yeni bir betik ASCII kodlaması ile MyScript.ps1 kaydeder.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Aşağıdaki komutu, geçerli komut dosyasını bir dosyayla aynı ada sahip, ancak ASCII kodlaması ile değiştirir.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Aşağıdaki komut, geçerli dosyanın kodlamasını alır.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE aşağıdaki kodlama seçeneklerini destekler: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 ve varsayılan. Varsayılan seçenek değerini sistemine göre farklılık gösterir.

Windows PowerShell ISE Kaydet veya Kaydet kullandığınızda komut dosyaları, kodlama değiştirmez komutları.

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE’yi Keşfetme](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
