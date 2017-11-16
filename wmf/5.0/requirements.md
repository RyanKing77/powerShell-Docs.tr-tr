---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: e4e5c6fff2eea12b9cfbba325d5519f6266218e8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="system-requirements"></a>Sistem Gereksinimleri

- WMF 5.0 RTM yüklemeden önce en son Windows güncelleştirmeleri yükleyin.
- Yalnızca aşağıdaki işletim sistemlerinde WMF 5.0 RTM yükleyebilirsiniz:

    | İşletim Sistemi       | Sürümleri         | Önkoşullar        |  Paket bağlantılar |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2 KB3134758 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12 KB3134759 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | IA64 dışında tüm | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) ve [.NET Framework 4.5 veya üstü](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) yüklenir| [Win7AndW2K8R2 KB3134760 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro, Enterprise | | **x64:**[Win8.1AndW2K12R2 KB3134758 x64.msu  ](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:**[Win8.1 KB3134758 x86.msu  ](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | Tümü | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) ve [.NET Framework 4.5 veya üstü](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) yüklenir | **x64:**[Win7AndW2K8R2 KB3134760 x64.msu  ](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:**[Win7 KB3134760 x86.msu  ](http://go.microsoft.com/fwlink/?LinkID=717962)|

# <a name="installation-instructions"></a>Yükleme yönergeleri

### <a name="to-install-wmf-50-from-windows-explorer-or-file-explorer"></a>WMF 5.0 Windows Explorer (veya dosya Gezgini'ni) yüklemek için:

1. MSU dosyasının yüklediğiniz klasöre gidin.

2. Çalıştırmak için MSU çift tıklayın.

### <a name="to-install-wmf-50-from-command-prompt"></a>WMF 5.0 komut isteminden yüklemek için:

1. Bilgisayarınızın mimarisi için doğru paket indirdikten sonra yükseltilmiş kullanıcı haklarıyla (yönetici olarak çalıştır) bir komut istemi penceresi açın. Üzerinde Sunucu Çekirdeği yükleme seçenekleri Windows Server 2012 R2 veya Windows Server 2012 veya Windows Server 2008 R2 SP1, varsayılan olarak yükseltilmiş kullanıcı haklarıyla bir komut istemi açar.

2. Dizinleri içine varsa indirilen veya WMF 5.0 yükleme paketini kopyaladığınız klasöre gidin.

3. Aşağıdaki komutlardan birini çalıştırın:
    - Windows Server 2012 R2 veya Windows 8.1 x64 çalıştıran bilgisayarlarda çalıştırmak **Win8.1AndW2K12R2 KB3134758 x64.msu quiet**.
    - Windows Server 2012 çalıştıran bilgisayarlarda çalıştırmak **W2K12 KB3134759 x64.msu quiet**.
    - X 64 Windows Server 2008 R2 SP1 veya Windows 7 SP1 çalıştıran bilgisayarlarda çalıştırmak **Win7AndW2K8R2 KB3134760 x64.msu quiet**.
    - Windows 8.1 x86 çalıştıran bilgisayarlarda çalıştırmak **Win8.1 KB3134758 x86.msu quiet**.
    - X 86 Windows 7 SP1 çalıştıran bilgisayarlarda çalıştırmak **Win7 KB3134760 x86.msu quiet**.

### <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Windows Server 2008 R2 SP1 ve Windows 7 SP1 için ek yükleme notları:

Aşağıdaki önkoşulların karşılandığından emin olun:
- En son hizmet paketine yüklenir.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) yüklenir.
- [.NET framework 4.5 veya üstü](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) yüklenir.

**WMF 4.0 bağımlılık**

Windows Server 2008 R2 SP1 ve Windows 7 SP1 sistemleri yerleşik PowerShell 2.0, WinRM ve WMI sahiptir. Bu yerleşik bileşenleri güncelleştirmeleri, WMF 3.0 ve WMF 4.0 paketleri, Windows Server 2008 R2 SP1 ve Windows 7 SP1 yayımlandıktan sonra kullanıma sunulmuştur. Yükleme/kaldırma WMF 3.0 ve WMF 4.0 paketleri aşağıdaki yükseltme yolundaki bazı sorunlar sınamayla:

- Yerleşik WMF 4.0-->
- Yerleşik--> WMF 3.0 WMF4.0-->. 

Biz bu sorunların tümü WMF 4.0 paketinde düzeltti. Bu nedenle, WMF 5.0 yüklemek için Windows Server 2008 R2 SP1 ve Windows 7 SP1 WMF 4.0 bir önkoşul yoktur. Aşağıda WMF 5.0 yükseltmeden önce WMF 4.0 yüklemezseniz, karşılaşabileceğiniz belirli sorunları şunlardır:

- İletilen olayları günlüğü kullanılamıyorsa ve EventCollector günlük gösterilmesi için Olay Görüntüleyicisi'nde WMF 3.0 veya WMF 5.0 (Önkoşul WMF 4.0 yüklü) kaldırıldıktan sonra Windows 7 SP1 ve Windows Server 2008 R2 SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)).
- Özelleştirme için *PSModulePath* ortam değişkeni WMF 5.0 doğrudan yerleşik PowerShell 2. 0 yükselttiğinizde varsayılan değere sıfırlayın ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) ya da WMF 5.0 WMF 3.0. ([KB2872047](https://support.microsoft.com/en-us/kb/2872047)) Windows 7 SP1 ve Windows Server 2008 R2 SP1.

**WinRM bağımlılık**

Windows PowerShell istenen durum yapılandırması (DSC) üzerinde WinRM bağlıdır. WinRM Windows Server 2008 R2 SP1 ve Windows 7 SP1'i varsayılan olarak etkin değildir. WinRM, etkinleştirmek için bir Windows PowerShell oturumunda çalıştırın, yükseltilmiş **Set-WSManQuickConfig**.

# <a name="uninstallation-instructions"></a>Kaldırma yönergeleri

### <a name="using-command-prompt"></a>Komut istemini kullanarak

1.  Açık **komut istemi.**

2.  Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:

Windows Server 2012 R2 ve Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
Windows Server 2008 R2 SP1 ve Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

### <a name="using-control-panel"></a>Denetim Masası'nı kullanarak

1.  Açık **Denetim Masası.**

2.  Açık **programları**, ardından açık **program Kaldır.**

3.  Tıklatın **yüklü güncelleştirmeleri görüntüle.**

4.  Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden. Bu karşılık *KB3134758*, *KB3134759*, veya *KB3134760*. Tıklatın **kaldırın.**

