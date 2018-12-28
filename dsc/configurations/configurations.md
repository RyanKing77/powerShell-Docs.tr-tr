---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC yapılandırmaları
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405777"
---
# <a name="dsc-configurations"></a><span data-ttu-id="44e27-103">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="44e27-103">DSC Configurations</span></span>

> <span data-ttu-id="44e27-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="44e27-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="44e27-105">DSC, özel bir işlev türü tanımlayan PowerShell betiklerini yapılandırmalardır.</span><span class="sxs-lookup"><span data-stu-id="44e27-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="44e27-106">Bir yapılandırmasını tanımlamak için PowerShell anahtar sözcüğünü kullanın. **yapılandırma**.</span><span class="sxs-lookup"><span data-stu-id="44e27-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="44e27-107">Betik olarak Kaydet bir `.ps1` dosya.</span><span class="sxs-lookup"><span data-stu-id="44e27-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="44e27-108">Yapılandırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44e27-108">Configuration syntax</span></span>

<span data-ttu-id="44e27-109">Bir yapılandırma betiği aşağıdaki bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="44e27-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="44e27-110">**Yapılandırma** blok.</span><span class="sxs-lookup"><span data-stu-id="44e27-110">The **Configuration** block.</span></span> <span data-ttu-id="44e27-111">Dış betik bloğundaki budur.</span><span class="sxs-lookup"><span data-stu-id="44e27-111">This is the outermost script block.</span></span> <span data-ttu-id="44e27-112">Kullanarak tanımladığınız **yapılandırma** anahtar sözcüğü ve bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="44e27-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="44e27-113">Bu durumda, yapılandırma "MyDscConfiguration" adıdır.</span><span class="sxs-lookup"><span data-stu-id="44e27-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="44e27-114">Bir veya daha fazla **düğüm** engeller.</span><span class="sxs-lookup"><span data-stu-id="44e27-114">One or more **Node** blocks.</span></span> <span data-ttu-id="44e27-115">Bunlar, yapılandırmakta olduğunuz düğüm (bilgisayarların veya Vm'leri) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44e27-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="44e27-116">Yukarıdaki yapılandırmada, bir tane olduğunu **düğüm** bir bilgisayarı hedef blok, "TEST-PC1" adlı.</span><span class="sxs-lookup"><span data-stu-id="44e27-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="44e27-117">Düğümü blok birden çok bilgisayar adlarını kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="44e27-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="44e27-118">Bir veya daha fazla kaynak engeller.</span><span class="sxs-lookup"><span data-stu-id="44e27-118">One or more resource blocks.</span></span> <span data-ttu-id="44e27-119">Burada, yapılandırma kaynaklarını özelliklerini yapılandırmayı ayarlar budur.</span><span class="sxs-lookup"><span data-stu-id="44e27-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="44e27-120">Bu durumda, iki kaynak blok, her biri "WindowsFeature" kaynak çağrısı vardır.</span><span class="sxs-lookup"><span data-stu-id="44e27-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="44e27-121">İçinde bir **yapılandırma** blok, normalde bir PowerShell işlevde verebilecek her şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44e27-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="44e27-122">Örneğin, önceki örnekte sabit yapılandırmasında, hedef bilgisayarın adını kod gelmedi isterseniz düğüm adı için bir parametre ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44e27-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="44e27-123">Bu örnekte, düğümün adı olarak geçirerek belirttiğiniz **ComputerName** yapılandırma derlediğinizde parametresi.</span><span class="sxs-lookup"><span data-stu-id="44e27-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="44e27-124">Adı varsayılan olarak "localhost".</span><span class="sxs-lookup"><span data-stu-id="44e27-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="44e27-125">**Düğüm** blok birden çok bilgisayar adları da kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="44e27-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="44e27-126">Yukarıdaki örnekte kullanabilir `-ComputerName` parametresi veya doğrudan bilgisayarlara geçişi bir virgülle ayrılmış listesi **düğüm** blok.</span><span class="sxs-lookup"><span data-stu-id="44e27-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="44e27-127">Bilgisayarlara listesini belirtirken **düğüm** blok, gelen bir yapılandırması dizi gösterimi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44e27-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="44e27-128">Yapılandırma derleme</span><span class="sxs-lookup"><span data-stu-id="44e27-128">Compiling the configuration</span></span>

