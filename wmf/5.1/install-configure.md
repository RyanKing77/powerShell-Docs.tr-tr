---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: keithb
title: "Yükleme ve WMF 5.1 yapılandırma"
ms.openlocfilehash: f58676de6f7a5c51ba586a8c607097af8e60d0c9
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2018
---
# <a name="install-and-configure-wmf-51"></a>Yükleme ve WMF 5.1 yapılandırma #


## <a name="download-and-install-the-wmf-51-package"></a>WMF 5.1 paketini indirin ve yükleyin

Yüklemek istediğiniz işletim sistemi ve mimarisi için WMF 5.1 paketini indirin:

| İşletim Sistemi       | Önkoşullar           | Paket bağlantılar                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Windows Server 2008 R2 ve Windows 7 için WMF 5.1 yükleyin

> **Not:** yükleme yönergeleri için Windows Server 2008 R2 ve Windows 7 değişmiş ve diğer paketleri yönergelerini farklıdır. Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için yükleme yönergeleri aşağıda verilmiştir.

**Windows Server 2008 R2 ve Windows 7 WMF 5.1 yükleme**

1. ZIP dosyasının yüklediğiniz klasöre gidin.

2. ZIP dosyasını sağ tıklatın ve "Extract tüm..." öğesini seçin. Zip 2 dosyaları içerir: bir MSU ve yükleme WMF5.1.PS1 komut dosyasıdır.
ZIP dosyası açılmış sonra Windows 7 veya Windows Server 2008 R2 çalıştıran herhangi bir makineye içeriği kopyalayabilirsiniz.

3. ZIP dosyasının içeriğini ayıkladıktan, yönetici olarak PowerShell'i açın, sonra ZIP dosyasının içeriğini içeren klasöre gidin.

4. Bu klasöre yükle Wmf5.1.ps1 komut dosyasını çalıştırın ve yönergeleri izleyin. Bu komut dosyası yerel makine üzerinde önkoşulları denetleyin ve Önkoşullar karşılanıyorsa WMF 5.1 yükleyin. Önkoşullar aşağıda listelenmiştir.

Yükleme WMF5.1.ps1 Windows Server 2008 R2 ve Windows 7 yüklemesinde otomatikleştirme kolaylaştırmak için aşağıdaki parametreleri alır:

- AcceptEula: Bu parametreyi dahil edildiğinde EULA'yı otomatik olarak kabul edilir ve görüntülenmeyecek.
- AllowRestart: Bu parametre, yalnızca AcceptEula belirtilmişse kullanılabilir. Bu parametre bulunur ve WMF 5.1 yükledikten sonra bir yeniden başlatma gerekli ise, yeniden yüklemesi tamamlandıktan hemen sonra sormadan gerçekleşir.

**WMF 5.1 Windows Server 2008 R2 SP1 ve Windows 7 SP1 için Önkoşullar**

Windows Server 2008 R2 SP1 ya da Windows 7 SP1, WMF 5.1 yükleme aşağıdakileri gerektirir:
- En son hizmet paketi yüklü olmalıdır.
- WMF 3.0 **bulunmamalıdır** yüklü olmalıdır. WMF 3.0 WMF 5.1 yükleme diğer uygulamaların başarısız olmasına neden olabilir PSModulePath kaybına neden olur. WMF 5.1'ı yüklemeden önce ya da yüklemeyi WMF 3.0 veya PSModulePath kaydedin ve WMF 5.1 yüklemesi tamamlandıktan sonra sonra onu el ile geri yüklemelisiniz.
- WMF 5.1 en azından [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Microsoft .NET Framework 4.5.2 yükleme konumundan yönergeleri izleyerek yükleyebilirsiniz.

**WinRM bağımlılık**

Windows PowerShell istenen durum yapılandırması (DSC) üzerinde WinRM bağlıdır.
WinRM Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değildir.
Çalıştırma `Set-WSManQuickConfig`, Windows PowerShell'de yükseltilmiş WinRM etkinleştirmek için oturumu.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için WMF 5.1 yükleyin
**Windows Gezgini (veya dosya Gezgini'nde, Windows Server 2012 R2 veya Windows 8.1) yükleyin**

1. MSU dosyasının yüklediğiniz klasöre gidin.
2. Çalıştırmak için MSU çift tıklayın.

**Komut istemi kullanarak yükleme**

1. Bilgisayarınızın mimarisi için doğru paket indirdikten sonra yükseltilmiş kullanıcı haklarıyla (yönetici olarak çalıştır) bir komut istemi penceresi açın. Üzerinde Sunucu Çekirdeği yükleme seçenekleri, Windows Server 2012 R2, Windows Server 2012 veya Windows Server 2008 R2 SP1, varsayılan olarak yükseltilmiş kullanıcı haklarıyla bir komut istemi açar.
2. Dizinleri içine varsa indirilen veya WMF 5.1 yükleme paketini kopyaladığınız klasöre gidin.
3. Aşağıdaki komutlardan birini çalıştırın:
   - Windows Server 2012 R2 veya Windows 8.1 x64 çalıştıran bilgisayarlarda çalıştırmak `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Windows Server 2012 çalıştıran bilgisayarlarda çalıştırmak `W2K12-KB3191565-x64.msu /quiet`.
   - Windows 8.1 x86 çalıştıran bilgisayarlarda çalıştırmak `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> WMF 5.1 yüklemek için yeniden başlatma gerekir. Kullanarak `/quiet` seçeneği yeniden başlatma uyarısı olmadan sistem.
> Kullanım `/norestart` yeniden başlatılmasını önlemek için seçeneği. Ancak, yeniden kadar WMF 5.1 yüklenmez.