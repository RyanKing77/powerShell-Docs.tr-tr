---
title: Windows’da PowerShell Core yükleme
description: Üzerinde Windows PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058038"
---
# <a name="installing-powershell-core-on-windows"></a>Windows’da PowerShell Core yükleme

İçinde Windows PowerShell Core yüklemek için birden çok yolu vardır.

## <a name="prerequisites"></a>Önkoşullar

WSMan PowerShell uzaktan iletişimini etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:

- Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) önce Windows 10 Windows sürümleri üzerinde. Doğrudan indirme veya Windows Update kullanılabilir. Tam olarak düzeltme eki (isteğe bağlı paketleri dahil), desteklenen sistemleri zaten bu yüklü olacaktır.
- Windows Management Framework (WMF) 4.0 veya daha yeni Windows 7 ve Windows Server 2008 R2 yükleyin.

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />MSI paketini yükleme

Bir Windows istemci veya sunucuda Windows PowerShell'i yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve sonraki sürümler), GitHub [sürümleri] [] sayfamızı MSI paketini indirin. Ekranı aşağı kaydırarak **varlıklar** bölümü, yüklemek istediğiniz sürümü. Genişletmek için tıklaymanız gerekebilir. Bu nedenle, varlıklar bölüm daraltılmış.

MSI dosyası şu şekilde görünür- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

İndirildikten sonra yükleyiciye çift tıklayın ve yönergeleri izleyin.

Yükleyici Windows Başlat menüsünde bir kısayol oluşturur.

- Varsayılan olarak, paket için yüklenir `$env:ProgramFiles\PowerShell\<version>`
- Başlat menüsü aracılığıyla PowerShell başlatabilir veya `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a>Komut satırından yönetici yükleme

MSI paketleri, komut satırından yüklenebilir. Bu, kullanıcı etkileşimi olmadan paketlerini dağıtma olanağı sağlar. PowerShell için MSI paketi yükleme seçeneklerini denetlemek için aşağıdaki özellikleri içerir:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -bu özellik ekleme seçeneği denetler **açık PowerShell** Windows Gezgini bağlam menüsü öğesi.
- **ENABLE_PSREMOTING** -bu özellik, yükleme sırasında PowerShell uzaktan iletişimini etkinleştirme seçeneği denetler.
- **REGISTER_MANIFEST** -bu özellik, Windows olay günlüğü bildirimi kaydetme seçeneği denetler.

Aşağıdaki örneklerde, PowerShell Core etkin tüm yükleme seçenekleri ile sessizce yüklemek nasıl gösterir.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Msiexec.exe komut satırı seçeneklerinin tam listesi için bkz. [komut satırı seçenekleri](/windows/desktop/Msi/command-line-options).

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />ZIP paketini yükleme

Gelişmiş dağıtım senaryoları etkinleştirmek için PowerShell ikili ZIP arşivlerini sağlanır. ZIP arşivini kullanırken, önkoşul denetimi MSI paketini olduğu gibi vermeyecektir kaydedilmelidir. WSMan düzgün çalışması için üzerinden uzaktan iletişim için,, karşıladığınızdan emin olun [önkoşulları](#prerequisites).

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

## <a name="how-to-create-a-remoting-endpoint"></a>Uzaktan iletişim uç noktası oluşturma

PowerShell Core WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler. Daha fazla bilgi için bkz.:

- [SSH PowerShell core'da uzaktan iletişim] [ssh-uzaktan iletişim]
- [WSMan uzak PowerShell core'da] [wsman uzaktan iletişim]

<!-- [download-center]: TODO -->
[sürümleri]: https://github.com/PowerShell/PowerShell/releases [ssh-uzaktan iletişim]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman uzaktan iletişim]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