<span data-ttu-id="44e27-129">Bir yapılandırma yürürlüğe koymasına önce MOF belgeye derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44e27-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="44e27-130">Bunun için bir PowerShell işlevini çağırırdı gibi yapılandırma çağırarak.</span><span class="sxs-lookup"><span data-stu-id="44e27-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="44e27-131">Yalnızca yapılandırma adını içeren örnek son satırının yapılandırma çağırır.</span><span class="sxs-lookup"><span data-stu-id="44e27-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="44e27-132">Bir yapılandırma çağırmak için işlev genel kapsamda (ile diğer PowerShell bir işlev gibi) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44e27-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="44e27-133">Bu sorun ya da göre "nokta betik kaynak belirleme" hale getirebilir veya F5'i kullanarak ya da tıklandığında yapılandırma betiğini çalıştırarak **betiğini Çalıştır** işe düğmesi.</span><span class="sxs-lookup"><span data-stu-id="44e27-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="44e27-134">Nokta kaynak için betik komutu çalıştırmak `. .\myConfig.ps1` burada `myConfig.ps1` yapılandırmanızı içeren betik dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="44e27-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="44e27-135">Bu yapılandırma, çağırdığınızda bu:</span><span class="sxs-lookup"><span data-stu-id="44e27-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="44e27-136">Tüm değişkenler çözümler</span><span class="sxs-lookup"><span data-stu-id="44e27-136">Resolves all variables</span></span>
- <span data-ttu-id="44e27-137">Geçerli dizin yapılandırma olarak aynı ada sahip bir klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44e27-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="44e27-138">Adlı bir dosya oluşturur _NodeName_.mof yeni dizininde nereye _NodeName_ hedef düğüm yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="44e27-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="44e27-139">Birden fazla düğüm varsa, her düğüm için bir MOF dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="44e27-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="44e27-140">MOF dosyası tüm hedef düğüm için yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="44e27-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="44e27-141">Bu nedenle, güvenliğini sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="44e27-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="44e27-142">Daha fazla bilgi için [MOF dosyasının güvenliğini sağlama](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="44e27-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="44e27-143">İlk yapılandırması aşağıdaki klasör yapısındaki sonuçları yukarıda derleme:</span><span class="sxs-lookup"><span data-stu-id="44e27-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="44e27-144">Yapılandırma ikinci örnekte olduğu gibi bir parametre alırsa, derleme zamanında sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44e27-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="44e27-145">Bu nasıl görüneceğini aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="44e27-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="44e27-146">Yapılandırmanızda yeni kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="44e27-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="44e27-147">Önceki örneklerde çalıştırdıysanız, açıkça içeri aktarmadan bir kaynağı kullanmakta olduğunuz uyarı fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44e27-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="44e27-148">Bugün, DSC ile 12 kaynağı da PSDesiredStateConfiguration modülün bir parçası gelir.</span><span class="sxs-lookup"><span data-stu-id="44e27-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="44e27-149">Cmdlet'in [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), sistemde yüklenmiş ve kullanıma göre LCM hangi kaynakların belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44e27-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="44e27-150">Bu modüller, yerleştirildi sonra `$env:PSModulePath` ve tarafından tanınır [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), bunların hala yapılandırmanızı içinde yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44e27-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="44e27-151">**Import-DscResource** içinde yalnızca tanınabilmesi dinamik bir anahtar sözcüğü bir **yapılandırma** blok, bir cmdlet değildir.</span><span class="sxs-lookup"><span data-stu-id="44e27-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="44e27-152">**Import-DscResource** iki parametrelerini destekler:</span><span class="sxs-lookup"><span data-stu-id="44e27-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="44e27-153">**ModuleName** kullanmanın önerilen yöntem **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="44e27-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="44e27-154">Bu, (bir dize dizisi modülü adlarının yanı sıra) içeri aktarılacak kaynakları içeren modül adını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="44e27-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="44e27-155">**Adı** alınacak kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="44e27-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="44e27-156">Bu kolay adı "Name" döndürdüğü değil [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ancak kullanıldığında sınıf adı kaynak şemasını tanımlama (olarak döndürülen **ResourceType** tarafından [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="44e27-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="44e27-157">Kullanma hakkında daha fazla bilgi için `Import-DSCResource`, bkz: [Import-DSCResource kullanma](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="44e27-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="44e27-158">PowerShell v4 ve v5 farklılıkları</span><span class="sxs-lookup"><span data-stu-id="44e27-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="44e27-159">DSC kaynakları PowerShell 4. 0'depolanması gereken yere farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="44e27-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="44e27-160">Daha fazla bilgi için [kaynak konumu](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="44e27-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="44e27-161">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="44e27-161">See Also</span></span>

- [<span data-ttu-id="44e27-162">Windows PowerShell Desired State Configuration ' ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="44e27-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="44e27-163">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="44e27-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="44e27-164">Yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="44e27-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
