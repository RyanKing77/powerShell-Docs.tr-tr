---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Yazma ve komut dosyaları içinde Windows PowerShell ISE çalıştırma"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: dd3055df8c84195f0145b1a058f1d17c9c382f33
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Yazma ve komut dosyaları içinde Windows PowerShell ISE çalıştırma
Bu konu, oluşturmak, düzenlemek, çalıştırmak ve komut dosyaları betik bölmesinde Kaydet açıklar.

## <a name="how-to-create-and-run-scripts"></a>Oluşturma ve komut dosyalarını çalıştır
Açın ve Windows PowerShell betik bölmesine dosyalarında düzenleyin. Belirli dosya ilgilendiğiniz Windows PowerShell komut dosyaları (.ps1), komut dosyası veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) türleridir. Betik bölmesine Düzenleyicisi'nde renkli sözdizimi bu dosya türleridir. Betik bölmesinde açılabilir diğer ortak dosya yapılandırma dosyalarını (.ps1xml), XML dosyalarını ve metin dosyaları türleridir.

> [!NOTE]
> Windows PowerShell yürütme ilkesini betik çalıştıran ve Windows PowerShell profilleri ve yapılandırma dosyalarını yükleme olup olmadığını belirler. Varsayılan yürütme ilkesini kısıtlı, tüm komut dosyalarının çalışmasını engeller ve yükleme profilleri engeller. Yürütme İlkesi yüklenmesi ve kullanılması profilleri izin verecek şekilde değiştirmek için bkz: [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) ve [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Yeni bir komut dosyası oluşturmak için
Araç çubuğunda tıklatın **yeni** , veya **dosya** menüsünde tıklatın **yeni**. Yeni bir dosya sekmesinde geçerli PowerShell sekmesi altında oluşturulan dosya görüntülenir. Olduğunda birden fazla PowerShell sekmeleri yalnızca görünür olduğunu unutmayın. Varsayılan olarak bir dosya türü betiği (.ps1) oluşturuldu, ancak yeni adı ve uzantısı ile kaydedilebilir. Birden çok komut dosyaları aynı PowerShell sekmesindeki oluşturulabilir.

### <a name="to-open-an-existing-script"></a>Varolan bir komut dosyasını açmak için
Araç çubuğunda tıklatın **açık**, veya **dosya** menüsünde tıklatın **açık**. İçinde **açmak** iletişim kutusunda, açmak istediğiniz dosyayı seçin. Açılan dosyayı yeni bir sekmede görüntülenir.

### <a name="to-close-a-script-tab"></a>Bir komut dosyası sekmesini kapatmak için
Kapatmak istediğiniz komut dosyası komut dosyası sekmesini tıklatın, ardından aşağıdakilerden birini yapın:

1. Tıklatın **Kapat** betik sekmesindeki simgesini (X).

2. Üzerinde **dosya** menüsünde tıklatın **Kapat**.

Dosyanın son kaydedilişinden değiştirildiyse kaydedin veya atmak istenir.

### <a name="to-display-the-file-path"></a>Dosya yolu görüntülemek için
Dosya sekmesinde dosya adının üzerine gelin. Komut dosyasının tam yoluna bir araç ipucunda görüntülenir.

### <a name="to-run-a-script"></a>Bir komut dosyasını çalıştırmak için
Araç çubuğunda tıklatın **komut dosyasını Çalıştır**, veya **dosya** menüsünde tıklatın **çalıştırmak**.

### <a name="to-run-a-portion-of-a-script"></a>Bir bölümü bir komut çalıştırmak için

1. Betik bölmesinde bir betiğin bir bölümü seçin.

2. Üzerinde **dosya** menüsünde tıklatın **Seçimi Çalıştır**, veya araç çubuğunda tıklatın **Seçimi Çalıştır**.

### <a name="to-stop-a-running-script"></a>Çalışan bir komut dosyası durdurmak için
Araç çubuğunda tıklatın **durdurma işlemi**, CTRL + BREAK tuşlarına basın veya **dosya** menüsünde tıklatın **durdurma işlemi**. Tuşuna basarak **CTRL + C** bazı metinleri şu anda, bu durumda seçili değilse de çalışır **CTRL + C** kopyalama işlevi için seçili metni eşleştirir.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Yazma ve düzenleme metin betik bölmesine
Betik bölmesine metnini düzenlemek için aşağıdaki adımları kullanın. Kopyalama, kesme, yapıştırma, bulmak ve metni Değiştir. Ayrıca, Geri Al ve yalnızca gerçekleştirdiğiniz en son eylemi yinele. Bu eylemleri gerçekleştirmek için klavye kısayolları tüm Windows uygulamaları için kullanılanlarla aynıdır.

### <a name="to-enter-text-in-the-script-pane"></a>Betik bölmesinde metin girmek için

1. Betik bölmesinde herhangi bir yere tıklayarak veya tıklatarak imleci betik bölmesine gider **betik bölmesine gider** içinde **Görünüm** menüsü.

2. Bir komut dosyası oluşturun. Sözdizimi renklendirmesi ve sekme tamamlama bu Windows PowerShell ISE daha zengin bir deneyim yapın.

3. Bkz: [kullanım sekme tamamlama betik bölmesine ve konsol bölmesinde nasıl](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) yazarak de yardımcı olmak için sekme tamamlama özelliğini kullanma hakkında ayrıntılı bilgi için.

### <a name="to-find-text-in-the-script-pane"></a>Betik bölmesinde metin bulmak için

1. Herhangi bir yere metin bulmak için basın **CTRL + F** veya **Düzenle** menüsünde tıklatın **komut dosyasında bulmak**.

2. İmleci sonra metin bulmak için basın **F3** veya **Düzenle** menüsünde tıklatın **komut Sonrakini Bul**.

3. İmleç önce metin bulmak için basın **SHIFT + F3** veya **Düzenle** menüsünde tıklatın **komut Öncekini Bul**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Betik bölmesine metin bulma ve değiştirme için
Tuşuna **CRTL + H** veya **Düzenle** menüsünde tıklatın **komut dosyasında Değiştir**. Bulmak istediğiniz metin ve istediğiniz tuşuna basın ve bunun yerine metin girin **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Betik bölmesine metnin belirli bir satırın gitmek için

1. Betik bölmesinde basın **CTRL + G** veya **Düzenle** menüsünde tıklatın **satıra gitme**.

2. Bir satır numarası girin.

### <a name="to-copy-text-in-the-script-pane"></a>Betik bölmesinde metin kopyalamak için

1. Betik bölmesinde kopyalamak istediğiniz metni seçin.

2. Basın **CTRL + C** veya araç çubuğunda tıklatın **kopyalama** simgesi, veya **Düzenle** menüsünde tıklatın **kopyalama**.

### <a name="to-cut-text-in-the-script-pane"></a>Betik bölmesinde metin kesme

1. Betik bölmesinde kesmek istediğiniz metni seçin.

2. Tuşuna basın **CTRL + X** veya araç çubuğunda tıklatın **Kes** simgesi, veya **Düzenle** menüsünde tıklatın **Kes**.

### <a name="to-paste-text-into-the-script-pane"></a>Betik bölmesine metni yapıştırmak için
Tuşuna **CTRL + V** veya araç çubuğunda tıklatın **Yapıştır** simgesi, veya **Düzenle** menüsünde tıklatın **Yapıştır**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Betik bölmesine bir eylemi geri almak için
Tuşuna **CTRL + Z** veya araç çubuğunda tıklatın **geri** simgesi, veya **Düzenle** menüsünde tıklatın **geri**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Betik bölmesine eylemi yinelemek için
Tuşuna **CTRL + Y** veya araç çubuğunda tıklatın **Yinele** simgesi, veya **Düzenle** menüsünde tıklatın **Yinele**.

## <a name="how-to-save-a-script"></a>Bir komut dosyasını kaydetme
Kaydet ve bir betik adı için aşağıdaki adımları kullanın. Bir yıldız işareti, değiştirilmiş olduğundan kaydedilmedi bir dosya olarak işaretlemek için komut dosyası adı yanında görüntülenir. Dosyası kaydedildiğinde yıldız işareti kaybolur.

### <a name="to-save-a-script"></a>Bir komut dosyası kaydetmek için
Tuşuna basın **CTRL + S** veya araç çubuğunda tıklatın **kaydetmek** simgesi veya **dosya** menüsünde tıklatın **kaydetmek**.

### <a name="to-save-and-name-a-script"></a>Kaydet ve bir betik adı

1. Üzerinde **dosya** menüsünde tıklatın **Kaydet**. **Kaydet** iletişim kutusu görüntülenir.

2. İçinde **dosya adı** kutusuna, dosya için bir ad girin.

3. İçinde **farklı türde Kaydet** kutusunda, bir dosya türünü seçin. Örneğin, **farklı türde Kaydet** kutusunda ' œPowerShell komut dosyaları (\* .ps1)'.

4. **Kaydet**'e tıklayın.

### <a name="to-save-a-script-in-ascii-encoding"></a>Bir komut dosyası ASCII kodlamasında kaydetmek için
Varsayılan olarak, Windows PowerShell ISE yeni komut dosyaları (.ps1), komut dosyası veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) Unicode (BigEndianUnicode) olarak varsayılan olarak kaydeder. Â için başka bir kodlamada bir komut dosyası kaydetme ASCII (ANSI gibi), kullanın **kaydetmek** veya **Farklı Kaydet** yöntemlere [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) nesnesi.

Aşağıdaki komutu ASCII kodlama ile yeni bir komut dosyası MyScript.ps1 kaydeder.

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Aşağıdaki komutu geçerli komut dosyasını aynı ada sahip, ancak ASCII kodlama ile bir dosya ile değiştirir.

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Aşağıdaki komutu, geçerli dosyanın kodlamasını alır.

```
$psise.CurrentFile.encoding
```

Windows PowerShell ISE aşağıdaki kodlama seçeneklerini destekler: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 ve varsayılan. Varsayılan seçenek değerini sistemine göre farklılık gösterir.

Windows PowerShell ISE diğer düzenleyicilerde tarafından oluşturulan komut dosyalarını kodlama değiştirmez bile Kaydet veya Kaydet kullandığınızda, Windows PowerShell ISE komutları.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell ISE kullanma](Using-the-Windows-PowerShell-ISE.md)

