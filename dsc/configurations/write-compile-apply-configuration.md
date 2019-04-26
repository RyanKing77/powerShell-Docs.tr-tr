---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, hizmet, Kurulum
title: Yapılandırma Yazma, Derleme ve Uygulama
ms.openlocfilehash: 947308efa165543571801c88a922daf44fa88be0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080025"
---
> <span data-ttu-id="74377-103">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="74377-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="74377-104">Yapılandırma Yazma, Derleme ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="74377-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="74377-105">Bu alıştırmada oluşturmak ve uygulamak başlangıçtan bitişe kadar bir Desired State Configuration ' nı (DSC) yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="74377-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="74377-106">Aşağıdaki örnekte, yazma ve çok basit bir yapılandırmayı uygulamak öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="74377-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="74377-107">Yapılandırma, yerel makinenizde "HelloWorld.txt" dosyasından sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="74377-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="74377-108">Dosyayı silerseniz, DSC, sonraki güncelleştirdiğinde yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74377-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="74377-109">DSC nedir ve nasıl çalıştığını genel bakış için bkz: [Desired State Configuration geliştiriciler için genel bakış](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="74377-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="74377-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74377-110">Requirements</span></span>

<span data-ttu-id="74377-111">Bu örneği çalıştırmak için PowerShell 4.0 veya sonraki sürümü çalıştıran bir bilgisayar gerekir.</span><span class="sxs-lookup"><span data-stu-id="74377-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="74377-112">Yapılandırmasını yazın</span><span class="sxs-lookup"><span data-stu-id="74377-112">Write the configuration</span></span>

<span data-ttu-id="74377-113">Bir DSC [yapılandırma](configurations.md) tanımlayan bir veya daha fazla hedef bilgisayarların (düğümlerin) yapılandırmak istediğiniz nasıl özel bir PowerShell işlevdir.</span><span class="sxs-lookup"><span data-stu-id="74377-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="74377-114">PowerShell ISE veya diğer PowerShell Düzenleyicisi, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="74377-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="74377-115">Dosyayı "HelloWorld.ps1" kaydedin.</span><span class="sxs-lookup"><span data-stu-id="74377-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="74377-116">Bir yapılandırma tanımlanması gibi bir işlevi tanımlayan olur.</span><span class="sxs-lookup"><span data-stu-id="74377-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="74377-117">**Düğüm** blok belirtir, bu durumda yapılandırılması için hedef düğümü `localhost`.</span><span class="sxs-lookup"><span data-stu-id="74377-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="74377-118">Yapılandırma çağıran bir [kaynakları](../resources/resources.md), `File` kaynak.</span><span class="sxs-lookup"><span data-stu-id="74377-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="74377-119">Kaynak hedef düğüm yapılandırması tarafından tanımlanmış durumda sağlayarak iş yapın.</span><span class="sxs-lookup"><span data-stu-id="74377-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="74377-120">Yapılandırma derleme</span><span class="sxs-lookup"><span data-stu-id="74377-120">Compile the configuration</span></span>

<span data-ttu-id="74377-121">DSC yapılandırması düğüme uygulanacak ilk MOF dosyasına derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="74377-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="74377-122">Bir işlev gibi bir yapılandırmayı çalıştırma derleme bir ".mof" dosyası tarafından tanımlanan her düğüm için `Node` blok.</span><span class="sxs-lookup"><span data-stu-id="74377-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="74377-123">Yapılandırma çalıştırmak için için gereken *nokta kaynak* "HelloWorld.ps1" betiğinizi geçerli kapsama.</span><span class="sxs-lookup"><span data-stu-id="74377-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="74377-124">Daha fazla bilgi için [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="74377-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="74377-125">*Nokta kaynak* depolandığı, sonra yolunda yazarak "HelloWorld.ps1" betiğinizi `. ` (nokta, alan).</span><span class="sxs-lookup"><span data-stu-id="74377-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="74377-126">Daha sonra olabilir gibi bir işlev çağırarak yapılandırmanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="74377-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="74377-127">Bu, aşağıdaki çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="74377-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="74377-128">Yapılandırmasını Uygula</span><span class="sxs-lookup"><span data-stu-id="74377-128">Apply the configuration</span></span>

