---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC kullanarak ilk önyükleme yukarı bir sanal makineleri yapılandırma"
ms.openlocfilehash: ff06aafa6db49d93a9b42e38ac7c3e9a11657bd5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
><span data-ttu-id="b0924-103">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b0924-103">Applies To: Windows PowerShell 5.0</span></span>

><span data-ttu-id="b0924-104">**Not:** **DSCAutomationHostEnabled** kayıt defteri anahtarı bu konuda açıklanan PowerShell 4. 0 ' kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="b0924-104">**Note:** The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
<span data-ttu-id="b0924-105">İlk önyükleme li PowerShell 4. 0'ın en yeni sanal makineleri yapılandırma hakkında daha fazla bilgi için bkz: [otomatik olarak yapılandırmak bilgisayarınızı makineler kullanarak DSC ilk önyükleme li adresindeki istiyorsunuz?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="b0924-105">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="b0924-106">DSC kullanarak ilk önyükleme yukarı bir sanal makineleri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0924-106">Configure a virtual machines at initial boot-up by using DSC</span></span>

## <a name="requirements"></a><span data-ttu-id="b0924-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0924-107">Requirements</span></span>

<span data-ttu-id="b0924-108">Bu örnekleri çalıştırmak için ihtiyacınız:</span><span class="sxs-lookup"><span data-stu-id="b0924-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="b0924-109">Çalışmak üzere önyüklenebilir VHD.</span><span class="sxs-lookup"><span data-stu-id="b0924-109">A bootable VHD to work with.</span></span> <span data-ttu-id="b0924-110">Windows Server 2016 değerlendirme kopyasının ile bir ISO indirebilirsiniz [TechNet değerlendirme Merkezi](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="b0924-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="b0924-111">Bir ISO görüntüsüne bir VHD oluşturmak nasıl yönergelerini bulabilirsiniz [oluşturma önyüklenebilir sanal sabit diskler](https://technet.microsoft.com/library/gg318049.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0924-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](https://technet.microsoft.com/library/gg318049.aspx).</span></span>
- <span data-ttu-id="b0924-112">Hyper-V'nin etkin olduğu bir ana bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="b0924-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="b0924-113">Bilgi için bkz: [Hyper-V'ye Genel Bakış](https://technet.microsoft.com/library/hh831531.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0924-113">For information, see [Hyper-V overview](https://technet.microsoft.com/library/hh831531.aspx).</span></span>

<span data-ttu-id="b0924-114">DSC kullanarak, bir bilgisayarda ilk önyükleme yukarı için yazılım yükleme ve yapılandırma otomatikleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0924-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
<span data-ttu-id="b0924-115">İlk önyükleme işlemi sırasında çalıştırılır, böylece her iki yapılandırma MOF belge veya bir meta yapılandırmasını önyüklenebilir medya (örneğin, bir VHD) içine ekleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0924-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
<span data-ttu-id="b0924-116">Bu davranış tarafından belirtilen [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarında **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies**.</span><span class="sxs-lookup"><span data-stu-id="b0924-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span></span>
<span data-ttu-id="b0924-117">Varsayılan olarak, bu anahtarın değeri 2, önyükleme zamanında DSC sağlayan'dir.</span><span class="sxs-lookup"><span data-stu-id="b0924-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

<span data-ttu-id="b0924-118">DSC önyükleme zamanında istemiyorsanız değerini ayarlamak [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md) kayıt defteri anahtarını 0.</span><span class="sxs-lookup"><span data-stu-id="b0924-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="b0924-119">Bir yapılandırma MOF belgesi bir VHD'ye Ekle</span><span class="sxs-lookup"><span data-stu-id="b0924-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="b0924-120">Bir VHD'ye DSC meta yapılandırmasını Ekle</span><span class="sxs-lookup"><span data-stu-id="b0924-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="b0924-121">DSC önyükleme sırasında devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="b0924-121">Disable DSC at boot time</span></span>

><span data-ttu-id="b0924-122">**Not:** her ikisi de Ekle `Pending.mof` ve `MetaConfig.mof` bir bilgisayarda aynı anda.</span><span class="sxs-lookup"><span data-stu-id="b0924-122">**Note:** You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
<span data-ttu-id="b0924-123">Her iki dosya varsa, belirtilen ayarlar `MetaConfig.mof` önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="b0924-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="b0924-124">Bir yapılandırma MOF belgesi bir VHD'ye Ekle</span><span class="sxs-lookup"><span data-stu-id="b0924-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="b0924-125">İlk önyükleme yukarı konumundaki yapılandırma yürürlüğe için derlenmiş yapılandırma MOF belgesi VHD içine ekleyemezsiniz kendi `Pending.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="b0924-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="b0924-126">Varsa **DSCAutomationHostEnabled** 2 (varsayılan değer) kayıt defteri anahtarını ayarlayın, DSC yapılandırması tarafından tanımlanan geçerli `Pending.mof` bilgisayar ilk kez kaydınızı önyüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="b0924-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="b0924-127">Bu örnekte, IIS yeni bilgisayarınıza yükleyecek aşağıdaki yapılandırma kullanacağız:</span><span class="sxs-lookup"><span data-stu-id="b0924-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="b0924-128">VHD yapılandırma MOF belgede ekleme</span><span class="sxs-lookup"><span data-stu-id="b0924-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="b0924-129">Yapılandırma çağırarak eklemesine istediğiniz VHD'nin [bağlama VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="b0924-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0924-130">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. <span data-ttu-id="b0924-131">Çalıştıran bir bilgisayarda PowerShell 5.0 veya daha sonra yukarıdaki yapılandırmayı kaydedin (**SampleIISInstall**) bir PowerShell Betiği (.ps1) dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="b0924-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="b0924-132">Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="b0924-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="b0924-133">MOF belge derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="b0924-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. <span data-ttu-id="b0924-134">Bu oluşturacak bir `localhost.mof` adlı yeni bir klasör dosyasında `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="b0924-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
<span data-ttu-id="b0924-135">Yeniden adlandırın ve bu dosyayı doğru konuma VHD taşıyın `Pending.mof` kullanarak [taşıma öğesi](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="b0924-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0924-136">For example:</span></span>

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. <span data-ttu-id="b0924-137">VHD çağırarak çıkarılması [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-137">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="b0924-138">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0924-138">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. <span data-ttu-id="b0924-139">DSC MOF belge yüklendiği VHD kullanarak bir VM oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0924-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span> <span data-ttu-id="b0924-140">İlk önyükleme yukarı ve işletim sisteminin yüklenmesinden sonra IIS yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b0924-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="b0924-141">Bunu çağırarak doğrulamak [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="b0924-142">Bir VHD'ye DSC meta yapılandırmasını Ekle</span><span class="sxs-lookup"><span data-stu-id="b0924-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="b0924-143">Bir meta yapılandırmasını ekleyerek bir yapılandırma ilk önyükleme yukarı çıkarmak için bir bilgisayarı da yapılandırabilirsiniz (bkz [yerel Configuration Manager (LCM'yi) yapılandırma](metaConfig.md)) VHD içine kendi `MetaConfig.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="b0924-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="b0924-144">Varsa **DSCAutomationHostEnabled** kayıt defteri anahtarı, 2 (varsayılan değer) olarak ayarlandığında, DSC meta yapılandırmasını tarafından tanımlanan geçerli `MetaConfig.mof` bilgisayar için ilk kez önyükleme yaptığında LCM'yi için.</span><span class="sxs-lookup"><span data-stu-id="b0924-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="b0924-145">Meta yapılandırmasını LCM'yi yapılandırmaları bir çekme sunucudan çekme belirtiyorsa, bilgisayar yapılandırmasını o çekme sunucusundan ilk önyükleme yukarı çekme dener.</span><span class="sxs-lookup"><span data-stu-id="b0924-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="b0924-146">DSC çekme sunucusu kurma hakkında daha fazla bilgi için bkz: [DSC web çekme sunucusu kurma](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="b0924-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="b0924-147">Bu örnekte, önceki bölümde açıklanan her iki yapılandırma kullanacağız (**SampleIISInstall**) ve aşağıdaki meta yapılandırmasını:</span><span class="sxs-lookup"><span data-stu-id="b0924-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="b0924-148">VHD meta yapılandırmasını MOF belgede ekleme</span><span class="sxs-lookup"><span data-stu-id="b0924-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="b0924-149">Çağırarak meta yapılandırmasını eklemesine istediğiniz VHD'nin [bağlama VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="b0924-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0924-150">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="b0924-151">[DSC web çekme sunucusu kurmak](pullServer.md), kaydedip **SampleIISInistall** uygun klasöre yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="b0924-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="b0924-152">Çalıştıran bir bilgisayarda PowerShell 5.0 veya daha sonra yukarıdaki meta yapılandırmasını kaydedin (**PullClientBootstrap**) bir PowerShell Betiği (.ps1) dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="b0924-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="b0924-153">Bir PowerShell konsolunda .ps1 dosyası olarak kaydettiğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="b0924-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="b0924-154">Meta yapılandırmasını MOF belge derlemek için aşağıdaki PowerShell komutlarını çalıştırın (DSC yapılandırmaları derleme hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="b0924-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. <span data-ttu-id="b0924-155">Bu oluşturacak bir `localhost.meta.mof` adlı yeni bir klasör dosyasında `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="b0924-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
<span data-ttu-id="b0924-156">Yeniden adlandırın ve bu dosyayı doğru konuma VHD taşıyın `MetaConfig.mof` kullanarak [taşıma öğesi](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. <span data-ttu-id="b0924-157">VHD çağırarak çıkarılması [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-157">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="b0924-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0924-158">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. <span data-ttu-id="b0924-159">DSC MOF belge yüklendiği VHD kullanarak bir VM oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0924-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>
<span data-ttu-id="b0924-160">İlk önyükleme yukarı ve işletim sistemi yüklemesi sonra DSC çekme sunucusuna yapılandırmasından çeker ve IIS yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b0924-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="b0924-161">Bunu çağırarak doğrulamak [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="b0924-162">DSC önyükleme sırasında devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="b0924-162">Disable DSC at boot time</span></span>

<span data-ttu-id="b0924-163">Varsayılan olarak, değeri **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** anahtar ayarlanmış 2'ye bir DSC yapılandırma sağlayan bilgisayar bekleyen veya geçerli ise çalıştırmak için durumu.</span><span class="sxs-lookup"><span data-stu-id="b0924-163">By default, the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="b0924-164">İlk önyükleme li çalıştırmak için bir yapılandırma istemiyorsanız, bu anahtarın değeri 0 olarak olacak şekilde ayarlamanız:</span><span class="sxs-lookup"><span data-stu-id="b0924-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="b0924-165">Çağırarak VHD'nin [bağlama VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b0924-165">Mount the VHD by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="b0924-166">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0924-166">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="b0924-167">Kayıt defteri **HKLM\Software** çağırarak VHD'den alt anahtar `reg load`.</span><span class="sxs-lookup"><span data-stu-id="b0924-167">Load the registry **HKLM\Software** subkey from the VHD by calling `reg load`.</span></span>

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. <span data-ttu-id="b0924-168">Gidin **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\***  PowerShell kayıt defteri sağlayıcısını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b0924-168">Navigate to the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*** by using the PowerShell Registry provider.</span></span>

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. <span data-ttu-id="b0924-169">Değerini değiştirme `DSCAutomationHostEnabled` 0.</span><span class="sxs-lookup"><span data-stu-id="b0924-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. <span data-ttu-id="b0924-170">Kayıt defteri aşağıdaki komutları çalıştırarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="b0924-170">Unload the registry by running the following commands:</span></span>

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a><span data-ttu-id="b0924-171">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b0924-171">See Also</span></span>

- [<span data-ttu-id="b0924-172">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="b0924-172">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="b0924-173">DSCAutomationHostEnabled kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="b0924-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)
- [<span data-ttu-id="b0924-174">Local Configuration Manager’ı (LCM) Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0924-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)
- [<span data-ttu-id="b0924-175">DSC çekme sunucusuna ayarlama</span><span class="sxs-lookup"><span data-stu-id="b0924-175">Setting up a DSC web pull server</span></span>](pullServer.md)

