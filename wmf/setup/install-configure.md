---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: WMF 5.1'i yükleme ve yapılandırma
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848141"
---
# <a name="install-and-configure-wmf-51"></a>WMF 5,1 'yi yükleyip yapılandırın

> [!IMPORTANT]
> WMF 5,0, WMF 5,1 tarafından değiştirildi. WMF 5,0 olan kullanıcıların destek alabilmesi için WMF 5,1 ' e yükseltilmesi gerekir.
> **WMF 5,1, .NET Framework 4.5.2 gerektirir** (veya üzeri). Yükleme başarılı olur, ancak .NET 4.5.2 (veya üzeri) yüklü değilse anahtar özellikler başarısız olur.

## <a name="download-and-install-the-wmf-51-package"></a>WMF 5,1 paketini indirme ve yükleme

Yüklemek istediğiniz işletim sistemi ve mimari için WMF 5,1 paketini indirin:

| İşletim Sistemi       | Önkoşullar           | Paket bağlantıları                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**Itanium** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**Itanium** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- WMF 5,1 RTM yüklenmeden önce WMF 5,1 önizlemesinin kaldırılması gerekir.
- WMF 5,1, WMF 5,0 veya WMF 4,0 üzerinden doğrudan yüklenebilir.
- Windows 7 ve Windows Server 2008 R2 üzerinde WMF 5,1 ' yi yüklemeden önce WMF 4,0 ' ü yüklemek **gerekli değildir** .

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Windows Server 2008 R2 ve Windows 7 için WMF 5,1 'yi yükler

> [!NOTE]
> Windows Server 2008 R2 ve Windows 7 için yükleme yönergeleri değiştirilmiştir ve diğer paketlere yönelik yönergelerden farklıdır. Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için yükleme yönergeleri aşağıda verilmiştir.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Windows Server 2008 R2 SP1 ve Windows 7 SP1 için WMF 5,1 önkoşulları

Windows Server 2008 R2 SP1 veya Windows 7 SP1 'de WMF 5,1 yüklemesi şunları gerektirir:

- En son hizmet paketi yüklü olmalıdır.
- WMF 3,0 **yüklü olmamalıdır.** WMF 5,1 3,0 üzerinden WMF yükleme, **PSModulePath** (`$env:PSModulePath`) kaybına neden olur ve bu da diğer uygulamaların başarısız olmasına neden olabilir. WMF 5,1 ' ü yüklemeden önce, WMF 3,0 ' yi kaldırmalı veya **PSModulePath** ' i KAYDETMENIZ ve WMF 5,1 yüklemesi tamamlandıktan sonra el ile geri yüklemeniz gerekir.
- WMF 5,1, en az [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)gerektirir.
  Yükleme konumundaki yönergeleri izleyerek Microsoft .NET Framework 4.5.2 yükleyebilirsiniz.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>Windows Server 2008 R2 ve Windows 7 ' de WMF 5,1 yükleme

1. ZIP dosyasını indirdiğiniz klasöre gidin.

2. ZIP dosyasına sağ tıklayın ve **Tümünü ayıkla...** seçeneğini belirleyin. ZIP dosyası iki dosya içerir: bir msu ve `Install-WMF5.1.ps1` betik dosyası. ZIP dosyasını paketledikten sonra, içeriği Windows 7 veya Windows Server 2008 R2 çalıştıran herhangi bir makineye kopyalayabilirsiniz.

3. ZIP dosya içeriğini ayıkladıktan sonra, PowerShell 'i yönetici olarak açın ve ZIP dosyasının içeriğini içeren klasöre gidin.

4. `Install-WMF5.1.ps1` Betiği bu klasörde çalıştırın ve yönergeleri izleyin. Bu betik, yerel makinedeki önkoşulları denetler ve önkoşullar karşılanıyorsa WMF 5,1 ' ü yükler. Önkoşullar aşağıda listelenmiştir.

   `Install-WMF5.1.ps1`Windows Server 2008 R2 ve Windows 7 ' de yüklemeyi otomatik hale getirmek için aşağıdaki parametreleri alır:

   - **ACCEPTEULA**: Bu parametre dahil edildiğinde, EULA otomatik olarak kabul edilir ve gösterilmez.
   - **Allowrestart**: Bu parametre, yalnızca AcceptEula belirtilmişse kullanılabilir. Bu parametre dahil ise ve WMF 5,1 yüklendikten sonra yeniden başlatma gerekliyse, yükleme tamamlandıktan hemen sonra istenmeden yeniden başlatma gerçekleşecektir.

## <a name="winrm-dependency"></a>WinRM bağımlılığı

Windows PowerShell Istenen durum yapılandırması (DSC), WinRM 'ye bağımlıdır. WinRM, Windows Server 2008 R2 ve Windows 7 ' de varsayılan olarak etkinleştirilmemiştir. WinRM `Set-WSManQuickConfig`'yi etkinleştirmek için Windows PowerShell yükseltilmiş oturumunda çalıştırın.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için WMF 5,1 'yi yükler

### <a name="install-from-windows-file-explorer"></a>Windows Dosya Gezgini 'nden yüklemesi

1. MSU dosyasını indirdiğiniz klasöre gidin.
2. Bunu çalıştırmak için MSU 'ya çift tıklayın.

### <a name="installing-from-the-command-prompt"></a>Komut Isteminden yükleme

1. Bilgisayarınızın mimarisi için doğru paketi indirdikten sonra, yükseltilmiş kullanıcı haklarıyla bir komut Istemi penceresi açın (yönetici olarak çalıştır). Windows Server 2012 R2, Windows Server 2012 veya Windows Server 2008 R2 SP1 'in Sunucu Çekirdeği yükleme seçeneklerinde, komut Istemi varsayılan olarak yükseltilmiş kullanıcı haklarıyla açılır.
2. Dizinleri, WMF 5,1 yükleme paketini indirdiğiniz veya kopyaladığınız klasöre değiştirin.
3. Aşağıdaki komutlardan birini çalıştırın:
   - Windows Server 2012 R2 veya Windows 8.1 x64 çalıştıran bilgisayarlarda çalıştırın `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Windows Server 2012 çalıştıran bilgisayarlarda çalıştırın `W2K12-KB3191565-x64.msu /quiet`.
   - Windows 8.1 x86 çalıştıran bilgisayarlarda çalıştırın `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> WMF 5,1 'nin yüklenmesi için yeniden başlatma gerekir. `/quiet` Seçeneğinin kullanılması, sistem uyarı vermeden yeniden başlatılır. Yeniden başlatmadan kaçınmak için seçeneğinikullanın.`/norestart` Ancak, WMF 5,1, yeniden başlatılana kadar yüklenmez.
