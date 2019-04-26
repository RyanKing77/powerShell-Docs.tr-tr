---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058675"
---
# <a name="improvements-in-powershell-script-debugging"></a>PowerShell Betik Hata Ayıklama İyileştirmeleri

Hata ayıklama deneyimini geliştirmek için PowerShell 5. 0'iyileştirmeler yapılmıştır:

## <a name="break-all"></a>Tümünü Kes

Artık PowerShell konsolunu ve Windows PowerShell ISE, komut dosyaları çalıştırmak için hata ayıklayıcıya girdikten olanak tanır. Bu, hem yerel hem de uzak oturumlarda çalışır.

Konsolda, basın **Ctrl + Break**.

ISE'de basın **Ctrl + B**, veya **hata ayıklama -> Tümünü Kes** menü komutu.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Uzaktan hata ayıklama ve Windows PowerShell ISE'de uzaktan dosya düzenleme

Windows PowerShell ISE'de artık, dosyaları açabilir ve uzak bir oturumda PSEdit komutuna çalıştırarak düzenleyebilirsiniz olanak tanır.
Örneğin, komut satırından aşağıdaki gibi uzak bir oturumda düzenlemek için bir dosya açabilirsiniz:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Ayrıca, artık düzenleyebilir ve değişiklikleri bir kesme noktasına ulaştığınızda, Windows PowerShell ISE'de otomatik olarak açılmış uzak bir dosyaya kaydedin.
Şimdi, uzak bir bilgisayarda çalışan bir komut dosyası hata ayıklama, ortaya çıkan hata düzeltildi ve değiştirilmiş betiği yeniden dosyasını düzenleyin.

## <a name="advanced-script-debugging"></a>Gelişmiş komut dosyası hata ayıklama

Windows PowerShell yüklü herhangi bir yerel bilgisayar işleme eklemesine ve rastgele çalışma alanları bu işlemde hata ayıklama izin veren yeni, Gelişmiş hata ayıklama özellikleri vardır.

### <a name="runspace-debugging"></a>Çalışma hata ayıklama

İşlemin geçerli çalışma alanlarını listelemek ve ISE hata ayıklayıcı ve Windows PowerShell Konsolu komut dosyası hata ayıklama için bu çalışma alanı ekleme izin veren yeni cmdlet'ler eklenmiştir:

-   Get-çalışma
-   Hata ayıklama çalışma
-   RunspaceDebug etkinleştir
-   RunspaceDebug devre dışı bırak
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>PowerShell barındırma işleme

Artık Windows PowerShell yüklü olan herhangi bir bilgisayar işleme iliştirilebilir. Bunun için etkileşimli bir oturum ile nasıl Enter-PSSession cmdlet'i çalıştırarak etkileşimli bir uzak oturuma girmek için benzer şekilde, işlem içine girerek:

-   PSHostProcess girin
-   Çıkış PSHostProcess
