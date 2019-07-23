---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, hizmet, kurulum
title: Yapılandırma Yazma, Derleme ve Uygulama
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372186"
---
> <span data-ttu-id="57969-103">Şunun için geçerlidir: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="57969-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="57969-104">Yapılandırma Yazma, Derleme ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="57969-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="57969-105">Bu alıştırma, başlangıçtan sonuna kadar Istenen durum yapılandırması (DSC) yapılandırması oluşturma ve uygulamayı adım adım göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="57969-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="57969-106">Aşağıdaki örnekte, çok basit bir yapılandırmanın nasıl yazılacağını ve uygulanacağını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="57969-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="57969-107">Yapılandırma, yerel makinenizde bir "HelloWorld. txt" dosyasının var olduğundan emin olur.</span><span class="sxs-lookup"><span data-stu-id="57969-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="57969-108">Dosyayı silerseniz, DSC bir sonraki güncelleştirilişinde onu yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57969-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="57969-109">DSC 'nin ne olduğu ve nasıl çalıştığı hakkında genel bir bakış için, bkz. [geliştiriciler Için Istenen durum yapılandırmasına genel bakış](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="57969-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="57969-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57969-110">Requirements</span></span>

<span data-ttu-id="57969-111">Bu örneği çalıştırmak için PowerShell 4,0 veya sonraki bir sürümünü çalıştıran bir bilgisayara ihtiyacınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="57969-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="57969-112">Yapılandırmayı yazma</span><span class="sxs-lookup"><span data-stu-id="57969-112">Write the configuration</span></span>

<span data-ttu-id="57969-113">DSC [yapılandırması](configurations.md) , bir veya daha fazla hedef bilgisayar (düğüm) yapılandırmak istediğinizi tanımlayan özel bir PowerShell işlevidir.</span><span class="sxs-lookup"><span data-stu-id="57969-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="57969-114">PowerShell ıSE veya başka bir PowerShell düzenleyicisinde aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="57969-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

> <span data-ttu-id="57969-115">! Aynı yapılandırmada birçok DSC kaynaklarıyla çalışabilmek için birden çok modülün içeri aktarılması gereken daha Gelişmiş senaryolarda, her modülün kullanarak `Import-DscResource`ayrı bir satıra yerleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="57969-115">!Important In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a seperate line using `Import-DscResource`.</span></span>
> <span data-ttu-id="57969-116">Bu, kaynak denetiminde bakım yapmak ve Azure Durum Yapılandırması 'nda DSC ile çalışırken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="57969-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="57969-117">Dosyayı "HelloWorld. ps1" olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="57969-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="57969-118">Bir yapılandırma tanımlamak bir Işlevi tanımlamaya benzer.</span><span class="sxs-lookup"><span data-stu-id="57969-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="57969-119">**Düğüm** bloğu, bu durumda `localhost`yapılandırılacak hedef düğümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="57969-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="57969-120">Yapılandırma [tek bir](../resources/resources.md)kaynağı, `File` kaynağı çağırır.</span><span class="sxs-lookup"><span data-stu-id="57969-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="57969-121">Kaynaklar, hedef düğümün yapılandırma tarafından tanımlanan durumda olmasını sağlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="57969-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="57969-122">Yapılandırmayı derle</span><span class="sxs-lookup"><span data-stu-id="57969-122">Compile the configuration</span></span>

<span data-ttu-id="57969-123">Bir DSC yapılandırmasının bir düğüme uygulanması için öncelikle bir MOF dosyasına derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="57969-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="57969-124">Bir işlev gibi yapılandırmayı çalıştırmak, `Node` blok tarafından tanımlanan her düğüm için bir ". mof" dosyası derler.</span><span class="sxs-lookup"><span data-stu-id="57969-124">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="57969-125">Yapılandırmayı çalıştırmak için, geçerli kapsamda "HelloWorld. ps1" betiğinizin *kaynağını* yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="57969-125">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="57969-126">Daha fazla bilgi için bkz. [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="57969-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="57969-127">*Nokta kaynağı* "HelloWorld. ps1" betiğinizi, depoladığınız yolu `. ` (nokta, boşluk) sonra yazarak yazın.</span><span class="sxs-lookup"><span data-stu-id="57969-127">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="57969-128">Daha sonra, bir Işlev gibi çağırarak yapılandırmanızı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57969-128">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="57969-129">Bu, aşağıdaki çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="57969-129">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="57969-130">Yapılandırmayı Uygula</span><span class="sxs-lookup"><span data-stu-id="57969-130">Apply the configuration</span></span>

