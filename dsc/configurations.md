---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC yapılandırmaları
ms.openlocfilehash: 8b44fd9a715c217ee198ea343cdffbfab1193625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="6caf5-103">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="6caf5-103">DSC Configurations</span></span>

><span data-ttu-id="6caf5-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6caf5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6caf5-105">DSC yapılandırmaları özel türde bir işlevi tanımlayan PowerShell betiklerdir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="6caf5-106">Bir yapılandırma tanımlamak için PowerShell anahtar sözcüğü kullanın **yapılandırma**.</span><span class="sxs-lookup"><span data-stu-id="6caf5-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="6caf5-107">Komut dosyasını bir .ps1 dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6caf5-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="6caf5-108">Yapılandırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6caf5-108">Configuration syntax</span></span>

<span data-ttu-id="6caf5-109">Bir yapılandırma betiğini aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="6caf5-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="6caf5-110">**Yapılandırma** bloğu.</span><span class="sxs-lookup"><span data-stu-id="6caf5-110">The **Configuration** block.</span></span> <span data-ttu-id="6caf5-111">Dış betik bloğu budur.</span><span class="sxs-lookup"><span data-stu-id="6caf5-111">This is the outermost script block.</span></span> <span data-ttu-id="6caf5-112">Kullanarak tanımladığınız **yapılandırma** anahtar sözcüğü ve sağlayan bir adı.</span><span class="sxs-lookup"><span data-stu-id="6caf5-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="6caf5-113">Bu durumda, yapılandırma "MyDscConfiguration" adıdır.</span><span class="sxs-lookup"><span data-stu-id="6caf5-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="6caf5-114">Bir veya daha fazla **düğümü** engeller.</span><span class="sxs-lookup"><span data-stu-id="6caf5-114">One or more **Node** blocks.</span></span> <span data-ttu-id="6caf5-115">Bunlar, yapılandırmakta olduğunuz düğümleri (bilgisayarların veya VM'ler) tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6caf5-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="6caf5-116">Yukarıdaki yapılandırmada bir olduğundan **düğümü** "TEST-PC1" adlı bir bilgisayarı hedef blok.</span><span class="sxs-lookup"><span data-stu-id="6caf5-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="6caf5-117">Bir veya daha fazla kaynak engeller.</span><span class="sxs-lookup"><span data-stu-id="6caf5-117">One or more resource blocks.</span></span> <span data-ttu-id="6caf5-118">Burada yapılandırma özellikleri, yapılandırma kaynaklara ilişkin ayarlar budur.</span><span class="sxs-lookup"><span data-stu-id="6caf5-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="6caf5-119">Bu durumda, her biri çağrısı "WindowsFeature" kaynak iki kaynak blokları vardır.</span><span class="sxs-lookup"><span data-stu-id="6caf5-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="6caf5-120">İçinde bir **yapılandırma** bloğu, normalde bir PowerShell işlevinde verebilir herhangi bir şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6caf5-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="6caf5-121">Örneğin, önceki örnekte, sabit yapılandırmasında, hedef bilgisayarın adını kod gelmedi istiyorsanız düğüm adı için bir parametre ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6caf5-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

<span data-ttu-id="6caf5-122">Bu örnekte, düğümün adı olarak geçirerek belirttiğiniz **ComputerName** yapılandırma derlediğinizde parametresi.</span><span class="sxs-lookup"><span data-stu-id="6caf5-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="6caf5-123">Adı varsayılan olarak "localhost".</span><span class="sxs-lookup"><span data-stu-id="6caf5-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="6caf5-124">Yapılandırmayı derleme</span><span class="sxs-lookup"><span data-stu-id="6caf5-124">Compiling the configuration</span></span>

<span data-ttu-id="6caf5-125">Bir yapılandırma yürürlüğe önce bir MOF belgeye derleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="6caf5-126">Bunun için bir PowerShell işlevi gibi yapılandırma çağırarak.</span><span class="sxs-lookup"><span data-stu-id="6caf5-126">You do this by calling the configuration like you would a PowerShell function.</span></span>
<span data-ttu-id="6caf5-127">Bu yapılandırma, yalnızca adını içeren örnek son satırının yapılandırma çağırır.</span><span class="sxs-lookup"><span data-stu-id="6caf5-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="6caf5-128">**Not:** bir yapılandırma çağrılacak işlev genel kapsamda (işleviyle herhangi diğer PowerShell gibi) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6caf5-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
><span data-ttu-id="6caf5-129">Bu durum ya da göre "nokta betik kaynak belirleme" hale getirebilir veya F5 kullanarak veya tıklayarak yapılandırma komut dosyası çalıştırarak **komut dosyasını Çalıştır** işe düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6caf5-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
><span data-ttu-id="6caf5-130">Nokta kaynak için komut dosyası, komutu çalıştırmak `. .\myConfig.ps1` burada `myConfig.ps1` yapılandırmanızı içeren komut dosyası adıdır.</span><span class="sxs-lookup"><span data-stu-id="6caf5-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="6caf5-131">Bu yapılandırma, çağırdığınızda:</span><span class="sxs-lookup"><span data-stu-id="6caf5-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="6caf5-132">Tüm değişkenleri çözümler</span><span class="sxs-lookup"><span data-stu-id="6caf5-132">Resolves all variables</span></span>
- <span data-ttu-id="6caf5-133">Geçerli dizinde yapılandırma olarak aynı ada sahip bir klasör oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6caf5-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="6caf5-134">Adlı bir dosya oluşturur _NodeName_yeni dizininde .mof nerede _NodeName_ hedef düğüm yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="6caf5-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
    <span data-ttu-id="6caf5-135">Birden fazla düğüm varsa, her düğüm için bir MOF dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6caf5-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="6caf5-136">**Not**: MOF dosyası tüm hedef düğüm için yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="6caf5-137">Bu nedenle, daha güvenli tutmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-137">Because of this, it’s important to keep it secure.</span></span>
