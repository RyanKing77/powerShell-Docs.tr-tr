---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: Windows powershell web erişimini kaldırma
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-windows-powershell-web-access"></a>Windows PowerShell Web Erişimini Kaldırma

Güncelleştirilmiş: 24 Haziran 2013

İçin geçerlidir: Windows Server 2012 R2, Windows Server 2012

Bu konudaki adımlarda Windows PowerShell Web erişimi ve karşılık gelen uygulama yüklü olduğu ağ geçidi sunucusundan kaldırın.

## <a name="notify-users"></a>Kullanıcıları bildir

Başlamadan önce, web tabanlı konsolun kullanıcılarına web sitesini kaldırdığınızı bildirin.

Windows PowerShell Web erişimini kaldırma IIS veya Windows PowerShell Web erişimi çalıştırmalarını gerektirdiğinden, otomatik olarak yüklenen diğer özellikler kaldırılmaz.
Kaldırma işlemi, Windows PowerShell Web erişimi bağımlı özellikleri yüklü bırakır; Bu özellikleri gerekirse ayrı ayrı kaldırabilirsiniz.

## <a name="recommended-quick-uninstallation"></a>Önerilen (hızlı) kaldırma

Bu bölümdeki yordamlar hem kaldırmanıza yardımcı:

- Windows PowerShell Web erişimi web uygulaması ve
- Windows PowerShell Web erişimi özelliği

Windows PowerShell cmdlet'lerini kullanarak.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>1. adım: cmdlet'lerini kullanarak web uygulamasını silme

1. Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

    -   Windows masaüstünde, sağ **Windows PowerShell** görev çubuğunda.

    -   Windows **Başlat** ekranında **Windows PowerShell**.

2. Tür `Uninstall-PswaWebApplication`ve tuşuna basarak **Enter**.
   1. Kendi, özel web sitesi adınızı belirttiyseniz, komutunuza `-WebsiteName` parametresini ekleyin ve web sitesi adını belirtin.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Özel bir web uygulaması kullandıysanız (varsayılan uygulama değil, **pswa**, ekleme `-WebApplicationName` parametresi, komut ve web uygulamasının adını belirtin.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Bir test sertifikası kullanıyorsanız, aşağıdaki örnekte gösterildiği gibi `DeleteTestCertificate` parametresini cmdlet’e ekleyin.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>2. adım: Windows PowerShell Web erişimi cmdlet'leri kullanarak kaldırma

1. Yükseltilmiş kullanıcı haklarıyla bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın. Bir oturum zaten açıksa sonraki adıma geçin.

    -   Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.

    -   Windows **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

1. Aşağıdaki komutu yazın ve sonra basın **Enter**, burada *bilgisayar_adı* istediğiniz Windows PowerShell Web erişimi kaldırmak bir uzak sunucuyu temsil eder. Kaldırma işlemi gerektiriyorsa `-Restart` parametresi otomatik olarak hedef sunucuları yeniden başlatır.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Çevrimdışı bir VHD’den rolleri ve özellikleri kaldırmak için hem `-ComputerName` parametresini hem de `-VHD` parametresini eklemelisiniz. `-ComputerName` parametresi, VHD’nin bağlanacağı sunucunun adını içerir ve `-VHD` parametresi de belirtilen sunucuda VHD dosyasının yolunu içerir.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Kaldırma tamamlandığında, Windows PowerShell Web erişimi açarak kaldırdığını doğrulamak **tüm sunucuları** sayfası sunucu Özelliği Kaldırdığınız sunucuyu seçip ve görüntüleme Yöneticisi ' nde **rolleri ve Özellikler** döşeme seçilen sunucunun sayfasında.

    De çalıştırabilirsiniz `Get-WindowsFeature` seçilen sunucuda hedeflenen cmdlet (Get-WindowsFeature - ComputerName &lt; *bilgisayar_adı*&gt;), sunucuda yüklü rol ve özellikleri listesini görüntülemek için.

## <a name="custom-uninstallation"></a>Özel kaldırma

Bu bölümdeki yordamlar hem Windows PowerShell Web erişimi web uygulaması hem de kaldırma roller ve Özellikler Sihirbazı'nı Sunucu Yöneticisi'nde ve IIS Yöneticisi konsolunu kullanarak Windows PowerShell Web erişimi özelliğini kaldırmanıza yardımcı.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>1. adım: IIS Yöneticisi'ni kullanarak web uygulamasını silme


1. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın. Zaten açıksa sonraki adıma geçin.

    -   Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.

    -   Windows **Başlat** adının bir kısmını ekranında, **Internet Information Services (IIS) Yöneticisi'ni**. İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.

1. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesini seçin.

1. İçinde **Eylemler** bölmesi altında **Web sitesini Yönet**, tıklatın **durdurmak**.

1. Ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesi web uygulamasında sağ tıklayın ve ardından **kaldırmak**.

1. Ağaç bölmesinde seçin **uygulama havuzları**, Windows PowerShell Web erişimi uygulama havuzu klasörünü seçin, **durdurmak** içinde **Eylemler** bölmesinde ve 'ıtıklatın **Kaldırma** içerik bölmesindeki.

1. IIS Yöneticisi’ni kapatın.

> ![Uyarı notu](images/SecurityNote.jpeg)**Not**:
>
> Sertifika kaldırma sırasında silinmez.
>
> Kendinden imzalı bir sertifika oluşturduysanız veya bir test sertifikası kullanıyor ve bunu kaldırmak istiyorsanız, IIS Yöneticisi'nde sertifikayı silin.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>2. adım: Kaldırma rol ve Özellik Ekleme Sihirbazı'nı kullanarak Windows PowerShell Web erişimini kaldırma

1. Sunucu Yöneticisi'ni zaten açıksa sonraki adıma geçin. Sunucu Yöneticisi'ni zaten açık değilse aşağıdakilerden birini yaparak açın.

    -   Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda.

    -   Windows **Başlat** ekranında **Sunucu Yöneticisi'ni**.

1. Üzerinde **Yönet** menüsünde tıklatın **rolleri ve özellikleri Kaldır**.

1. Üzerinde **Select hedef sunucu** sayfasında, özelliği kaldırmak istediğiniz sunucuyu veya çevrimdışı VHD'yi seçin. Çevrimdışı bir VHD’yi seçmek için önce VHD’nin bağlanacağı sunucuyu ve sonra VHD dosyasını seçin. Hedef sunucuyu seçtikten sonra tıklayın **sonraki**.

1. Tıklatın **sonraki** atlamak için yeniden **kaldırma özellikleri** sayfası.

1. Onay kutusunu temizleyin **Windows PowerShell Web erişimi**ve ardından **sonraki**.

1. Üzerinde **Kaldırma Seçimlerini Onayla** sayfasında, **kaldırmak**.

## <a name="see-also"></a>Ayrıca bkz:

- [Yükleme ve Windows PowerShell Web erişimini kullanma](install-and-use-windows-powershell-web-access.md)
- [IIS Yöneticisi 7.0 Yardımı](https://technet.microsoft.com/library/cc732664.aspx)