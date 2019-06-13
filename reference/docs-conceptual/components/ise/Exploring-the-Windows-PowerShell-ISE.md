---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’yi Keşfetme
ms.openlocfilehash: 8c47e236e2e345a887fc3af281e429f440e176ff
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031036"
---
# <a name="exploring-the-windows-powershell-ise"></a>Windows PowerShell ISE’yi Keşfetme

Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) oluşturma, çalıştırma ve hata ayıklama komutları ve betikleri kullanabilirsiniz. Windows PowerShell ISE menü çubuğu, Windows PowerShell sekmeler, araç, betik sekmeler, bir betik bölmesinde, konsol bölmesinde, durum çubuğu, bir metin boyutu kaydırıcı ve bağlama duyarlı Yardım oluşur.

> [!NOTE]
> Komut ve çıkış bölmeleri Windows PowerShell ISE 3. 0'ile başlayan birleştirilmiş tek bir konsol bölmesine.

## <a name="menu-bar"></a>Menü çubuğu

Menü çubuğu içerir **dosya**, **Düzenle**, **görünümü**, **Araçları**, **hata ayıklama**,  **Eklentileri**, ve **yardımcı** menüleri. Menülerdeki düğmeleri yazmayı ve çalışan komut dosyaları ve çalışan komutlar Windows PowerShell ıse'de ilgili görevleri gerçekleştirmenize olanak sağlar. Ayrıca, bir [eklenti aracını](../../core-powershell/ise/The-ISEAddOnTool-Object.md) menü çubuğunda, komut dosyaları çalıştırarak yerleştirilebilir [ISE nesne modeli hiyerarşisi](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> Windows PowerShell ISE 2.0, **Araçları** ve **eklentileri** menüleri mevcut değil.

## <a name="windows-powershell-tabs"></a>Windows PowerShell sekmeleri

Bir Windows PowerShell sekmesi, bir Windows PowerShell Betiği çalıştığı ortamıdır. Yeni Windows PowerShell sekmeler, yerel bilgisayarda veya uzak bilgisayarlarda ayrı ortamlar oluşturmak için Windows PowerShell ıse'de açabilirsiniz. En fazla sekiz PowerShell sekmeleri aynı anda açık olabilir.

## <a name="toolbar"></a>Araç Çubuğu

Aşağıdaki düğmeler, araç çubuğunda yer alır.

|Düğme|İşlev|
|----------|------------|
|**Yeni**|Yeni bir komut dosyası açılır.|
|**açın**|Bir varolan komut dosyası veya dosya açar.|
|**Kaydet**|Bir komut dosyası veya dosya kaydeder.|
|**Kes**|Seçili metni keser ve panoya kopyalar.|
|**Kopyala**|Seçili metni panoya kopyalar.|
|**Yapıştır**|İmleç konumuna Pano içeriğini yapıştırır.|
|**Çıkış bölmesini temizle**|Çıkış bölmesinde tüm içeriği temizler.|
|**Geri alma**|Az önce gerçekleştirdiğiniz eylemin tersine çevirir.|
|**Yinele**|Yalnızca geri alınan eylemi gerçekleştirir.|
|**Betiği çalıştırın**|Bir betiği çalıştırır.|
|**Seçimi Çalıştır**|Seçili bir bölümü bir komut çalıştırır.|
|**Yürütmeyi durdur**|Çalışan bir komut dosyasını durdurur.|
|**Yeni Uzak PowerShell sekmesi**|Uzak bir bilgisayarda oturumunu yeni bir PowerShell sekmesi oluşturur. Bir iletişim kutusu görünür ve uzak bağlantı kurmak için gerekli ayrıntıları girmenizi ister.|
|**PowerShell.exe Başlat**|Bir PowerShell konsolu açılır.|
|**Betik bölmesinde üstü Göster**|Betik bölmesine ekranı üst taşır.|
|**Betik bölmesine sağ Göster**|Betik bölmesine ekranı sağa taşır.|
|**Tam ekran betik bölmesini göster**|Betik bölmesini en üst düzeye çıkarır.|

## <a name="script-tab"></a>Komut dosyası sekmesi

Düzenlemekte olduğunuz komut dosyasının adını görüntüler. Düzenlemek istediğiniz komut dosyası seçmek için bir betik sekmesine tıklayabilirsiniz.

Betik sekmenin üzerine geldiğinizde, betik dosyasının tam yolunu bir araç ipucu olarak görüntülenir.

## <a name="script-pane"></a>Betik bölmesi

Betik oluştur ve Çalıştır olanak sağlar. Açın, düzenlemek ve betik bölmesinde mevcut betiklerini çalıştırın.

## <a name="output-pane"></a>Çıkış bölmesi

Komutları ve betikleri çalıştırmanız sonuçlarını görüntüler. Ayrıca, kopyalayın ve çıkış bölmesinde içeriği temizleyin.

## <a name="command-pane"></a>Komut bölmesi

Komutları yazmanıza olanak sağlar. Komut bölmesinde bir bir satır veya çok satırlı komutunu çalıştırabilirsiniz. Her bir çok satırlı komut satırının girmek için SHIFT + ENTER tuşlarına basın ve çok satırlı komutu yürütmek için son satırından sonra ENTER tuşuna basın. Geçerli çalışma dizini yolu üzerinde komut bölmesinde görüntülenen istemi gösterir.

## <a name="status-bar"></a>Durum çubuğu

Çalıştırdığınız betikleri ve komutları tam olup olmadığını görmenize olanak sağlar. Durum çubuğunda çok ekranın alt kısmında ' dir. Hata iletileri seçili bölümlerini durum çubuğunda görüntülenir.

## <a name="text-size-slider"></a>Metin boyutu kaydırıcı

Artırır veya ekrana metnin boyutunu azaltır.

## <a name="help"></a>Yardım

Windows PowerShell ISE için Yardım, TechNet Kitaplığı'nda Web üzerinde kullanılabilir. Yardım'a tıklayarak açabilirsiniz **Windows PowerShell ISE Yardımı** üzerinde **yardımcı** menüsünü veya İmleç bir cmdlet adı betik bölmesine veya Konsol bölmesinde açık olduğunda dışındaki her yerde F1 tuşuna basarak. Gelen **yardımcı** menü, ayrıca Update-Help cmdlet'ini çalıştırın ve komutları oluştururken bir cmdlet parametrelerini gösteren ve parametrelerini doldurun olanak sağlayarak yardımcı olur komut penceresini görüntülemek bir kullanımı kolay formu.

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE Tanıtımı](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)
