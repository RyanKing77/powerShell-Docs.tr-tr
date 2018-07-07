---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kullanarak bir sanal makineler ilk önyüklemede yapılandırma
ms.openlocfilehash: 2f228a38379d1e65b31c03594e876f7226474fc3
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893361"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="806cc-103">DSC kullanarak bir sanal makineler ilk önyüklemede yapılandırma</span><span class="sxs-lookup"><span data-stu-id="806cc-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="806cc-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="806cc-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="806cc-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="806cc-105">Requirements</span></span>

> [!NOTE] 
> <span data-ttu-id="806cc-106">**DSCAutomationHostEnabled** kayıt defteri anahtarı bu konuda açıklanan PowerShell 4. 0'kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="806cc-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="806cc-107">[Otomatik olarak yapılandırma bilgisayarınızı makineleri kullanarak DSC, ilk önyükleme yukarı istiyorsunuz?] yeni sanal makineler PowerShell 4.0 ilk önyükleme yukarı yapılandırma hakkında daha fazla bilgi için bkz. > ()https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="806cc-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="806cc-108">Bu örnekleri çalıştırmak için ihtiyacınız olacak:</span><span class="sxs-lookup"><span data-stu-id="806cc-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="806cc-109">Çalışmak için önyüklenebilir bir VHD.</span><span class="sxs-lookup"><span data-stu-id="806cc-109">A bootable VHD to work with.</span></span> <span data-ttu-id="806cc-110">Bir Windows Server 2016'da kopyasının bir ISO indirebileceğiniz [TechNet değerlendirme Merkezi](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="806cc-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="806cc-111">Bir VHD ISO görüntüsünü oluşturma konusunda yönergeler bulabilirsiniz [önyükleme sanal sabit diskler oluşturarak](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="806cc-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="806cc-112">Hyper-V etkin olan bir konak bilgisayarı.</span><span class="sxs-lookup"><span data-stu-id="806cc-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="806cc-113">Bilgi için [Hyper-V'ye Genel Bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="806cc-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="806cc-114">DSC kullanarak bir bilgisayarda ilk önyükleme artırma için yazılım yükleme ve yapılandırma otomatik hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="806cc-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="806cc-115">Böylece ilk önyükleme işlemi sırasında çalıştırılan ya da bir yapılandırma MOF belgesi ya da bir metaconfiguration (VHD gibi) önyüklenebilir medya içine ekleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="806cc-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="806cc-116">Bu davranış tarafından belirtilen [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarı altında `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span><span class="sxs-lookup"><span data-stu-id="806cc-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span></span>
  <span data-ttu-id="806cc-117">Varsayılan olarak, bu anahtarın değeri, önyükleme sırasında çalıştırılacak DSC sağlayan 2 olan.</span><span class="sxs-lookup"><span data-stu-id="806cc-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="806cc-118">Önyükleme sırasında çalıştırılacak DSC istemiyorsanız ayarlayın [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarını 0.</span><span class="sxs-lookup"><span data-stu-id="806cc-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="806cc-119">Yapılandırma MOF belgesi bir VHD'ye ekleme</span><span class="sxs-lookup"><span data-stu-id="806cc-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="806cc-120">Bir VHD'ye DSC metaconfiguration ekleme</span><span class="sxs-lookup"><span data-stu-id="806cc-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="806cc-121">DSC önyükleme sırasında devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="806cc-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="806cc-122">Her ikisi de ekleyebilir `Pending.mof` ve `MetaConfig.mof` bilgisayara aynı anda.</span><span class="sxs-lookup"><span data-stu-id="806cc-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="806cc-123">Her iki dosya mevcut değilse, belirtilen ayarlar `MetaConfig.mof` önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="806cc-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="806cc-124">Yapılandırma MOF belgesi bir VHD'ye ekleme</span><span class="sxs-lookup"><span data-stu-id="806cc-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="806cc-125">İlk önyükleme yukarı bir yapılandırmasını uygulamak için derlenmiş yapılandırma MOF belgesi VHD'ye önyüklemeden ekleyebilir, `Pending.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="806cc-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="806cc-126">Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı 2 (varsayılan değer) olarak ayarlandığında, DSC yapılandırması tarafından tanımlanmış geçerli `Pending.mof` bilgisayar için ilk kez önyüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="806cc-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="806cc-127">Bu örnekte, biz IIS yeni bilgisayara yükleyecek aşağıdaki yapılandırmayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="806cc-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="806cc-128">Yapılandırma MOF belgesi üzerinde VHD ekleme</span><span class="sxs-lookup"><span data-stu-id="806cc-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="806cc-129">İstediğiniz yapılandırmanın çağırarak eklemesine VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="806cc-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="806cc-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="806cc-131">Bir bilgisayarda çalışan PowerShell 5.0 veya daha sonra yukarıdaki yapılandırma kaydetmek (**SampleIISInstall**) bir PowerShell Betiği (.ps1) dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="806cc-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="806cc-132">Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="806cc-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="806cc-133">MOF belgesi derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="806cc-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="806cc-134">Bu oluşturacak bir `localhost.mof` adlı yeni bir klasörde dosya `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="806cc-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="806cc-135">Yeniden adlandırmak ve bu dosyayı doğru konuma VHD taşıyın `Pending.mof` kullanarak [taşıma öğesi](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="806cc-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="806cc-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="806cc-137">Çağırarak VHD çıkarma [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="806cc-138">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="806cc-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="806cc-139">DSC MOF belgesi yüklediğiniz VHD kullanarak bir VM oluşturun.</span><span class="sxs-lookup"><span data-stu-id="806cc-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="806cc-140">İlk önyükleme yukarı ve işletim sistemi yüklemesi sonra IIS yüklenir.</span><span class="sxs-lookup"><span data-stu-id="806cc-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="806cc-141">Bunu çağırarak doğrulamak [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="806cc-142">Bir VHD'ye DSC metaconfiguration ekleme</span><span class="sxs-lookup"><span data-stu-id="806cc-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="806cc-143">Ayrıca bir metaconfiguration ekleyerek ilk önyüklemede yapılandırma çekmek için bir bilgisayarı yapılandırabilirsiniz (bkz [yerel Configuration Manager (LCM) yapılandırma](metaConfig.md)) VHD'ye önyüklemeden kendi `MetaConfig.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="806cc-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="806cc-144">Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı, 2 (varsayılan değer) olarak ayarlandığında, DSC tarafından tanımlanan metaconfiguration geçerli `MetaConfig.mof` bilgisayar için ilk kez önyüklendiğinde LCM için.</span><span class="sxs-lookup"><span data-stu-id="806cc-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="806cc-145">Metaconfiguration LCM yapılandırmalar çekme sunucusundan çekmelidir belirtiyorsa, bilgisayar ilk önyüklemede bir yapılandırmasını söz konusu çekme sunucusundan çekme dener.</span><span class="sxs-lookup"><span data-stu-id="806cc-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="806cc-146">DSC çekme sunucusu ayarlama hakkında daha fazla bilgi için bkz: [bir DSC web çekme sunucusu ayarlama](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="806cc-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="806cc-147">Bu örnekte, önceki bölümde açıklanan yapılandırma, her iki kullanacağız (**SampleIISInstall**) ve aşağıdaki metaconfiguration:</span><span class="sxs-lookup"><span data-stu-id="806cc-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="806cc-148">VHD metaconfiguration MOF belgede ekleme</span><span class="sxs-lookup"><span data-stu-id="806cc-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="806cc-149">Çağırarak metaconfiguration eklemek istediğiniz VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="806cc-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="806cc-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="806cc-151">[Bir DSC web çekme sunucusu ayarlama](pullServer.md), kaydedip **SampleIISInistall** uygun klasöre yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="806cc-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="806cc-152">Bir bilgisayarda çalışan PowerShell 5.0 veya daha sonra yukarıdaki metaconfiguration kaydetmek (**PullClientBootstrap**) bir PowerShell Betiği (.ps1) dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="806cc-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="806cc-153">Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="806cc-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="806cc-154">Metaconfiguration MOF belgesi derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="806cc-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="806cc-155">Bu oluşturacak bir `localhost.meta.mof` adlı yeni bir klasörde dosya `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="806cc-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="806cc-156">Yeniden adlandırmak ve bu dosyayı doğru konuma VHD taşıyın `MetaConfig.mof` kullanarak [taşıma öğesi](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="806cc-157">Çağırarak VHD çıkarma [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="806cc-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="806cc-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="806cc-159">DSC MOF belgesi yüklediğiniz VHD kullanarak bir VM oluşturun.</span><span class="sxs-lookup"><span data-stu-id="806cc-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="806cc-160">İlk önyükleme yukarı ve işletim sistemi yüklemesi sonra DSC çekme sunucusundan yapılandırma çeker ve IIS yüklenir.</span><span class="sxs-lookup"><span data-stu-id="806cc-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="806cc-161">Bunu çağırarak doğrulamak [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="806cc-162">DSC önyükleme sırasında devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="806cc-162">Disable DSC at boot time</span></span>

<span data-ttu-id="806cc-163">Varsayılan olarak, değerini `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` anahtar ayarlanmış 2'ye bir DSC yapılandırması veren bilgisayar ise çalıştırmak için bekleyen veya geçerli durumunda.</span><span class="sxs-lookup"><span data-stu-id="806cc-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="806cc-164">İlk önyüklemede çalıştırmak için bir yapılandırma istemiyorsanız, bu anahtarın değeri 0'olacak şekilde ayarlamanız:</span><span class="sxs-lookup"><span data-stu-id="806cc-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="806cc-165">Çağırarak VHD'nin [VHD'yi Bağla](/powershell/module/hyper-v/mount-vhd) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="806cc-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="806cc-166">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="806cc-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="806cc-167">Kayıt defteri `HKLM\Software` çağırarak VHD'den alt anahtar `reg load`.</span><span class="sxs-lookup"><span data-stu-id="806cc-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="806cc-168">Gidin `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` PowerShell kayıt defteri sağlayıcıyı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="806cc-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. <span data-ttu-id="806cc-169">Değiştirin `DSCAutomationHostEnabled` 0.</span><span class="sxs-lookup"><span data-stu-id="806cc-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="806cc-170">Aşağıdaki komutları çalıştırarak kayıt kaldırma:</span><span class="sxs-lookup"><span data-stu-id="806cc-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="806cc-171">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="806cc-171">See Also</span></span>

[<span data-ttu-id="806cc-172">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="806cc-172">DSC Configurations</span></span>](configurations.md)

[<span data-ttu-id="806cc-173">DSCAutomationHostEnabled kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="806cc-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="806cc-174">Local Configuration Manager’ı (LCM) Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="806cc-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)

[<span data-ttu-id="806cc-175">Bir DSC web çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="806cc-175">Setting up a DSC web pull server</span></span>](pullServer.md)
