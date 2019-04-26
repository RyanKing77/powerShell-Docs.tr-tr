---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Yükleme ve WMF 5.1 yapılandırma
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085006"
---
# <a name="install-and-configure-wmf-51"></a>Yükleme ve WMF 5.1 yapılandırma

## <a name="download-and-install-the-wmf-51-package"></a>WMF 5.1 paketini indirin ve yükleyin

WMF 5.1 paket yüklemek istediğiniz işletim sistemi ve mimarisi için indirme:

| İşletim Sistemi       | Önkoşullar           | Paket bağlantıları                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>WMF 5.1, Windows Server 2008 R2 ve Windows 7 için yükleyin

> [!NOTE]
> Yükleme yönergeleri için Windows Server 2008 R2 ve Windows 7, değiştirildi ve diğer paketleri yönergelerini farklıdır. Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için yükleme yönergeleri aşağıda verilmiştir.

**WMF 5.1, Windows Server 2008 R2 ve Windows 7 yükleme**

1. ZIP dosyası yüklediğiniz klasöre gidin.

2. ZIP dosyasını sağ tıklatın ve "Extract tüm..." seçeneğini belirleyin. Zip 2 dosyaları içerir: bir MSU ve yükleme WMF5.1.PS1 betik dosyası.
ZIP dosyası açılmış sonra Windows 7 veya Windows Server 2008 R2 çalıştıran herhangi bir makineye içeriğini kopyalayabilirsiniz.

3. ZIP dosyasının içeriğini ayıklayın sonra yönetici olarak PowerShell'i açın, ardından ZIP dosyasının içeriğini içeren klasöre gidin.

4. Bu klasörde Wmf5.1.ps1 yükleme komut dosyasını çalıştırın ve yönergeleri izleyin. Bu betik yerel makinede önkoşulları denetleyin ve önkoşullar karşılanmışsa WMF 5.1 yükleyin. Önkoşullar aşağıda listelenmiştir.

Yükleme WMF5.1.ps1 Windows 7 ve Windows Server 2008 R2 yüklemesini otomatikleştirme kolaylaştırmak için aşağıdaki parametreleri alır:

- AcceptEula: Bu parametreyi dahil edildiğinde EULA'yı otomatik olarak kabul edilir ve görüntülenmeyecek.
- AllowRestart: AcceptEula belirtilirse bu parametre yalnızca kullanılabilir. Bu parametre bulunur ve WMF 5.1 yükledikten sonra yeniden başlatma gerekiyor, yeniden başlatma hemen yükleme tamamlandıktan sonra sormadan gerçekleşir.

**WMF 5.1 Windows Server 2008 R2 SP1 ve Windows 7 SP1 için Önkoşullar**

WMF 5.1, Windows Server 2008 R2 SP1 veya Windows 7 SP1 yüklemesi aşağıdakileri gerektirir:
- En son hizmet paketi yüklü olmalıdır.
- WMF 3.0 **gerekir** yüklü olmalıdır. WMF 5.1 WMF 3.0 üzerinden yükleme, diğer uygulamaların başarısız olmasına neden olabilir PSModulePath kaybına neden olur. WMF 5.1 kurmadan önce PSModulePath kaydedin veya WMF 5.1 yükleme tamamlandıktan sonra el ile geri yüklemeyi ya da WMF 3.0 gerekir.
- WMF 5.1 en azından [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Microsoft .NET Framework 4.5.2'yi yükleme konumundan yönergeleri izleyerek yükleyebilirsiniz.

**WinRM bağımlılık**

WinRM üzerinde Windows PowerShell Desired State Configuration (DSC) bağlıdır.
WinRM üzerinde Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değil.
Çalıştırma `Set-WSManQuickConfig`, Windows PowerShell'de yükseltilmiş oturumu WinRM'yi etkinleştirin.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>WMF 5.1, Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için yükleyin

**Windows Explorer (veya Windows Server 2012 R2 veya Windows 8.1 ' de dosya Gezgini) yükleyin**

1. MSU dosyanın yüklediğiniz klasöre gidin.
2. MSU çalıştırmak için çift tıklayın.

**Komut İstemi'nden yükleme**

1. Bilgisayarınızın mimarisi için doğru paketi indirdikten sonra yükseltilmiş kullanıcı haklarıyla (yönetici olarak çalıştır) bir komut istemi penceresi açın. Üzerinde Sunucu Çekirdeği yükleme seçenekleri Windows Server 2012 R2, Windows Server 2012 veya Windows Server 2008 R2 SP1, yükseltilmiş kullanıcı haklarıyla bir komut istemi varsayılan olarak açılır.
2. Dizinleri içine indirdiğiniz ya da WMF 5.1 yükleme paketini kopyaladığınız klasöre gidin.
3. Aşağıdaki komutlardan birini çalıştırın:
   - Windows Server 2012 R2 veya Windows 8.1 x64 çalıştıran bilgisayarları üzerinde çalışması `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Windows Server 2012 çalıştıran bilgisayarları üzerinde çalışması `W2K12-KB3191565-x64.msu /quiet`.
   - X86 Windows 8.1 çalıştıran bilgisayarları üzerinde çalışması `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> WMF 5.1 yüklemek, yeniden başlatma gerekir. Kullanarak `/quiet` seçeneği sistem uyarı vermeden yeniden.
> Kullanım `/norestart` yeniden başlatılmasını önlemek için seçeneği. Ancak, yeniden kadar WMF 5.1 yüklenmez.
