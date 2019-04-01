---
title: Windows’da PowerShell Core yükleme
description: Üzerinde Windows PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748950"
---
# <a name="installing-powershell-core-on-windows"></a>Windows’da PowerShell Core yükleme

## <a name="msi"></a>MSI

Bir Windows istemci veya sunucuda Windows PowerShell'i yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve daha sonra), bizim Github'dan MSI paketini indirme [Yayınları][] sayfası.  Ekranı aşağı kaydırarak **varlıklar** bölümü, yüklemek istediğiniz sürümü.  Genişletmek için tıklaymanız gerekebilir. Bu nedenle, varlıklar bölüm daraltılmış.

MSI dosyası şu şekilde görünür- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

İndirildikten sonra yükleyiciye çift tıklayın ve yönergeleri izleyin.

Bir kısayol Başlat menüsünde yükleme sonrasında yerleştirilen yoktur.

- Varsayılan olarak, paket için yüklenir `$env:ProgramFiles\PowerShell\<version>`
- Başlat menüsü aracılığıyla PowerShell başlatabilir veya `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Önkoşullar

WSMan PowerShell uzaktan iletişimini etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:

- Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) önce Windows 10 Windows sürümleri üzerinde.
  Doğrudan indirme veya Windows Update kullanılabilir.
  Tam olarak düzeltme eki (isteğe bağlı paketleri dahil), desteklenen sistemleri zaten bu yüklü olacaktır.
- Windows Management Framework (WMF) 4.0 veya daha yeni Windows 7 ve Windows Server 2008 R2 yükleyin.

## <a name="zip"></a>ZIP

Gelişmiş dağıtım senaryoları etkinleştirmek için PowerShell ikili ZIP arşivlerini sağlanır.
ZIP arşivini kullanırken, önkoşul denetimi MSI paketini olduğu gibi vermeyecektir kaydedilmelidir.
Windows 10 önceki Windows sürümlerinde düzgün çalışması için sırasıyla WSMan üzerinden uzaktan iletişim için emin olmamız gerekiyor. Bu nedenle [önkoşulları](#prerequisites) karşılanır.

## <a name="deploying-on-windows-iot"></a>Windows IOT dağıtma

Windows IOT zaten PowerShell Core 6'yı dağıtmak üzere kullanacağız Windows PowerShell ile birlikte gelir.

1. Oluşturma `PSSession` hedef cihaza

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. ZIP paketini cihaza Kopyala

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Cihaza bağlayın ve Arşiv genişletin

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. PowerShell Core 6 için'uzaktan iletişim kurma

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Cihazda PowerShell Core 6 uç noktasına bağlanma

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a>Nano Sunucu'yu dağıtma

Bu yönergeler, tarafından oluşturuldu ve Nano sunucu görüntüsünde PowerShell sürümü zaten çalışıyor varsayar [Nano sunucu görüntü Oluşturucusu](/windows-server/get-started/deploy-nano-server).
Nano sunucu "gözetimsiz" bir işletim sistemi ' dir. Çekirdek ikili dosyalarını olması dağıtabilir iki farklı yöntemle.

1. Çevrimdışı - Nano sunucu VHD'sini bağlayın ve bağlı görüntü içinde seçilen konumunuza ZIP dosyasının içeriğini sıkıştırmasını açın.
2. Çevrimiçi - zip dosyasını bir PowerShell oturumu üzerinden aktarım ve seçilen konumunuza sıkıştırmasını açın.

Her iki durumda da, Windows 10 x64 ZIP yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.

### <a name="offline-deployment-of-powershell-core"></a>PowerShell Core çevrimdışı dağıtımı

1. Bir dizine bağlı Nano sunucu görüntü içinde paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.
2. Yansımayı ve bunu önyükleme.
3. Windows PowerShell'in gelen örneğine bağlanın.
4. Uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>PowerShell Core çevrimiçi dağıtımı

Aşağıdaki adımlar PowerShell Core dağıtımı çalışan bir Nano sunucu ve kendi uzak uç nokta yapılandırması örneği için yol.

- Windows PowerShell gelen örneğine bağlanın

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Nano sunucu örneğine dosya kopyalayın

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Oturum girin

  ```powershell
  Enter-PSSession $session
  ```

- ZIP dosyasını ayıklayın

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- WSMan tabanlı uzak istiyorsanız, uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Bir uzak uç noktası oluşturmaya ilişkin yönergeler

PowerShell Core WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler.
Daha fazla bilgi için bkz.:

- [SSH PowerShell core'da uzaktan iletişim][ssh-remoting]
- [PowerShell core'da WSMan uzaktan iletişim][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Yapıt yükleme yönergeleri

Biz bir arşiv CoreCLR bitleri ile her bir CI yapısı ile yayımlama [AppVeyor][].

PowerShell Core CoreCLR yapıdan yüklemek için:

1. ZIP paketini indirin **yapıtları** belirli yapı sekmesi.
2. Engellemeyi kaldırma ZIP dosyası: dosya Gezgini'nde sağ -> Özellikler -> 'engellemeyi kaldırma kutusu ->' uygulama denetimi
3. Zip dosyasını ayıklayın `bin` dizini
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[Yayınları]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
