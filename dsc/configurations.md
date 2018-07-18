---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC yapılandırmaları
ms.openlocfilehash: 171068acb51f44e31c81e63f6640222ef71bee38
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093703"
---
# <a name="dsc-configurations"></a><span data-ttu-id="a775a-103">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="a775a-103">DSC Configurations</span></span>

> <span data-ttu-id="a775a-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a775a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a775a-105">DSC, özel bir işlev türü tanımlayan PowerShell betiklerini yapılandırmalardır.</span><span class="sxs-lookup"><span data-stu-id="a775a-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="a775a-106">Bir yapılandırmasını tanımlamak için PowerShell anahtar sözcüğünü kullanın. **yapılandırma**.</span><span class="sxs-lookup"><span data-stu-id="a775a-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

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

<span data-ttu-id="a775a-107">Komut dosyasını bir .ps1 dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a775a-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="a775a-108">Yapılandırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a775a-108">Configuration syntax</span></span>

<span data-ttu-id="a775a-109">Bir yapılandırma betiği aşağıdaki bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="a775a-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="a775a-110">**Yapılandırma** blok.</span><span class="sxs-lookup"><span data-stu-id="a775a-110">The **Configuration** block.</span></span> <span data-ttu-id="a775a-111">Dış betik bloğundaki budur.</span><span class="sxs-lookup"><span data-stu-id="a775a-111">This is the outermost script block.</span></span> <span data-ttu-id="a775a-112">Kullanarak tanımladığınız **yapılandırma** anahtar sözcüğü ve bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="a775a-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="a775a-113">Bu durumda, yapılandırma "MyDscConfiguration" adıdır.</span><span class="sxs-lookup"><span data-stu-id="a775a-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="a775a-114">Bir veya daha fazla **düğüm** engeller.</span><span class="sxs-lookup"><span data-stu-id="a775a-114">One or more **Node** blocks.</span></span> <span data-ttu-id="a775a-115">Bunlar, yapılandırmakta olduğunuz düğüm (bilgisayarların veya Vm'leri) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a775a-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="a775a-116">Yukarıdaki yapılandırmada, bir tane olduğunu **düğüm** bir bilgisayarı hedef blok, "TEST-PC1" adlı.</span><span class="sxs-lookup"><span data-stu-id="a775a-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="a775a-117">Bir veya daha fazla kaynak engeller.</span><span class="sxs-lookup"><span data-stu-id="a775a-117">One or more resource blocks.</span></span> <span data-ttu-id="a775a-118">Burada, yapılandırma kaynaklarını özelliklerini yapılandırmayı ayarlar budur.</span><span class="sxs-lookup"><span data-stu-id="a775a-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="a775a-119">Bu durumda, iki kaynak blok, her biri "WindowsFeature" kaynak çağrısı vardır.</span><span class="sxs-lookup"><span data-stu-id="a775a-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="a775a-120">İçinde bir **yapılandırma** blok, normalde bir PowerShell işlevde verebilecek her şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a775a-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="a775a-121">Örneğin, önceki örnekte sabit yapılandırmasında, hedef bilgisayarın adını kod gelmedi isterseniz düğüm adı için bir parametre ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a775a-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {
    param(
        [string[]]$ComputerName='localhost'
    )
    Node $ComputerName {
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
MyDscConfiguration -ComputerName $ComputerName
```

<span data-ttu-id="a775a-122">Bu örnekte, düğümün adı olarak geçirerek belirttiğiniz **ComputerName** yapılandırma derlediğinizde parametresi.</span><span class="sxs-lookup"><span data-stu-id="a775a-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="a775a-123">Adı varsayılan olarak "localhost".</span><span class="sxs-lookup"><span data-stu-id="a775a-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="a775a-124">Yapılandırma derleme</span><span class="sxs-lookup"><span data-stu-id="a775a-124">Compiling the configuration</span></span>

<span data-ttu-id="a775a-125">Bir yapılandırma yürürlüğe koymasına önce MOF belgeye derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a775a-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="a775a-126">Bunun için bir PowerShell işlevini çağırırdı gibi yapılandırma çağırarak.</span><span class="sxs-lookup"><span data-stu-id="a775a-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="a775a-127">Yalnızca yapılandırma adını içeren örnek son satırının yapılandırma çağırır.</span><span class="sxs-lookup"><span data-stu-id="a775a-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="a775a-128">Bir yapılandırma çağırmak için işlev genel kapsamda (ile diğer PowerShell bir işlev gibi) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a775a-128">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="a775a-129">Bu sorun ya da göre "nokta betik kaynak belirleme" hale getirebilir veya F5'i kullanarak ya da tıklandığında yapılandırma betiğini çalıştırarak **betiğini Çalıştır** işe düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a775a-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="a775a-130">Nokta kaynak için betik komutu çalıştırmak `. .\myConfig.ps1` burada `myConfig.ps1` yapılandırmanızı içeren betik dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="a775a-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="a775a-131">Bu yapılandırma, çağırdığınızda bu:</span><span class="sxs-lookup"><span data-stu-id="a775a-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="a775a-132">Tüm değişkenler çözümler</span><span class="sxs-lookup"><span data-stu-id="a775a-132">Resolves all variables</span></span>
- <span data-ttu-id="a775a-133">Geçerli dizin yapılandırma olarak aynı ada sahip bir klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a775a-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="a775a-134">Adlı bir dosya oluşturur _NodeName_.mof yeni dizininde nereye _NodeName_ hedef düğüm yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="a775a-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="a775a-135">Birden fazla düğüm varsa, her düğüm için bir MOF dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a775a-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="a775a-136">MOF dosyası tüm hedef düğüm için yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a775a-136">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="a775a-137">Bu nedenle, güvenliğini sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a775a-137">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="a775a-138">Daha fazla bilgi için [MOF dosyasının güvenliğini sağlama](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="a775a-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="a775a-139">İlk yapılandırması aşağıdaki klasör yapısındaki sonuçları yukarıda derleme:</span><span class="sxs-lookup"><span data-stu-id="a775a-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="a775a-140">Yapılandırma ikinci örnekte olduğu gibi bir parametre alırsa, derleme zamanında sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a775a-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="a775a-141">Bu nasıl görüneceğini aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a775a-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="a775a-142">DependsOn kullanma</span><span class="sxs-lookup"><span data-stu-id="a775a-142">Using DependsOn</span></span>

<span data-ttu-id="a775a-143">Yararlı bir DSC anahtar sözcüğü **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="a775a-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="a775a-144">Genellikle (mutlaka rağmen), DSC kaynakları içine yapılandırmayı göründükleri sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a775a-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="a775a-145">Ancak, **DependsOn** belirten bağımlı kaynaklar diğer kaynaklara ve bunlar hangi kaynak örnekleri tanımlanmış sırasını bağımsız olarak doğru sırayla uygulanır LCM sağlar.</span><span class="sxs-lookup"><span data-stu-id="a775a-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="a775a-146">Örneğin, bir yapılandırma, belirtebilirsiniz örneği **kullanıcı** kaynak varlığını bağlıdır bir **grubu** örneği:</span><span class="sxs-lookup"><span data-stu-id="a775a-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = 'Present'
            GroupName = 'TestGroup'
        }

        User UserExample {
            Ensure = 'Present'
            UserName = 'TestUser'
            FullName = 'TestUser'
            DependsOn = '[Group]GroupExample'
        }
    }
}
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="a775a-147">Yapılandırmanızda yeni kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="a775a-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="a775a-148">Önceki örneklerde çalıştırdıysanız, açıkça içeri aktarmadan bir kaynağı kullanmakta olduğunuz uyarı fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a775a-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="a775a-149">Bugün, DSC ile 12 kaynağı da PSDesiredStateConfiguration modülün bir parçası gelir.</span><span class="sxs-lookup"><span data-stu-id="a775a-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="a775a-150">Diğer kaynakları harici modüllerdeki yerleştirilmelidir `$env:PSModulePath` LCM tarafından tanınması için.</span><span class="sxs-lookup"><span data-stu-id="a775a-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="a775a-151">Yeni bir cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), sistemde yüklenmiş ve kullanıma göre LCM hangi kaynakların belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a775a-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="a775a-152">Bu modüller, yerleştirildi sonra `$env:PSModulePath` ve tarafından tanınır [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), bunların hala yapılandırmanızı içinde yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a775a-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="a775a-153">**Import-DscResource** içinde yalnızca tanınabilmesi dinamik bir anahtar sözcüğü bir **yapılandırma** blok (yani olmadığı bir cmdlet'i).</span><span class="sxs-lookup"><span data-stu-id="a775a-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="a775a-154">**Import-DscResource** iki parametrelerini destekler:</span><span class="sxs-lookup"><span data-stu-id="a775a-154">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="a775a-155">**ModuleName** kullanmanın önerilen yöntem **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="a775a-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="a775a-156">Bu, (bir dize dizisi modülü adlarının yanı sıra) içeri aktarılacak kaynakları içeren modül adını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a775a-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="a775a-157">**Adı** alınacak kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="a775a-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="a775a-158">Bu kolay adı "Name" döndürdüğü değil [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ancak kullanıldığında sınıf adı kaynak şemasını tanımlama (olarak döndürülen **ResourceType** tarafından [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="a775a-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="a775a-159">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a775a-159">See Also</span></span>

- [<span data-ttu-id="a775a-160">Windows PowerShell Desired State Configuration ' ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="a775a-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="a775a-161">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="a775a-161">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="a775a-162">Yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a775a-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)