<span data-ttu-id="74377-129">Derlenmiş MOF olduğuna göre yapılandırma (Bu durumda, yerel bilgisayar) hedef düğüm çağırarak uygulayabileceğiniz [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="74377-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="74377-130">`Start-DscConfiguration` Cmdlet'i söyler [yerel Configuration Manager'ı (LCM)](../managing-nodes/metaConfig.md), yapılandırmayı uygulamak için DSC, altyapı.</span><span class="sxs-lookup"><span data-stu-id="74377-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="74377-131">LCM yapılandırmayı uygulamak için DSC kaynakları çağırma çalışır.</span><span class="sxs-lookup"><span data-stu-id="74377-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="74377-132">Yürütmek için aşağıdaki kodu kullanın `Start-DSCConfiguration` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="74377-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="74377-133">İçin "localhost.mof" depolandığı dizin yolunu belirtin `-Path` parametresi.</span><span class="sxs-lookup"><span data-stu-id="74377-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="74377-134">`Start-DSCConfiguration` Cmdlet'i görünüyor için belirtilen dizin aracılığıyla "\<computername\>.mof" dosyaları.</span><span class="sxs-lookup"><span data-stu-id="74377-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="74377-135">`Start-DSCConfiguration` Filename ("localhost", "server01", "dc-02", vb.) tarafından belirtilen computername bulduğu her ".mof" dosyasını uygulamak cmdlet'i çalışır.</span><span class="sxs-lookup"><span data-stu-id="74377-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="74377-136">Varsa `-Wait` parametresi belirtilmezse, `Start-DSCConfiguration` işlemi gerçekleştirmek için bir arka plan işi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74377-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="74377-137">Belirtme `-Verbose` parametresi, izlemek verir **ayrıntılı** işleminin çıktı.</span><span class="sxs-lookup"><span data-stu-id="74377-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="74377-138">`-Wait`, ve `-Verbose` hem isteğe bağlı parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="74377-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="74377-139">Test yapılandırması</span><span class="sxs-lookup"><span data-stu-id="74377-139">Test the configuration</span></span>

<span data-ttu-id="74377-140">Bir kez `Start-DSCConfiguration` cmdlet tamamlandıktan sonra belirtilen konumda bir "HelloWorld.txt" dosyası görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="74377-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="74377-141">İçeriğiyle doğrulayabilirsiniz [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="74377-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="74377-142">Ayrıca *test* geçerli durumunu kullanma [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="74377-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="74377-143">Düğümü şu anda uygulanan yapılandırma ile uyumlu ise çıktısı "True" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74377-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="74377-144">Yapılandırmayı yeniden uygulanıyor</span><span class="sxs-lookup"><span data-stu-id="74377-144">Re-applying the configuration</span></span>

<span data-ttu-id="74377-145">Yeniden uygulandığından yapılandırmanızı görmeyi, yapılandırma tarafından oluşturulan metin dosyasını kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74377-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="74377-146">Kullanımı `Start-DSCConfiguration` cmdlet'iyle `-UseExisting` parametresi.</span><span class="sxs-lookup"><span data-stu-id="74377-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="74377-147">`-UseExisting` Parametresi `Start-DSCConfiguration` "current.mof" dosya yeniden Uygula için en son başarılı bir şekilde temsil eden yapılandırma uygulandı.</span><span class="sxs-lookup"><span data-stu-id="74377-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="74377-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="74377-148">Next steps</span></span>

- <span data-ttu-id="74377-149">DSC yapılandırmalar hakkında daha fazla bilgi edinin [DSC yapılandırmaları](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="74377-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="74377-150">Hangi DSC kaynakların kullanılabilir olduğundan ve özel DSC kaynakları oluşturmak nasıl [DSC kaynakları](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="74377-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="74377-151">DSC yapılandırmaları ve kaynakları Bul [PowerShell Galerisi](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="74377-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
