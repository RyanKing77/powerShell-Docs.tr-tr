---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: aaf1809277f072c82e5a1a862ea64b75586e32d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-in-powershell-script-debugging"></a>PowerShell komut dosyası hata ayıklamasını yenilikleri

Bazı geliştirmeler, hata ayıklama deneyimini geliştirmek için PowerShell 5. 0 ' yapıldı:

## <a name="break-all"></a>Tüm bölün

PowerShell konsolunda ve Windows PowerShell ISE artık betikleri çalıştırmak için hata ayıklayıcısında araya girmektir olanak sağlar. Bu, hem yerel hem de uzak oturumlarda çalışır.

Konsolda basın **Ctrl + Break**.

ISE içinde basın **Ctrl + B**, veya kullanmak **hata ayıklama -> bölün tüm** menü komutu.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Uzaktan hata ayıklama ve Windows PowerShell ISE uzaktan dosya düzenleme

Windows PowerShell ISE şimdi açın ve PSEdit komutunu çalıştırarak uzak bir oturumda dosyaları düzenlemenize olanak sağlar.
Örneğin, komut satırından aşağıdaki gibi uzak bir oturumda düzenlemek için bir dosya açabilirsiniz:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Ayrıca, artık düzenleyebilir ve değişiklikleri bir kesme noktası isabet yükleyen Windows PowerShell ISE açıldığında otomatik olarak uzak bir dosyaya kaydedin.
Şimdi, uzak bir bilgisayarda çalışan bir komut dosyası hata ayıklama, hata düzeltme ve değiştirilen komut dosyası yeniden dosyasını düzenleyin.

## <a name="advanced-script-debugging"></a>Gelişmiş komut dosyası hata ayıklaması

Windows PowerShell yükledi herhangi bir yerel bilgisayarda işlem ekleyin ve bu işlem rasgele alanlarında hata ayıklama izin veren yeni, Gelişmiş hata ayıklama özellikleri vardır.

### <a name="runspace-debugging"></a>Çalışma hata ayıklama

İşlemin geçerli çalışma alanlarını listelemek ve komut dosyası hata ayıklama için bu çalışma alanı Windows PowerShell konsolu veya işe hata ayıklayıcı ekleme imkan sağlayan yeni cmdlet'ler eklenmiştir:

-   Get-çalışma
-   Hata ayıklama çalışma
-   Enable-RunspaceDebug
-   RunspaceDebug devre dışı bırak
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>PowerShell barındırma işlem ekleme

Windows PowerShell yüklü olan herhangi bir bilgisayarda işlem şimdi ekleyebilirsiniz. Etkileşimli oturum işlemine nasıl Enter-PSSession cmdlet'i çalıştırarak etkileşimli bir uzak oturuma girin benzer şekilde, içine girerek yapın:

-   Girin PSHostProcess
-   Çıkış PSHostProcess

