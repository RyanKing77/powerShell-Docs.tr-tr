---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell ISE keşfetme"
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 979209d4b200728b7e78e341bb9595741d2b8e68
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="exploring-the-windows-powershell-ise"></a>Windows PowerShell ISE keşfetme
Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) oluşturmak, çalıştırmak ve komutları ve komut dosyaları hata ayıklamak için kullanabilirsiniz. Windows PowerShell ISE menü çubuğunda, Windows PowerShell sekmeler, araç, komut dosyası sekmeler, bir betik bölmesinde, bir konsol bölmesinde, durum çubuğu, bir metin boyutu kaydırıcı ve bağlama duyarlı Yardım oluşur.

> [!NOTE]
> Komut ve çıktı bölmeleri Windows PowerShell ISE 3.0 ile başlayarak birleşik tek bir konsol bölmesine.

## <a name="menu-bar"></a>Menü çubuğu
Menü çubuğu içerir **dosya**, **Düzenle**, **Görünüm**, **Araçları**, **hata ayıklama**,  **Eklentiler**, ve **yardımcı** menüleri. Menülerde düğmeleri yazılırken ve çalışan komut dosyaları ve Windows PowerShell ISE çalışan komutlar ilgili görevleri gerçekleştirmenize olanak sağlar. Ayrıca, bir [eklenti aracı](../../core-powershell/ise/The-ISEAddOnTool-Object.md) menü çubuğunda, komut dosyaları çalıştırarak yerleştirilebilir [Windows PowerShell ISE komut dosyası nesne modeli](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md).

> [!NOTE]
> Windows PowerShell ISE 2.0 **Araçları** ve **eklentileri** menüleri mevcut değil.

## <a name="windows-powershell-tabs"></a>Windows PowerShell sekmeleri
Bir Windows PowerShell sekmesi bir Windows PowerShell Betiği çalıştığı ortamıdır. Yeni Windows PowerShell sekmeler, yerel bilgisayarda veya uzak bilgisayarlarda ayrı ortamlar oluşturmak için Windows PowerShell ISE açabilirsiniz. En fazla sekiz PowerShell sekmeleri aynı anda açık olabilir.

## <a name="toolbar"></a>Araç çubuğu
Aşağıdaki düğmeler araç çubuğunda yer alır.

|Düğmesi|İşlev|
|----------|------------|
|**Yeni**|Yeni bir komut dosyası açar.|
|**Açık**|Varolan komut dosyası veya dosya açar.|
|**Kaydet**|Bir komut dosyası veya dosya kaydeder.|
|**Kes**|Seçili metni keser ve Pano'ya kopyalar.|
|**Kopyalama**|Seçili metni panoya kopyalar.|
|**Yapıştır**|İmlecin konumundaki Pano içeriğini gönderebilir.|
|**Çıkış bölmesinde temizleyin**|Çıkış bölmesinde tüm içeriği siler.|
|**Geri alma**|Yalnızca gerçekleştirilen eylem tersine çevirir.|
|**Yinele**|Yalnızca geri alınan eylemi gerçekleştirir.|
|**Komut dosyasını çalıştır**|Bir komut dosyasını çalıştırır.|
|**Selction Çalıştır**|Bir komut dosyası seçili bir bölümünü çalışır.|
|**Yürütme Durdur**|Çalışan bir komut dosyasını durdurur.|
|**Yeni Uzak PowerShell sekmesi**|Uzak bir bilgisayarda oturum kurar yeni bir PowerShell sekmesi oluşturur. Bir iletişim kutusu görünür ve uzak bağlantı kurmak için gerekli ayrıntıları girmenizi ister.|
|**PowerShell.exe Başlat**|Bir PowerShell konsolunu açar.|
|**Betik bölmesinde üstü Göster**|Betik bölmesine görünen üst taşır.|
|**Betik bölmesine sağ Göster**|Betik bölmesine görüntü sağa taşır.|
|**Tam ekran betik bölmesini göster**|Betik bölmesine en üst düzeye çıkarır.|

## <a name="script-tab"></a>Komut dosyası sekmesi
Düzenlemekte olduğunuz komut dosyasının adını görüntüler. Düzenlemek istediğiniz komut dosyasını seçmek için bir komut dosyası sekmesini tıklatabilirsiniz.

Komut dosyası sekmesini üzerine geldiğinizde, komut dosyasının tam yolunu ipucunda görüntülenir.

## <a name="script-pane"></a>Komut dosyası bölmesi
Oluşturmak ve komut dosyaları çalıştırmak sağlar. Açın, düzenlemek ve betik bölmesinde varolan betikleri çalıştırın.

## <a name="output-pane"></a>Çıkış bölmesi
Komutları ve komut dosyalarını çalıştırdığınızda sonuçlarını görüntüler. Ayrıca, kopyalamak ve içeriği çıkış bölmesinde temizleyin.

## <a name="command-pane"></a>Komut bölmesi
Komutları yazmanızı sağlar. Komut Bölmesi'nde, bir tek bir çizgi veya çok satırlı komutunu çalıştırabilirsiniz. Her bir çok satırlı komut satırının girmek için SHIFT + ENTER tuşuna basın ve çok satırlı komutu yürütmek için son satırından sonra ENTER tuşuna basın. Komut bölmesinin en üstünde istemini geçerli çalışma dizini yolu gösterir.

## <a name="status-bar"></a>Durum çubuğu
Komutlar ve, çalışan bir komut dosyası tam olup olmadığını görmenize olanak sağlar. Durum çubuğu görüntü çok alt kısmında vardır. Hata iletileri seçili bölümlerini durum çubuğunda görüntülenir.

## <a name="text-size-slider"></a>Metin boyutu kaydırıcı
Artırır veya ekran üzerindeki metnin boyutunu azaltır.

## <a name="help"></a>Yardım
Windows PowerShell ISE için Yardım, TechNet Kitaplığı'nda Web'de kullanılabilir. Yardım'a tıklayarak açabilirsiniz **Windows PowerShell ISE Yardımı** üzerinde **yardımcı** menü imleci cmdlet adı betik bölmesine veya Konsol bölmesinde üzerinde olduğunda dışında herhangi bir yere F1 tuşuna basarak veya. Gelen **yardımcı** menüsü, da Update-Help cmdlet'ini çalıştırın ve tüm bir cmdlet parametreleri gösteren ve parametrelerinde doldurmak sağlayarak tarafından komutları oluştururken yardımcı olur komut penceresini görüntülemek bir kullanımı kolay formu.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell ISE kullanma](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

