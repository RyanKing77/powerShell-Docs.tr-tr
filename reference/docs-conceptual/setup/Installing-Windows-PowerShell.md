---
ms.date: 08/09/2017
keywords: PowerShell cmdlet'i, indirme, yükleme, Kurulum, windows 10, windows 8.1, windows 8.0, windows 7
title: Windows PowerShell Yükleme
ms.openlocfilehash: e703d3444b1d661c482b314781cf9a1cb16ef7ed
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893530"
---
# <a name="installing-windows-powershell"></a>Windows PowerShell Yükleme

Windows PowerShell varsayılan olarak Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayarak, her Windows yüklenmiş olarak sunulur.

PowerShell 6 ve üzeri ilgileniyorsanız, PowerShell Core yerine Windows PowerShell yüklemeniz gerekir. Bunun için bkz. [üzerinde Windows PowerShell Core yükleme](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>PowerShell, Windows 10 ve 8.1, 8.0 ve 7 bulma

Konumu bir Windows sürümünden diğerine taşınırken bazen PowerShell bulma konsolu veya Windows (tümleşik komut dosyası ortamı) ISE'de zor olabilir.

Aşağıdaki tablolarda, PowerShell, Windows sürümünde bulmanıza yardımcı olmalıdır.
Burada listelenen tüm özgün sürümle, hiçbir güncelleştirme ile serbest bırakıldı sürümleridir.

### <a name="for-console"></a>Konsolu için

Sürüm | Konum
-- | --
Windows 10 | Sol alt köşedeki Windows simgesine tıklayın, PowerShell yazmaya başlayın
Windows 8.1, 8.0 | Başlangıç ekranında, PowerShell yazmaya başlayın.<br/>Masaüstünde varsa, sol alt köşedeki Windows simgesine tıklayın, PowerShell yazmaya başlayın
Windows 7 SP1 | Sol alt köşedeki Windows simgesine, PowerShell yazarak arama kutusunun başlangıç tıklayın

### <a name="for-ise"></a>ISE için

Sürüm | Konum
-- | --
Windows 10 | Sol alt köşedeki Windows simgesine tıklayın, işe yazmaya başlayın
Windows 8.1, 8.0 | Başlangıç ekranında **PowerShell ISE**.<br/>Masaüstünde, alt köşe Windows simgesine tıklayın bırakılırsa yazın **PowerShell ISE**
Windows 7 SP1 | Sol alt köşedeki Windows simgesine, PowerShell yazarak arama kutusunun başlangıç tıklayın

## <a name="finding-powershell-in-windows-server-versions"></a>PowerShell, Windows Server sürümlerinde bulma

Windows Server 2008 R2 ile başlayarak, Windows işletim sistemi grafik kullanıcı arabirimi (GUI) yüklenebilir.
GUI içermeyen Windows Server sürümlerini adlı **çekirdek** ve GUI içeren sunucu sürümleri adlı **Masaüstü**.

### <a name="windows-server-core-editions"></a>Windows Server Core sürümleri

Sunucuda oturum açtığında tüm çekirdeği sürümlerinde, bir Windows komut istemi penceresi alırsınız.

Tür `powershell` basın **ENTER** PowerShell içinde komut istemi oturumu başlatmak için.
Tür `exit` PowerShell oturumu sona erdirmek ve komut istemine dönün.

### <a name="windows-server-desktop-editions"></a>Windows Server Masaüstü sürümleri

Tüm masaüstü sürümlerinde, sol alt köşedeki Windows simgesine tıklayın, PowerShell yazmaya başlayın.
Hem konsol hem de ISE seçenekler olursunuz.

Windows Server 2008 R2 SP1 ISE'de yukarıdaki kuralın tek özel durumu olan; Bu durumda, sol alt köşedeki Windows simgesine tıklayın, PowerShell ISE yazın.

## <a name="how-to-check-the-version-of-powershell"></a>PowerShell sürümünü denetleme

Hangi PowerShell sürümünü yüklediğiniz bulmak için bir PowerShell Konsolu (veya ISE) başlatın ve türü `$PSVersionTable` basın **ENTER**. Aranacak `PSVersion` değeri.

## <a name="upgrading-existing-windows-powershell"></a>Mevcut Windows PowerShell yükseltme

PowerShell yükleme paketi bir WMF yükleyici gelir.
WMF yükleyicisinin sürümünü PowerShell sürümüyle eşleşmiyor; Windows PowerShell için tek başına yükleyici yok yoktur.

Mevcut PowerShell sürümünüz güncelleştirmeniz gerekiyorsa Windows, yükleyici için güncelleştirmek istediğiniz PowerShell sürümü bulmak için aşağıdaki tabloyu kullanın.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (Note1 bakın)<br/>Windows Server 2016 | - | - | - | yüklü
Windows 8.1<br/>Windows Server 2012 R2 | - | yüklü | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | yüklü | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> Etkin, otomatik güncelleştirmeleri ile Windows 10'in ilk sürümünden üzerindeki PowerShell 5.0 için 5.1 sürümünden güncelleştirilir.
>
> Orijinal Windows 10 sürümünü aracılığıyla Windows güncelleştirmelerini güncelleştirilmezse, PowerShell 5.0 sürümüdür.

## <a name="need-azure-powershell"></a>Azure PowerShell olması gerekir

Aradığınız varsa **Azure PowerShell**, ile başlatabilir [genel bakış, Azure PowerShell](/powershell/azure/overview).

Aksi takdirde, gerek duyabileceğiniz olduğu [yüklemek ve Azure PowerShell yapılandırma](/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sistem gereksinimleri](Windows-PowerShell-System-Requirements.md)

[Windows PowerShell'i başlatma](Starting-Windows-PowerShell.md)