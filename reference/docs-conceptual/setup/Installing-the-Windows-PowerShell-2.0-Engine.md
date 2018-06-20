---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell 2.0 Altyapısını Yükleme
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: 0b3282a1a67886509e749af0f499c47fe7a99411
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952350"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 Altyapısını Yükleme
Bu konuda, Windows PowerShell 2.0 Altyapısı'nı açıklanmaktadır.

Windows PowerShell 3.0, Windows PowerShell 2.0 ile geriye dönük olarak uyumlu olacak şekilde tasarlanmıştır. Cmdlet'leri, sağlayıcıları, ek bileşenler, modüller ve Windows PowerShell 2.0 için yazılan komut dosyaları Windows PowerShell 3.0 ve Windows PowerShell 4.0 değişmeden çalıştırın. Ancak, Microsoft .NET Framework 4 çalışma zamanı etkinleştirme ilkesi değişikliği nedeniyle, Windows PowerShell 2.0 için yazılmış ve ortak dil çalışma zamanı (CLR ile) 2.0 derlenmiş Windows PowerShell konak programları değişiklik olmadan daha sonra çalıştıramaz CLR 4.0 ile derlenmiş Windows PowerShell sürümleri.

Komutları ve bu değişikliklerden etkilenir konak programları ile geriye dönük uyumluluğu korumak için Windows PowerShell 2.0, Windows PowerShell 3.0 ve Windows PowerShell 4.0 altyapılarının yan yana çalıştırmak için tasarlanmıştır. Ayrıca, Windows PowerShell 2.0 altyapısı, Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 ve Windows Management Framework 3.0 dahil edilir. Windows PowerShell 2.0 altyapısı varolan bir komut dosyasının kullanılması amaçlanmıştır veya Windows PowerShell 3.0, Windows PowerShell 4.0 veya Microsoft .NET Framework 4 ile uyumlu olmadığı için konak program çalıştırılamıyor. Bu gibi durumlarda nadir olması beklenir.

Windows PowerShell 2.0 altyapısı, Windows Server 2012 R2, Windows 8.1, Windows® 8 ve Windows Server® 2012 isteğe bağlı bir özelliktir. Windows Management Framework 3.0 yüklediğinizde, Windows'un önceki sürümlerinde, Windows PowerShell 3.0 yükleme Windows PowerShell 2.0 yükleme Windows PowerShell yükleme dizininde tamamen değiştirir. Ancak, Windows PowerShell 2.0 altyapısı korunur.

Windows PowerShell 2.0 altyapısı başlatma hakkında daha fazla bilgi için bkz: [Windows PowerShell 2.0 altyapısı başlangıç](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>Windows 8.1 ve Windows 8
Windows 8.1 ve Windows 8'de, Windows PowerShell 2.0 altyapısı özelliği varsayılan olarak açıktır. Ancak, kullanmak için bunu gerektiren seçeneği Microsoft .NET Framework 3.5, açmak gerekir. Bu bölümde ayrıca Windows PowerShell 2.0 altyapısı özelliğini açıp kapatmak açıklanmaktadır.

#### <a name="to-turn-on-net-framework-35"></a>.NET Framework 3.5 etkinleştirmek için

1. Üzerinde **Başlat** ekranında, yazın **Windows özelliklerini**.

2. Üzerinde **uygulamaları** çubuğu, tıklatın **ayarları**ve ardından **kapatma Windows özelliklerini aç veya Kapat**.

3. İçinde **Windows özelliklerini** kutusunda, **.NET Framework 3.5 (.NET 2.0 ve 3.0 dahildir** seçin.

    Seçtiğinizde, **.NET Framework 3.5 (.NET 2.0 ve 3.0 dahildir**, özelliği yalnızca bir kısmını seçildiğini belirtmek için kutusunu doldurur. Ancak, bu Windows PowerShell 2.0 altyapısı için yeterli olur.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Windows PowerShell 2.0 altyapısı üzerinde ve devre dışı bırakma

1. Üzerinde **Başlat** ekranında, yazın **Windows özelliklerini**.

2. Üzerinde **uygulamaları** çubuğu, tıklatın **ayarları**ve ardından **kapatma Windows özelliklerini aç veya Kapat**.

3. İçinde **Windows özelliklerini** kutusunda, genişletin **Windows PowerShell 2.0** düğümü ve tıklatın **Windows PowerShell 2.0 altyapısı** kutusunu işaretleyin veya temizleyin.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>Windows Server 2012 R2 ve Windows Server 2012
Windows PowerShell 2.0 altyapısı ve Microsoft .NET Framework 3.5 özellikleri eklemek için aşağıdaki yordamları kullanın. Windows PowerShell 2.0 altyapısı en az Microsoft .NET Framework 2.0.50727 gerektirir. Bu gereksinim, Microsoft .NET Framework 3.5 tarafından karşılanır.

#### <a name="to-add-the-net-framework-35-feature"></a>.NET Framework 3.5 özellik eklemek için

1. İçinde **Sunucu Yöneticisi'ni**, gelen **Yönet** menüsünde, select **rol ve Özellik Ekle**.

    Veya **Sunucu Yöneticisi'ni**, tıklatın **tüm sunucuları**bir sunucu adına sağ tıklayın ve ardından **rol ve Özellik Ekle**.

2. Üzerinde **yükleme türü** sayfasında, **rol tabanlı veya özellik tabanlı yükleme**.

3. Üzerinde **özellikleri** sayfasında **.NET 3.5 Framework özellikleri** düğümü ve select **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)**.

    Bu düğüm altındaki diğer seçenekleri için Windows PowerShell 2.0 altyapısı gerekli değildir.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Windows PowerShell 2.0 altyapısı özelliği eklemek için

- İçinde **Sunucu Yöneticisi'ni**, gelen **Yönet** menüsünde, select **rol ve Özellik Ekle**.

    Veya **Sunucu Yöneticisi'ni**, tıklatın **tüm sunucuları**bir sunucu adına sağ tıklayın ve ardından **rol ve Özellik Ekle**.

- Üzerinde **yükleme türü** sayfasında, **rol tabanlı veya özellik tabanlı yükleme**.

- Üzerinde **özellikleri** sayfasında **Windows PowerShell (yüklü)** düğümü ve select **Windows PowerShell 2.0 altyapısı**.

Windows PowerShell 2.0 altyapısı başlatma hakkında daha fazla bilgi için bkz: [Windows PowerShell 2.0 altyapısı başlangıç](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Önceki sistemlerde
[Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) Windows 7, Windows Server 2008 R2 ve Windows Server 2012'de, Windows PowerShell 4.0 sürümünü yükler paketi Windows PowerShell 2.0 altyapısı içerir. Windows PowerShell 2.0 altyapısı gerekiyorsa, ek yükleme, Kurulum ve yapılandırma olmadan etkin ve kullanıma hazır.

Windows 7, Windows Server 2008 R2 ve Windows Server 2008, Windows PowerShell 3.0 yükleyen Windows Management Framework 3.0 Paketi, Windows PowerShell 2.0 altyapısı içerir. Windows PowerShell 2.0 altyapısı gerekiyorsa, ek yükleme, Kurulum ve yapılandırma olmadan etkin ve kullanıma hazır.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell sistem gereksinimleri](Windows-PowerShell-System-Requirements.md)
- [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md)
- [Windows PowerShell'i başlatma](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Windows PowerShell 2.0 Altyapısını Başlatma](Starting-the-Windows-PowerShell-2.0-Engine.md)