---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kullanarak bir sanal makineler ilk önyüklemede yapılandırma
ms.openlocfilehash: 7b9ebc6c818aa39365759945667426c8976997e5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405878"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>DSC kullanarak bir sanal makineler ilk önyüklemede yapılandırma

> [!IMPORTANT]
> Şunun için geçerlidir: Windows PowerShell 5.0

## <a name="requirements"></a>Gereksinimler

> [!NOTE]
> **DSCAutomationHostEnabled** kayıt defteri anahtarı bu konuda açıklanan PowerShell 4. 0'kullanılabilir değil.
> [Otomatik olarak yapılandırma bilgisayarınızı makineleri kullanarak DSC, ilk önyükleme yukarı istiyorsunuz?] yeni sanal makineler PowerShell 4.0 ilk önyükleme yukarı yapılandırma hakkında daha fazla bilgi için bkz. > ()https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Bu örnekleri çalıştırmak için ihtiyacınız olacak:

- Çalışmak için önyüklenebilir bir VHD. Bir Windows Server 2016'da kopyasının bir ISO indirebileceğiniz [TechNet değerlendirme Merkezi](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Bir VHD ISO görüntüsünü oluşturma konusunda yönergeler bulabilirsiniz [önyükleme sanal sabit diskler oluşturarak](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Hyper-V etkin olan bir konak bilgisayarı. Bilgi için [Hyper-V'ye Genel Bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  DSC kullanarak bir bilgisayarda ilk önyükleme artırma için yazılım yükleme ve yapılandırma otomatik hale getirebilirsiniz.
  Böylece ilk önyükleme işlemi sırasında çalıştırılan ya da bir yapılandırma MOF belgesi ya da bir metaconfiguration (VHD gibi) önyüklenebilir medya içine ekleyerek bunu yapabilirsiniz.
  Bu davranış tarafından belirtilen [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarı altında `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.
  Varsayılan olarak, bu anahtarın değeri, önyükleme sırasında çalıştırılacak DSC sağlayan 2 olan.

  Önyükleme sırasında çalıştırılacak DSC istemiyorsanız ayarlayın [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarını 0.

- Yapılandırma MOF belgesi bir VHD'ye ekleme
- Bir VHD'ye DSC metaconfiguration ekleme
- DSC önyükleme sırasında devre dışı bırak

> [!NOTE]
> Her ikisi de ekleyebilir `Pending.mof` ve `MetaConfig.mof` bilgisayara aynı anda.
> Her iki dosya mevcut değilse, belirtilen ayarlar `MetaConfig.mof` önceliklidir.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Yapılandırma MOF belgesi bir VHD'ye ekleme

İlk önyükleme yukarı bir yapılandırmasını uygulamak için derlenmiş yapılandırma MOF belgesi VHD'ye önyüklemeden ekleyebilir, `Pending.mof` dosya.
Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı 2 (varsayılan değer) olarak ayarlandığında, DSC yapılandırması tarafından tanımlanmış geçerli `Pending.mof` bilgisayar için ilk kez önyüklendiğinde.

Bu örnekte, biz IIS yeni bilgisayara yükleyecek aşağıdaki yapılandırmayı kullanın:

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Yapılandırma MOF belgesi üzerinde VHD ekleme

1. İstediğiniz yapılandırmanın çağırarak eklemesine VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i. Örneğin:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Bir bilgisayarda çalışan PowerShell 5.0 veya daha sonra yukarıdaki yapılandırma kaydetmek (**SampleIISInstall**) bir PowerShell Betiği (.ps1) dosyası olarak.

3. Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.

4. MOF belgesi derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](../configurations/configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Bu oluşturacak bir `localhost.mof` adlı yeni bir klasörde dosya `SampleIISInstall`.
   Yeniden adlandırmak ve bu dosyayı doğru konuma VHD taşıyın `Pending.mof` kullanarak [taşıma öğesi](/powershell/module/microsoft.powershell.management/move-item) cmdlet'i. Örneğin:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Çağırarak VHD çıkarma [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet'i. Örneğin:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. DSC MOF belgesi yüklediğiniz VHD kullanarak bir VM oluşturun.

İlk önyükleme yukarı ve işletim sistemi yüklemesi sonra IIS yüklenir.
Bunu çağırarak doğrulamak [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet'i.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Bir VHD'ye DSC metaconfiguration ekleme

Ayrıca bir metaconfiguration ekleyerek ilk önyüklemede yapılandırma çekmek için bir bilgisayarı yapılandırabilirsiniz (bkz [yerel Configuration Manager (LCM) yapılandırma](../managing-nodes/metaConfig.md)) VHD'ye önyüklemeden kendi `MetaConfig.mof` dosya.
Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı, 2 (varsayılan değer) olarak ayarlandığında, DSC tarafından tanımlanan metaconfiguration geçerli `MetaConfig.mof` bilgisayar için ilk kez önyüklendiğinde LCM için.
Metaconfiguration LCM yapılandırmalar çekme sunucusundan çekmelidir belirtiyorsa, bilgisayar ilk önyüklemede bir yapılandırmasını söz konusu çekme sunucusundan çekme dener.
DSC çekme sunucusu ayarlama hakkında daha fazla bilgi için bkz: [bir DSC web çekme sunucusu ayarlama](../pull-server/pullServer.md).

Bu örnekte, önceki bölümde açıklanan yapılandırma, her iki kullanacağız (**SampleIISInstall**) ve aşağıdaki metaconfiguration:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>VHD metaconfiguration MOF belgede ekleme

1. Çağırarak metaconfiguration eklemek istediğiniz VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i. Örneğin:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Bir DSC web çekme sunucusu ayarlama](../pull-server/pullServer.md), kaydedip **SampleIISInistall** uygun klasöre yapılandırma.

3. Bir bilgisayarda çalışan PowerShell 5.0 veya daha sonra yukarıdaki metaconfiguration kaydetmek (**PullClientBootstrap**) bir PowerShell Betiği (.ps1) dosyası olarak.

4. Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.

5. Metaconfiguration MOF belgesi derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](../configurations/configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Bu oluşturacak bir `localhost.meta.mof` adlı yeni bir klasörde dosya `PullClientBootstrap`.
   Yeniden adlandırmak ve bu dosyayı doğru konuma VHD taşıyın `MetaConfig.mof` kullanarak [taşıma öğesi](/powershell/module/microsoft.powershell.management/move-item) cmdlet'i.

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Çağırarak VHD çıkarma [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet'i. Örneğin:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. DSC MOF belgesi yüklediğiniz VHD kullanarak bir VM oluşturun.

İlk önyükleme yukarı ve işletim sistemi yüklemesi sonra DSC çekme sunucusundan yapılandırma çeker ve IIS yüklenir.
Bunu çağırarak doğrulamak [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet'i.

## <a name="disable-dsc-at-boot-time"></a>DSC önyükleme sırasında devre dışı bırak

Varsayılan olarak, değerini `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` anahtar ayarlanmış 2'ye bir DSC yapılandırması veren bilgisayar ise çalıştırmak için bekleyen veya geçerli durumunda. İlk önyüklemede çalıştırmak için bir yapılandırma istemiyorsanız, bu anahtarın değeri 0'olacak şekilde ayarlamanız:

1. Çağırarak VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i. Örneğin:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Kayıt defteri `HKLM\Software` çağırarak VHD'den alt anahtar `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Gidin `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` PowerShell kayıt defteri sağlayıcıyı kullanarak.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. Değiştirin `DSCAutomationHostEnabled` 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Aşağıdaki komutları çalıştırarak kayıt kaldırma:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Ayrıca bkz:

[DSC yapılandırmaları](../configurations/configurations.md)

[DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md)

[Local Configuration Manager’ı (LCM) Yapılandırma](../managing-nodes/metaConfig.md)

[Bir DSC web çekme sunucusu ayarlama](../pull-server/pullServer.md)