><span data-ttu-id="6caf5-138">Daha fazla bilgi için bkz: [MOF dosyası güvenli hale getirme](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="6caf5-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="6caf5-139">İlk yapılandırması aşağıdaki klasör yapısını sonuçlarında yukarıda derleme:</span><span class="sxs-lookup"><span data-stu-id="6caf5-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="6caf5-140">Yapılandırma ikinci örnekte olduğu gibi bir parametre alırsa, derleme zamanında sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="6caf5-141">İşte, nasıl görünür:</span><span class="sxs-lookup"><span data-stu-id="6caf5-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="6caf5-142">DependsOn kullanma</span><span class="sxs-lookup"><span data-stu-id="6caf5-142">Using DependsOn</span></span>

<span data-ttu-id="6caf5-143">Yararlı bir DSC anahtar **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="6caf5-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="6caf5-144">Genellikle (mutlaka rağmen), DSC kaynakları yapılandırma içinde göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6caf5-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="6caf5-145">Ancak, **DependsOn** belirten diğer kaynaklara bağımlı kaynaklar ve bunların hangi kaynak örnekleri tanımlanan sipariş bakılmaksızın doğru sırada uygulanan LCM'yi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6caf5-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="6caf5-146">Bir yapılandırma, örneğin, belirtebilir örneği **kullanıcı** kaynak bağlıdır varlığı üzerinde bir **grup** örneği:</span><span class="sxs-lookup"><span data-stu-id="6caf5-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="6caf5-147">Yapılandırmanızda yeni kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="6caf5-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="6caf5-148">Önceki örneklerde çalıştırdıysanız, açıkça almadan kaynak kullanmakta olduğunuz uyarı fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6caf5-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="6caf5-149">Bugün, DSC da PSDesiredStateConfiguration modülünün bir parçası olarak 12 kaynakları ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="6caf5-150">Dış modüllerindeki diğer kaynakları yerleştirilmelidir `$env:PSModulePath` tarafından LCM'yi tanınması için.</span><span class="sxs-lookup"><span data-stu-id="6caf5-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="6caf5-151">Yeni bir cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), hangi kaynaklara göre LCM'yi sistemde yüklü ve kullanım için uygun olduğunu belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="6caf5-152">Bu modüller, yerleştirildi sonra `$env:PSModulePath` ve düzgün şekilde tarafından tanınan [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), bunlar yine de yapılandırmanızı içinde yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6caf5-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="6caf5-153">**İçeri aktarma DscResource** içinde yalnızca tanınmasını dinamik bir anahtar sözcüktür bir **yapılandırma** (yani olmadığı bir cmdlet) engelle.</span><span class="sxs-lookup"><span data-stu-id="6caf5-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="6caf5-154">**İçeri aktarma DscResource** iki parametreleri destekler:</span><span class="sxs-lookup"><span data-stu-id="6caf5-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="6caf5-155">**ModuleName** kullanmanın önerilen yöntem **alma DscResource**.</span><span class="sxs-lookup"><span data-stu-id="6caf5-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="6caf5-156">Bu, (bir dize dizisi modül adlarını yanı sıra) içeri aktarılacak kaynakları içeren modülü adını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6caf5-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="6caf5-157">**Ad** almak için kaynak adıdır.</span><span class="sxs-lookup"><span data-stu-id="6caf5-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="6caf5-158">Bu "Name" tarafından döndürülen kolay adı değil [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ancak kullanıldığında sınıf adı kaynak şemasını tanımlama (olarak döndürülen **ResourceType** tarafından [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="6caf5-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="6caf5-159">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6caf5-159">See Also</span></span>
* [<span data-ttu-id="6caf5-160">Windows PowerShell istenen durum yapılandırması genel bakış</span><span class="sxs-lookup"><span data-stu-id="6caf5-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="6caf5-161">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="6caf5-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="6caf5-162">Yerel Yapılandırma Yöneticisi'ni yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6caf5-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)