---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: Windows powershell web erişimini kaldırma
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405939"
---
# <a name="uninstall-windows-powershell-web-access"></a>Windows PowerShell Web Erişimini Kaldırma

Güncelleştirme tarihi: 24 Haziran 2013

Şunun için geçerlidir: Windows Server 2012 R2, Windows Server 2012

Bu konu başlığındaki adımları karşılık gelen uygulama ve Windows PowerShell Web Erişimi Web sitesinin yüklü olduğu ağ geçidi sunucusundan kaldırın.

## <a name="notify-users"></a>Kullanıcılara bildirme

Başlamadan önce, web tabanlı konsolun kullanıcılarına web sitesini kaldırdığınızı bildirin.

Windows PowerShell Web erişimini kaldırma, IIS veya çalıştırmak için Windows PowerShell Web erişimi için gerekli olduğundan, otomatik olarak yüklenen diğer özellikler kaldırılmaz.
Kaldırma işlemi, Windows PowerShell Web erişimi bağımlı özellikleri yüklü bırakır; Bu özellikleri gerekirse ayrı ayrı kaldırabilirsiniz.

## <a name="recommended-quick-uninstallation"></a>Önerilen (hızlı) kaldırma

Bu bölümdeki yordamlar hem kaldırmanıza yardımcı:

- Windows PowerShell Web erişimi web uygulaması ve
- Windows PowerShell Web erişim özelliği

Windows PowerShell cmdlet'lerini kullanarak.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Adım 1: Cmdlet'lerini kullanarak web uygulamasını silme

1. Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

    -   Windows masaüstünde, sağ **Windows PowerShell** görev.

    -   Windows üzerinde **Başlat** ekranında **Windows PowerShell**.

2. Tür `Uninstall-PswaWebApplication`ve tuşuna **Enter**.
   1. Kendi, özel web sitesi adınızı belirttiyseniz, komutunuza `-WebsiteName` parametresini ekleyin ve web sitesi adını belirtin.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Özel bir web uygulaması kullandıysanız (varsayılan uygulama **pswa**, ekleme `-WebApplicationName` parametresini komutunuza, web uygulamasının adını belirtin.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Bir test sertifikası kullanıyorsanız, aşağıdaki örnekte gösterildiği gibi `DeleteTestCertificate` parametresini cmdlet’e ekleyin.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Adım 2: Cmdlet'lerini kullanarak Windows PowerShell Web erişimini kaldırma

1. Bir Windows PowerShell oturumu yükseltilmiş kullanıcı haklarıyla açmak için aşağıdakilerden birini yapın. Bir oturum zaten açıksa sonraki adıma geçin.

    -   Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.

    -   Windows üzerinde **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

1. Aşağıdaki komutu yazın ve ardından basın **Enter**burada *bilgisayar_adı* Windows PowerShell Web erişimini kaldırmak istediğiniz uzak bir sunucuyu temsil eder. Kaldırma işlemi gerektiriyorsa `-Restart` parametresi otomatik olarak hedef sunucuları yeniden başlatır.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Çevrimdışı bir VHD’den rolleri ve özellikleri kaldırmak için hem `-ComputerName` parametresini hem de `-VHD` parametresini eklemelisiniz. `-ComputerName` parametresi, VHD’nin bağlanacağı sunucunun adını içerir ve `-VHD` parametresi de belirtilen sunucuda VHD dosyasının yolunu içerir.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Kaldırma tamamlandığında, Windows PowerShell Web erişimi açarak kaldırdığını doğrulamak **tüm sunucuları** sayfası sunucu Özelliği Kaldırdığınız bir sunucuyu seçerek ve görüntüleme Yöneticisi ' nde **rolleri ve Özellikleri** döşeme sonra seçtiğiniz sunucu için sayfadaki.

    Da çalıştırabilirsiniz `Get-WindowsFeature` seçilen sunucuda hedeflenen cmdlet (Get-WindowsFeature - ComputerName &lt; *bilgisayar_adı*&gt;), sunucuda yüklü rol ve özellikleri bir listesini görüntülemek için.

## <a name="custom-uninstallation"></a>Özel kaldırma

Bu bölümdeki yordamlar hem Windows PowerShell Web erişimi web uygulamasını hem de Kaldır rolleri ve özellikleri Sihirbazı'nı Sunucu Yöneticisi'nde ve IIS Yöneticisi konsolunu kullanarak Windows PowerShell Web erişimi özelliğini kaldırmanıza yardımcı olur.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Adım 1: IIS Yöneticisi'ni kullanarak web uygulamasını silme


1. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın. Zaten açıksa sonraki adıma geçin.

    -   Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.

    -   Windows üzerinde **Başlat** ekranında, adının bir kısmını **Internet Information Services (IIS) Yöneticisi'ni**. İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.

1. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesini seçin.

1. İçinde **eylemleri** bölmesi altında **Web sitesini Yönet**, tıklayın **Durdur**.

1. Ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesindeki web uygulamaya sağ tıklayın ve ardından **Kaldır**.

1. Ağaç bölmesinde seçin **uygulama havuzları**, Windows PowerShell Web erişimi uygulama havuzu klasörünü seçin, **Durdur** içinde **eylemleri** bölmesinde ve 'yetıklayın **Kaldırma** içerik bölmesinde.

1. IIS Yöneticisi’ni kapatın.

> ![Uyarı Not](images/SecurityNote.jpeg)**Not**:
>
> Sertifika kaldırma sırasında silinmez.
>
> Kendinden imzalı bir sertifika oluşturduysanız veya bir test sertifikası kullanıyor ve bunu kaldırmak istiyorsanız, IIS Yöneticisi'nde sertifikayı silin.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Adım 2: Kaldır rolleri ve özellikleri Sihirbazı'nı kullanarak Windows PowerShell Web erişimini kaldırma

1. Sunucu Yöneticisi zaten açıksa sonraki adıma geçin. Sunucu Yöneticisi'ni zaten açık değilse aşağıdakilerden birini yaparak açın.

    -   Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda.

    -   Windows üzerinde **Başlat** ekranında **Sunucu Yöneticisi**.

1. Üzerinde **Yönet** menüsünü tıklatın **Kaldır rolleri ve özellikleri**.

1. Üzerinde **hedef sunucuyu seçin** sayfasında, özelliği kaldırmak istediğiniz sunucuyu veya çevrimdışı VHD'yi seçin. Çevrimdışı bir VHD’yi seçmek için önce VHD’nin bağlanacağı sunucuyu ve sonra VHD dosyasını seçin. Hedef sunucuyu seçtikten sonra tıklayın **sonraki**.

1. Tıklayın **sonraki** atlamak için yeniden **Özellik Kaldır** sayfası.

1. Onay kutusunu temizleyin **Windows PowerShell Web erişimi**ve ardından **sonraki**.

1. Üzerinde **kaldırma seçimlerini onaylayın** sayfasında **Kaldır**.

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell Web erişimi yükleme ve kullanma](install-and-use-windows-powershell-web-access.md)
- [IIS Yöneticisi 7.0 Yardımı](https://technet.microsoft.com/library/cc732664.aspx)