---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell Betik Hata Ayıklama İyileştirmeleri
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856178"
---
# <a name="improvements-in-powershell-script-debugging"></a>PowerShell Betik Hata Ayıklama İyileştirmeleri

PowerShell 5.0, hata ayıklama deneyimini geliştiren çeşitli iyileştirmeler içerir.

## <a name="break-all"></a>Tümünü Kes

PowerShell ISE ve PowerShell konsolunu artık komut dosyaları çalıştırmak için hata ayıklayıcıyı durdurmak için izin verin. Bu, hem yerel hem de uzak oturumlarda çalışır.

Konsolda, basın <kbd>Ctrl</kbd>+<kbd>sonu</kbd>.

ISE'de basın <kbd>Ctrl</kbd>+<kbd>B</kbd>, veya **hata ayıklama -> Tümünü Kes** menü komutu.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Uzaktan hata ayıklama ve PowerShell ISE'de uzaktan dosya düzenleme

PowerShell ISE'de artık, dosyaları açabilir ve uzak bir oturumda PSEdit komutuna çalıştırarak düzenleyebilirsiniz olanak tanır.
Örneğin, komut satırından aşağıdaki gibi uzak bir oturumda düzenlemek için bir dosya açabilirsiniz:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Ayrıca, artık düzenleyebilir ve değişiklikleri bir kesme noktasına ulaştığınızda, PowerShell ISE'de otomatik olarak açılmış uzak bir dosyaya kaydedin. Şimdi, uzak bir bilgisayarda çalışan bir komut dosyası hata ayıklama, ortaya çıkan hata düzeltildi ve değiştirilmiş betiği yeniden dosyasını düzenleyin.

## <a name="advanced-script-debugging"></a>Gelişmiş komut dosyası hata ayıklama

PowerShell yüklü herhangi bir yerel bilgisayar işleme eklemesine ve rastgele çalışma alanları bu işlemde hata ayıklama izin veren yeni, Gelişmiş hata ayıklama özellikleri vardır.

### <a name="runspace-debugging"></a>Çalışma hata ayıklama

İşlemin geçerli çalışma alanlarını listelemek ve betik hata ayıklama için bu çalışma PowerShell konsolu veya PowerShell ISE hata ayıklayıcı iliştirmek izin veren yeni cmdlet'ler eklenmiştir:

- Get-çalışma
- Hata ayıklama çalışma
- RunspaceDebug etkinleştir
- RunspaceDebug devre dışı bırak
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>PowerShell barındırma işleme

Artık PowerShell yüklü olan herhangi bir bilgisayar işleme iliştirebilirsiniz. Ana bilgisayar işlemi ile etkileşimli bir oturum içine girerek bunu yapabilirsiniz. Daha fazla bilgi için bkz.:

- [PSHostProcess girin](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Çıkış PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
