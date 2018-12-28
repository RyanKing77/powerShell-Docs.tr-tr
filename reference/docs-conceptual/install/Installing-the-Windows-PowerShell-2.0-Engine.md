---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell 2.0 Altyapısını Yükleme
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: b625b61b4e191402074f57ea2e942f800dbbcd53
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405838"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 Altyapısını Yükleme
Bu konu, Windows PowerShell 2.0 altyapısını yükleme açıklanmaktadır.

Windows PowerShell 3.0, Windows PowerShell 2.0 ile geriye dönük olarak uyumlu olacak şekilde tasarlanmıştır. Cmdlet'leri, sağlayıcıları, ek bileşenler, modülleri ve Windows PowerShell 2.0 için yazılan betikler içinde Windows PowerShell 3.0 ve Windows PowerShell 4.0 değişmeden çalıştırın. Ancak, Microsoft .NET Framework 4 çalışma zamanı etkinleştirme ilkesini bir değişiklikten dolayı Windows PowerShell ana bilgisayar Windows PowerShell 2.0 için yazılmış ve ortak dil çalışma zamanı (CLR ile) 2.0 derlenmiş bir program gerektirmeden daha sonra çalıştırılamıyor CLR 4.0 ile derlenmiş olan Windows PowerShell sürümleri.

Komutlar ve bu değişikliklerden etkilenen ana bilgisayar programlarının ile geriye dönük uyumluluk sağlamak için Windows PowerShell 2.0, Windows PowerShell 3.0 ve Windows PowerShell 4.0 altyapıları yan yana çalıştırmak için tasarlanmıştır. Ayrıca, Windows PowerShell 2.0 altyapısını Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 ve Windows Management Framework 3.0 dahildir. Mevcut bir komut dosyasının yaparken kullanılmak üzere Windows PowerShell 2.0 altyapısını amaçlanmamıştır veya Windows PowerShell 3.0, Windows PowerShell 4.0 veya Microsoft .NET Framework 4 ile uyumsuz olduğundan ana program çalıştırılamıyor. Böyle durumlarda, nadir olmaları beklenir.

Windows PowerShell 2.0 altyapısı, Windows Server 2012 R2, Windows 8.1, Windows® 8 ve Windows Server® 2012 isteğe bağlı bir özelliktir. Önceki Windows sürümlerinde Windows Management Framework 3.0, yükleme sırasında Windows PowerShell 3.0 yükleme Windows PowerShell 2.0 yükleme Windows PowerShell yükleme dizininde tamamen değiştirir. Ancak, Windows PowerShell 2.0 altyapısını korunur.

Windows PowerShell 2.0 altyapısını başlatma hakkında daha fazla bilgi için bkz: [Windows PowerShell 2.0 altyapısını başlatma](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>Windows 8.1 ve Windows 8
Windows 8.1 ve Windows 8'de, Windows PowerShell 2.0 altyapısı özelliği varsayılan olarak açıktır. Ancak, bunu kullanmak için gerektiren seçeneği için Microsoft .NET Framework 3.5, açmanız gerekir. Bu bölümde ayrıca Windows PowerShell 2.0 altyapısını özelliğini açıp kapatmak açıklanmaktadır.

#### <a name="to-turn-on-net-framework-35"></a>.NET Framework 3.5 üzerinde etkinleştirmek için

1. Üzerinde **Başlat** ekranında, yazın **Windows özellikleri**.

2. Üzerinde **uygulamaları** çubuğunda tıklatın **ayarları**ve ardından **kapatma Windows özelliklerini aç veya Kapat**.

3. İçinde **Windows özellikleri** kutusunun **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir** seçin.

    Seçtiğinizde, **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir**, özelliği yalnızca bir kısmını seçildiğini belirtmek için kutusunu doldurur. Ancak, bu Windows PowerShell 2.0 altyapısı için yeterli olur.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Windows PowerShell 2.0 altyapısını açıp kapatmak için

1. Üzerinde **Başlat** ekranında, yazın **Windows özellikleri**.

2. Üzerinde **uygulamaları** çubuğunda tıklatın **ayarları**ve ardından **kapatma Windows özelliklerini aç veya Kapat**.

3. İçinde **Windows özellikleri** kutusunda **Windows PowerShell 2.0** düğüm seçeneğine tıklayıp **Windows PowerShell 2.0 altyapısını** kutusunu seçin veya temizleyin.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>Windows Server 2012 R2 ve Windows Server 2012 üzerinde
Windows PowerShell 2.0 altyapısını ve Microsoft .NET Framework 3.5 özellikleri eklemek için aşağıdaki yordamları kullanın. Windows PowerShell 2.0 altyapısını en az Microsoft .NET Framework 2.0.50727 gerektirir. Bu gereksinim, Microsoft .NET Framework 3.5 tarafından karşılanır.

#### <a name="to-add-the-net-framework-35-feature"></a>.NET Framework 3.5 özellik eklemek için

1. İçinde **Sunucu Yöneticisi'ni**, gelen **Yönet** menüsünde **rol ve Özellik Ekle**.

    Veya **Sunucu Yöneticisi'ni**, tıklayın **tüm sunucuları**sunucu adına sağ tıklayın ve ardından **rol ve Özellik Ekle**.

2. Üzerinde **yükleme türünü** sayfasında **rol tabanlı veya özellik tabanlı yükleme**.

3. Üzerinde **özellikleri** sayfasında **.NET 3.5 Framework özellikleri** düğümünü seçip alt **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)**.

    Bu düğüm altında diğer seçenekleri için Windows PowerShell 2.0 altyapısı gerekli değildir.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Bir Windows PowerShell 2.0 altyapısı özelliği eklemek için

- İçinde **Sunucu Yöneticisi'ni**, gelen **Yönet** menüsünde **rol ve Özellik Ekle**.

    Veya **Sunucu Yöneticisi'ni**, tıklayın **tüm sunucuları**sunucu adına sağ tıklayın ve ardından **rol ve Özellik Ekle**.

- Üzerinde **yükleme türünü** sayfasında **rol tabanlı veya özellik tabanlı yükleme**.

- Üzerinde **özellikleri** sayfasında **Windows PowerShell (yüklü)** düğümünü seçip alt **Windows PowerShell 2.0 altyapısını**.

Windows PowerShell 2.0 altyapısını başlatma hakkında daha fazla bilgi için bkz: [Windows PowerShell 2.0 altyapısını başlatma](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Eski sistemlerde
[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) üzerinde Windows 7, Windows Server 2008 R2 ve Windows Server 2012'de, Windows PowerShell 4.0 sürümünü yükler. paket, Windows PowerShell 2.0 altyapısını içerir. Windows PowerShell 2.0 altyapısı gerekli ek yükleme, Kurulum veya yapılandırma olmadan etkin ve kullanıma hazır olur.

Windows PowerShell 3.0, Windows 7, Windows Server 2008 R2 ve Windows Server 2008 ' in üzerinde yükler Windows Management Framework 3.0 Paketi, Windows PowerShell 2.0 altyapısını içerir. Windows PowerShell 2.0 altyapısı gerekli ek yükleme, Kurulum veya yapılandırma olmadan etkin ve kullanıma hazır olur.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell sistem gereksinimleri](Windows-PowerShell-System-Requirements.md)
- [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md)
- [Windows PowerShell'i başlatma](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Windows PowerShell 2.0 Altyapısını Başlatma](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)