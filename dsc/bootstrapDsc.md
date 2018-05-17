---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kullanarak ilk önyükleme yukarı bir sanal makineleri yapılandırma
ms.openlocfilehash: d6dd997e607152d09d24b55370bb2f85810b333e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
>İçin geçerlidir: Windows PowerShell 5.0

>**Not:** **DSCAutomationHostEnabled** kayıt defteri anahtarı bu konuda açıklanan PowerShell 4. 0 ' kullanılabilir değil.
İlk önyükleme li PowerShell 4. 0'ın en yeni sanal makineleri yapılandırma hakkında daha fazla bilgi için bkz: [otomatik olarak yapılandırmak bilgisayarınızı makineler kullanarak DSC ilk önyükleme li adresindeki istiyorsunuz?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>DSC kullanarak ilk önyükleme yukarı bir sanal makineleri yapılandırma

## <a name="requirements"></a>Gereksinimler

Bu örnekleri çalıştırmak için ihtiyacınız:

- Çalışmak üzere önyüklenebilir VHD. Windows Server 2016 değerlendirme kopyasının ile bir ISO indirebilirsiniz [TechNet değerlendirme Merkezi](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016). Bir ISO görüntüsüne bir VHD oluşturmak nasıl yönergelerini bulabilirsiniz [oluşturma önyüklenebilir sanal sabit diskler](https://technet.microsoft.com/library/gg318049.aspx).
- Hyper-V'nin etkin olduğu bir ana bilgisayar. Bilgi için bkz: [Hyper-V'ye Genel Bakış](https://technet.microsoft.com/library/hh831531.aspx).

DSC kullanarak, bir bilgisayarda ilk önyükleme yukarı için yazılım yükleme ve yapılandırma otomatikleştirebilirsiniz.
İlk önyükleme işlemi sırasında çalıştırılır, böylece her iki yapılandırma MOF belge veya bir meta yapılandırmasını önyüklenebilir medya (örneğin, bir VHD) içine ekleyerek bunu yapabilirsiniz.
Bu davranış tarafından belirtilen [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarında **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies**.
Varsayılan olarak, bu anahtarın değeri 2, önyükleme zamanında DSC sağlayan'dir.

DSC önyükleme zamanında istemiyorsanız değerini ayarlamak [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarını 0.

- Bir yapılandırma MOF belgesi bir VHD'ye Ekle
- Bir VHD'ye DSC meta yapılandırmasını Ekle
- DSC önyükleme sırasında devre dışı bırak

>**Not:** her ikisi de Ekle `Pending.mof` ve `MetaConfig.mof` bir bilgisayarda aynı anda.
Her iki dosya varsa, belirtilen ayarlar `MetaConfig.mof` önceliklidir.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Bir yapılandırma MOF belgesi bir VHD'ye Ekle

İlk önyükleme yukarı konumundaki yapılandırma yürürlüğe için derlenmiş yapılandırma MOF belgesi VHD içine ekleyemezsiniz kendi `Pending.mof` dosya.
Varsa **DSCAutomationHostEnabled** 2 (varsayılan değer) kayıt defteri anahtarını ayarlayın, DSC yapılandırması tarafından tanımlanan geçerli `Pending.mof` bilgisayar ilk kez kaydınızı önyüklendiğinde.

Bu örnekte, IIS yeni bilgisayarınıza yükleyecek aşağıdaki yapılandırma kullanacağız:

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>VHD yapılandırma MOF belgede ekleme

1. Yapılandırma çağırarak eklemesine istediğiniz VHD'nin [bağlama VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet'i. Örneğin:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. Çalıştıran bir bilgisayarda PowerShell 5.0 veya daha sonra yukarıdaki yapılandırmayı kaydedin (**SampleIISInstall**) bir PowerShell Betiği (.ps1) dosyası olarak.

3. Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.

4. MOF belge derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md):

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. Bu oluşturacak bir `localhost.mof` adlı yeni bir klasör dosyasında `SampleIISInstall`.
Yeniden adlandırın ve bu dosyayı doğru konuma VHD taşıyın `Pending.mof` kullanarak [taşıma öğesi](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet'i. Örneğin:

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. VHD çağırarak çıkarılması [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet'i. Örneğin:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. DSC MOF belge yüklendiği VHD kullanarak bir VM oluşturun.
İlk önyükleme yukarı ve işletim sisteminin yüklenmesinden sonra IIS yüklenir.
Bunu çağırarak doğrulamak [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet'i.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Bir VHD'ye DSC meta yapılandırmasını Ekle

Bir meta yapılandırmasını ekleyerek bir yapılandırma ilk önyükleme yukarı çıkarmak için bir bilgisayarı da yapılandırabilirsiniz (bkz [yerel Configuration Manager (LCM'yi) yapılandırma](metaConfig.md)) VHD içine kendi `MetaConfig.mof` dosya.
Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı, 2 (varsayılan değer) olarak ayarlandığında, DSC meta yapılandırmasını tarafından tanımlanan geçerli `MetaConfig.mof` bilgisayar için ilk kez önyükleme yaptığında LCM'yi için.
Meta yapılandırmasını LCM'yi yapılandırmaları bir çekme sunucudan çekme belirtiyorsa, bilgisayar yapılandırmasını o çekme sunucusundan ilk önyükleme yukarı çekme dener.
DSC çekme sunucusu kurma hakkında daha fazla bilgi için bkz: [DSC web çekme sunucusu kurma](pullServer.md).

Bu örnekte, önceki bölümde açıklanan her iki yapılandırma kullanacağız (**SampleIISInstall**) ve aşağıdaki meta yapılandırmasını:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>VHD meta yapılandırmasını MOF belgede ekleme

1. Çağırarak meta yapılandırmasını eklemesine istediğiniz VHD'nin [bağlama VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet'i. Örneğin:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. [DSC web çekme sunucusu kurmak](pullServer.md), kaydedip **SampleIISInistall** uygun klasöre yapılandırma.

3. Çalıştıran bir bilgisayarda PowerShell 5.0 veya daha sonra yukarıdaki meta yapılandırmasını kaydedin (**PullClientBootstrap**) bir PowerShell Betiği (.ps1) dosyası olarak.

4. Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.

5. Meta yapılandırmasını MOF belge derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md):

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. Bu oluşturacak bir `localhost.meta.mof` adlı yeni bir klasör dosyasında `PullClientBootstrap`.
Yeniden adlandırın ve bu dosyayı doğru konuma VHD taşıyın `MetaConfig.mof` kullanarak [taşıma öğesi](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet'i.

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. VHD çağırarak çıkarılması [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet'i. Örneğin:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. DSC MOF belge yüklendiği VHD kullanarak bir VM oluşturun.
İlk önyükleme yukarı ve işletim sistemi yüklemesi sonra DSC çekme sunucusuna yapılandırmasından çeker ve IIS yüklenir.
Bunu çağırarak doğrulamak [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet'i.

## <a name="disable-dsc-at-boot-time"></a>DSC önyükleme sırasında devre dışı bırak

Varsayılan olarak, değeri **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** anahtar ayarlanmış 2'ye bir DSC yapılandırma sağlayan bilgisayar bekleyen veya geçerli ise çalıştırmak için durumu. İlk önyükleme li çalıştırmak için bir yapılandırma istemiyorsanız, bu anahtarın değeri 0 olarak olacak şekilde ayarlamanız:

1. Çağırarak VHD'nin [bağlama VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet'i. Örneğin:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. Kayıt defteri **HKLM\Software** çağırarak VHD'den alt anahtar `reg load`.

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. Gidin **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\***  PowerShell kayıt defteri sağlayıcısını kullanarak.

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. Değerini değiştirme `DSCAutomationHostEnabled` 0.

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. Kayıt defteri aşağıdaki komutları çalıştırarak kaldırın:

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırmaları](configurations.md)
- [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md)
- [Local Configuration Manager’ı (LCM) Yapılandırma](metaConfig.md)
- [DSC çekme sunucusuna ayarlama](pullServer.md)