<span data-ttu-id="57969-131">Artık derlenmiş MOF 'ye sahip olduğunuza göre, [Başlangıç-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 'ini çağırarak yapılandırmayı hedef düğüme (Bu durumda yerel bilgisayar) uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57969-131">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="57969-132">Cmdlet 'i, yapılandırmayı uygulamak için [yerel Configuration Manager (LCM)](../managing-nodes/metaConfig.md), DSC altyapısını söyler. `Start-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="57969-132">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="57969-133">LCM, yapılandırmayı uygulamak için DSC kaynaklarını çağırma işini yapar.</span><span class="sxs-lookup"><span data-stu-id="57969-133">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="57969-134">`Start-DSCConfiguration` Cmdlet 'ini yürütmek için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="57969-134">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="57969-135">"Localhost. mof" `-Path` parametresinin parametreye depolandığı dizin yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="57969-135">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="57969-136">Cmdlet 'i herhangi bir "\<ComputerName\>. mof" dosyası için belirtilen dizine bakar. `Start-DSCConfiguration`</span><span class="sxs-lookup"><span data-stu-id="57969-136">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="57969-137">`Start-DSCConfiguration` Cmdlet 'i, bulduğu her ". mof" dosyasını dosya adı ("localhost", "Server01", "DC-02" vb.) tarafından belirtilen ComputerName 'a uygulamayı dener.</span><span class="sxs-lookup"><span data-stu-id="57969-137">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="57969-138">Parametresi belirtilmemişse, `Start-DSCConfiguration` işlemi gerçekleştirmek için bir arka plan işi oluşturur. `-Wait`</span><span class="sxs-lookup"><span data-stu-id="57969-138">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="57969-139">Parametresinin **belirtilmesi** işlemin ayrıntılı çıkışını izlemenize olanak sağlar. `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="57969-139">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="57969-140">`-Wait`, ve `-Verbose` isteğe bağlı parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="57969-140">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="57969-141">Yapılandırmayı test etme</span><span class="sxs-lookup"><span data-stu-id="57969-141">Test the configuration</span></span>

<span data-ttu-id="57969-142">`Start-DSCConfiguration` Cmdlet tamamlandıktan sonra, belirttiğiniz konumda bir "HelloWorld. txt" dosyası görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="57969-142">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="57969-143">İçeriği [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet 'i ile doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57969-143">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="57969-144">Ayrıca, [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)kullanarak geçerli durumu *Test* edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57969-144">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="57969-145">Düğüm, uygulanan yapılandırmayla uyumluysa, çıkış "true" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57969-145">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="57969-146">Yapılandırma yeniden uygulanıyor</span><span class="sxs-lookup"><span data-stu-id="57969-146">Re-applying the configuration</span></span>

<span data-ttu-id="57969-147">Yapılandırmanızın yeniden uygulandığını görmek için, yapılandırmanız tarafından oluşturulan metin dosyasını kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57969-147">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="57969-148">`Start-DSCConfiguration` Cmdlet 'ini`-UseExisting` parametresiyle kullanın.</span><span class="sxs-lookup"><span data-stu-id="57969-148">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="57969-149">Parametresi, en son başarıyla uygulanan yapılandırmayı temsil eden "Current. mof" dosyasını yeniden uygulamaya yönlendirir `Start-DSCConfiguration`. `-UseExisting`</span><span class="sxs-lookup"><span data-stu-id="57969-149">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="57969-150">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="57969-150">Next steps</span></span>

- <span data-ttu-id="57969-151">DSC yapılandırmalarında DSC yapılandırması hakkında daha fazla bilgi [edinin.](configurations.md)</span><span class="sxs-lookup"><span data-stu-id="57969-151">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="57969-152">Hangi DSC kaynaklarının kullanılabilir olduğunu ve [DSC kaynaklarında](../resources/resources.md)özel DSC kaynakları oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="57969-152">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="57969-153">[POWERSHELL GALERISI](https://www.powershellgallery.com/)DSC yapılandırma ve kaynaklarını bulun.</span><span class="sxs-lookup"><span data-stu-id="57969-153">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
