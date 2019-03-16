---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kullanarak bir sanal makineler ilk önyüklemede yapılandırma
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059431"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="3548e-103">DSC kullanarak bir sanal makineler ilk önyüklemede yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3548e-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3548e-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3548e-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="3548e-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3548e-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="3548e-106">**DSCAutomationHostEnabled** kayıt defteri anahtarı bu konuda açıklanan PowerShell 4. 0'kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="3548e-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="3548e-107">Yeni sanal makineler PowerShell 4.0 ilk önyükleme yukarı yapılandırma hakkında daha fazla bilgi için bkz: [otomatik olarak yapılandırma bilgisayarınızı makineleri kullanarak DSC, ilk önyükleme yukarı istiyorsunuz?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="3548e-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="3548e-108">Bu örnekleri çalıştırmak için ihtiyacınız olacak:</span><span class="sxs-lookup"><span data-stu-id="3548e-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="3548e-109">Çalışmak için önyüklenebilir bir VHD.</span><span class="sxs-lookup"><span data-stu-id="3548e-109">A bootable VHD to work with.</span></span> <span data-ttu-id="3548e-110">Bir Windows Server 2016'da kopyasının bir ISO indirebileceğiniz [TechNet değerlendirme Merkezi](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="3548e-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="3548e-111">Bir VHD ISO görüntüsünü oluşturma konusunda yönergeler bulabilirsiniz [önyükleme sanal sabit diskler oluşturarak](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="3548e-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="3548e-112">Hyper-V etkin olan bir konak bilgisayarı.</span><span class="sxs-lookup"><span data-stu-id="3548e-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="3548e-113">Bilgi için [Hyper-V'ye Genel Bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="3548e-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="3548e-114">DSC kullanarak bir bilgisayarda ilk önyükleme artırma için yazılım yükleme ve yapılandırma otomatik hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3548e-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="3548e-115">Böylece ilk önyükleme işlemi sırasında çalıştırılan ya da bir yapılandırma MOF belgesi ya da bir metaconfiguration (VHD gibi) önyüklenebilir medya içine ekleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3548e-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="3548e-116">Bu davranış tarafından belirtilen [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarı altında `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="3548e-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="3548e-117">Varsayılan olarak, bu anahtarın değeri, önyükleme sırasında çalıştırılacak DSC sağlayan 2 olan.</span><span class="sxs-lookup"><span data-stu-id="3548e-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="3548e-118">Önyükleme sırasında çalıştırılacak DSC istemiyorsanız ayarlayın [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarını 0.</span><span class="sxs-lookup"><span data-stu-id="3548e-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="3548e-119">Yapılandırma MOF belgesi bir VHD'ye ekleme</span><span class="sxs-lookup"><span data-stu-id="3548e-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="3548e-120">Bir VHD'ye DSC metaconfiguration ekleme</span><span class="sxs-lookup"><span data-stu-id="3548e-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="3548e-121">DSC önyükleme sırasında devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="3548e-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="3548e-122">Her ikisi de ekleyebilir `Pending.mof` ve `MetaConfig.mof` bilgisayara aynı anda.</span><span class="sxs-lookup"><span data-stu-id="3548e-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="3548e-123">Her iki dosya mevcut değilse, belirtilen ayarlar `MetaConfig.mof` önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="3548e-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="3548e-124">Yapılandırma MOF belgesi bir VHD'ye ekleme</span><span class="sxs-lookup"><span data-stu-id="3548e-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="3548e-125">İlk önyükleme yukarı bir yapılandırmasını uygulamak için derlenmiş yapılandırma MOF belgesi VHD'ye önyüklemeden ekleyebilir, `Pending.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="3548e-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="3548e-126">Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı 2 (varsayılan değer) olarak ayarlandığında, DSC yapılandırması tarafından tanımlanmış geçerli `Pending.mof` bilgisayar için ilk kez önyüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="3548e-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="3548e-127">Bu örnekte, biz IIS yeni bilgisayara yükleyecek aşağıdaki yapılandırmayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="3548e-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="3548e-128">Yapılandırma MOF belgesi üzerinde VHD ekleme</span><span class="sxs-lookup"><span data-stu-id="3548e-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="3548e-129">İstediğiniz yapılandırmanın çağırarak eklemesine VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="3548e-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3548e-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="3548e-131">Bir bilgisayarda çalışan PowerShell 5.0 veya daha sonra yukarıdaki yapılandırma kaydetmek (**SampleIISInstall**) bir PowerShell Betiği (.ps1) dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="3548e-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="3548e-132">Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="3548e-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="3548e-133">MOF belgesi derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="3548e-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="3548e-134">Bu oluşturacak bir `localhost.mof` adlı yeni bir klasörde dosya `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="3548e-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="3548e-135">Yeniden adlandırmak ve bu dosyayı doğru konuma VHD taşıyın `Pending.mof` kullanarak [taşıma öğesi](/powershell/module/microsoft.powershell.management/move-item) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="3548e-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3548e-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="3548e-137">Çağırarak VHD çıkarma [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="3548e-138">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3548e-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="3548e-139">DSC MOF belgesi yüklediğiniz VHD kullanarak bir VM oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3548e-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="3548e-140">İlk önyükleme yukarı ve işletim sistemi yüklemesinden sonra IIS yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3548e-140">After initial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="3548e-141">Bunu çağırarak doğrulamak [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="3548e-142">Bir VHD'ye DSC metaconfiguration ekleme</span><span class="sxs-lookup"><span data-stu-id="3548e-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="3548e-143">Ayrıca bir metaconfiguration ekleyerek ilk önyüklemede yapılandırma çekmek için bir bilgisayarı yapılandırabilirsiniz (bkz [yerel Configuration Manager (LCM) yapılandırma](../managing-nodes/metaConfig.md)) VHD'ye önyüklemeden kendi `MetaConfig.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="3548e-143">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="3548e-144">Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı, 2 (varsayılan değer) olarak ayarlandığında, DSC tarafından tanımlanan metaconfiguration geçerli `MetaConfig.mof` bilgisayar için ilk kez önyüklendiğinde LCM için.</span><span class="sxs-lookup"><span data-stu-id="3548e-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="3548e-145">Metaconfiguration LCM yapılandırmalar çekme sunucusundan çekmelidir belirtiyorsa, bilgisayar ilk önyüklemede bir yapılandırmasını söz konusu çekme sunucusundan çekme dener.</span><span class="sxs-lookup"><span data-stu-id="3548e-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span>
<span data-ttu-id="3548e-146">DSC çekme sunucusu ayarlama hakkında daha fazla bilgi için bkz: [bir DSC web çekme sunucusu ayarlama](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="3548e-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="3548e-147">Bu örnekte, önceki bölümde açıklanan yapılandırma, her iki kullanacağız (**SampleIISInstall**) ve aşağıdaki metaconfiguration:</span><span class="sxs-lookup"><span data-stu-id="3548e-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="3548e-148">VHD metaconfiguration MOF belgede ekleme</span><span class="sxs-lookup"><span data-stu-id="3548e-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="3548e-149">Çağırarak metaconfiguration eklemek istediğiniz VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="3548e-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3548e-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="3548e-151">[Bir DSC web çekme sunucusu ayarlama](../pull-server/pullServer.md), kaydedip **SampleIISInstall** uygun klasöre yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3548e-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="3548e-152">Bir bilgisayarda çalışan PowerShell 5.0 veya daha sonra yukarıdaki metaconfiguration kaydetmek (**PullClientBootstrap**) bir PowerShell Betiği (.ps1) dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="3548e-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="3548e-153">Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="3548e-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="3548e-154">Metaconfiguration MOF belgesi derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="3548e-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="3548e-155">Bu oluşturacak bir `localhost.meta.mof` adlı yeni bir klasörde dosya `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="3548e-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="3548e-156">Yeniden adlandırmak ve bu dosyayı doğru konuma VHD taşıyın `MetaConfig.mof` kullanarak [taşıma öğesi](/powershell/module/microsoft.powershell.management/move-item) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="3548e-157">Çağırarak VHD çıkarma [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="3548e-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3548e-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="3548e-159">DSC MOF belgesi yüklediğiniz VHD kullanarak bir VM oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3548e-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="3548e-160">İlk önyükleme yukarı ve işletim sistemi yüklemesi sonra DSC çekme sunucusundan yapılandırma çeker ve IIS yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3548e-160">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="3548e-161">Bunu çağırarak doğrulamak [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="3548e-162">DSC önyükleme sırasında devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="3548e-162">Disable DSC at boot time</span></span>

<span data-ttu-id="3548e-163">Varsayılan olarak, değerini `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` anahtar ayarlanmış 2'ye bir DSC yapılandırması veren bilgisayar ise çalıştırmak için bekleyen veya geçerli durumunda.</span><span class="sxs-lookup"><span data-stu-id="3548e-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="3548e-164">İlk önyüklemede çalıştırmak için bir yapılandırma istemiyorsanız, bu anahtarın değeri 0'olacak şekilde ayarlamanız:</span><span class="sxs-lookup"><span data-stu-id="3548e-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="3548e-165">Çağırarak VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3548e-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="3548e-166">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3548e-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="3548e-167">Kayıt defteri `HKLM\Software` çağırarak VHD'den alt anahtar `reg load`.</span><span class="sxs-lookup"><span data-stu-id="3548e-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="3548e-168">Gidin `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` PowerShell kayıt defteri sağlayıcıyı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3548e-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="3548e-169">Değiştirin `DSCAutomationHostEnabled` 0.</span><span class="sxs-lookup"><span data-stu-id="3548e-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="3548e-170">Aşağıdaki komutları çalıştırarak kayıt kaldırma:</span><span class="sxs-lookup"><span data-stu-id="3548e-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="3548e-171">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3548e-171">See Also</span></span>

[<span data-ttu-id="3548e-172">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="3548e-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="3548e-173">DSCAutomationHostEnabled kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="3548e-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="3548e-174">Local Configuration Manager’ı (LCM) Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3548e-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="3548e-175">Bir DSC web çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="3548e-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
