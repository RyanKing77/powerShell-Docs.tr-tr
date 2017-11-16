---
ms.date: 2017-08-09
keywords: "PowerShell cmdlet, indirme, yükleme, Kurulum, windows 10, windows 8.1, windows 8.0, windows 7"
title: "Windows PowerShell'i yükleme"
ms.openlocfilehash: 781bf50b6ac649e72bcdbb708555275fb7422d94
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2017
---
# <a name="installing-windows-powershell"></a>Windows PowerShell'i yükleme

PowerShell Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayarak, her Windows varsayılan olarak yüklenmiş olarak gelir.

Yüklemek istediğiniz Linux, macOS ve Windows kullanıcıları **PowerShell 6** (beta), kendi makinelerine içinde gerekir:

1. PowerShell belirli işletim sistemi ve sürümü için almanız [GitHub](https://github.com/powershell/powershell#get-powershell)
1. Yükleme yönergelerini izleyin
  - [Linux](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [macOS](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [Windows](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

Ayrıca, Docker için PowerShell 6 kullanılabilir; bkz: [Docker yükleme](https://github.com/PowerShell/PowerShell/tree/master/docker) yönergeler.

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>PowerShell Windows 10 ve 8.1, 8.0 ve 7 bulma

Cihazın konum bir Windows sürümünden diğerine taşır bazen PowerShell bulma konsolu veya Windows (tümleşik komut dosyası ortamı) işe zor olabilir.

Aşağıdaki tablolarda PowerShell, Windows sürümünde bulmanıza yardımcı olmalıdır.
Burada listelenen tüm özgün sürümü, hiçbir güncelleştirme ile serbest bırakıldı sürümleridir.

### <a name="for-console"></a>Konsolu için

Sürüm | Konum
-- | --
Windows 10 | Sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın
Windows 8.1, 8.0 | Başlangıç ekranında PowerShell yazmaya başlayın.<br/>Masaüstünde varsa, sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın
Windows 7 SP1 | Sol alt köşesindeki Windows, PowerShell yazarak arama kutusu başlangıç simgesine

### <a name="for-ise"></a>ISE için

Sürüm | Konum
-- | --
Windows 10 | Sol alt köşesindeki Windows simgesini tıklatın, işe yazmaya başlayın
Windows 8.1, 8.0 | Başlangıç ekranında **PowerShell ISE**.<br/>Masaüstünde, alt köşe Windows simgesini tıklatın bırakılırsa yazın **PowerShell ISE**
Windows 7 SP1 | Sol alt köşesindeki Windows, PowerShell yazarak arama kutusu başlangıç simgesine

## <a name="finding-powershell-in-windows-server-versions"></a>Windows Server sürümlerinde PowerShell bulma

Windows Server 2008 R2 ile başlayarak, Windows işletim sistemi grafik kullanıcı arabirimi (GUI) yüklenebilir.
GUI olmadan Windows Server sürümleri adlı **çekirdek** ve GUI içeren sürümleri adlı **Masaüstü**.

### <a name="windows-server-core-editions"></a>Windows Server Core sürümleri

Sunucuda oturum açtığınızda tüm çekirdeği sürümlerinde, bir Windows komut istemi penceresi olursunuz.

Tür `powershell` ve basın **ENTER** PowerShell içinde komut istemi oturumu başlatmak için. Tür `exit` PowerShell oturumu sona erdirmek ve komut istemine geri dönmek için.

### <a name="windows-server-desktop-editions"></a>Windows Server Masaüstü sürümleri

Tüm masaüstü sürümlerinde, sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın.
Hem konsol hem de işe seçenekleri alın.

Yukarıdaki kuralın tek özel durum, Windows Server 2008 R2 SP1 işe olan; Bu durumda, sol alt köşesindeki Windows simgesini tıklatın, PowerShell ISE yazın.

## <a name="how-to-check-the-version-of-powershell"></a>PowerShell sürümü denetleme

PowerShell hangi sürümünün yüklü olduğunu bulmak için bir PowerShell konsolunda (veya ISE) başlatın ve türü `$PSVersionTable` ve basın **ENTER**.

## <a name="upgrading-existing-windows-powershell"></a>Mevcut Windows PowerShell yükseltme

PowerShell yükleme paketi WMF yükleyici içinde gelir.
WMF yükleyici sürümü PowerShell sürümüyle eşleşen; Windows PowerShell için hiçbir tek başına yükleyici yoktur.

Windows, aşağıdaki tabloda varolan PowerShell sürümünüz güncellemeniz gerekiyorsa için güncelleştirmek istediğiniz PowerShell sürümü için yükleyiciyi bulmak için kullanın.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (Not1 bakın)<br/>Windows Server 2016 | - | - | - | yüklü
Windows 8.1<br/>Windows Server 2012 R2 | - | yüklü | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | yüklü | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **1 Not**:
  >>
  >> İlk sürümünden Windows 10, etkin, Otomatik Güncelleştirmeler PowerShell 5.0 için 5.1 sürümünden güncelleştirilmesi.
  >>
  >> Windows 10 özgün sürümü aracılığıyla Windows güncelleştirmeleri güncelleştirilmezse PowerShell 5.0 sürümüdür.

## <a name="need-azure-powershell"></a>Azure PowerShell gerekir

Arıyorsanız **Azure PowerShell**, ile başlayabilirsiniz [Azure PowerShell genel bakış](https://docs.microsoft.com/en-us/powershell/azure).

Aksi takdirde, gereksinim duyabileceğiniz değer [yükleyin ve Azure PowerShell yapılandırma](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell sistem gereksinimleri](Windows-PowerShell-System-Requirements.md)
- [Windows PowerShell'i başlatma](Starting-Windows-PowerShell.md)
