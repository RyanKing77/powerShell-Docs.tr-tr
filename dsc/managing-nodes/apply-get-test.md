---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Düğümlerde Test Yapılandırmaları Uygulama, Edinme ve Sınama
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079719"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="da37a-103">Düğümlerde Test Yapılandırmaları Uygulama, Edinme ve Sınama</span><span class="sxs-lookup"><span data-stu-id="da37a-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="da37a-104">Bu kılavuz, bir hedef düğüm yapılandırmaları ile çalışmaya nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="da37a-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="da37a-105">Bu kılavuz, aşağıdaki adımlar ayrılır:</span><span class="sxs-lookup"><span data-stu-id="da37a-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="da37a-106">Bir yapılandırmasını Uygula</span><span class="sxs-lookup"><span data-stu-id="da37a-106">Apply a Configuration</span></span>

<span data-ttu-id="da37a-107">Uygulama ve bir yapılandırmasını yönetmek için bir ".mof" dosyası oluşturmak gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="da37a-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="da37a-108">Aşağıdaki kod, bu kılavuzda kullanılan basit bir yapılandırmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="da37a-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="da37a-109">Bu yapılandırmanın derlenmesi iki ".mof" dosya ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="da37a-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="da37a-110">Bir yapılandırmayı uygulamak için kullanma [Başlat-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="da37a-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="da37a-111">`-Path` Parametresi ".mof" dosyalarının bulunduğu bir dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="da37a-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="da37a-112">Hayır ise `-Computername` belirtilen `Start-DSCConfiguration` '.mof' dosya adı tarafından belirtilen bilgisayar adı her yapılandırma uygulamak dener (\<computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="da37a-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="da37a-113">Belirtin `-Verbose` için `Start-DSCConfiguration` daha ayrıntılı çıktıyı görmek için.</span><span class="sxs-lookup"><span data-stu-id="da37a-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="da37a-114">Varsa `-Wait` belirtilmezse, oluşturulan bir işi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="da37a-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="da37a-115">Oluşturulan projeyi bir olacaktır **ChildJob** her ".mof" dosyası için işlenen tarafından `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="da37a-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="da37a-116">Bir yapılandırma uzun sürüyor ve durdurmak istiyorsanız, kullanabilirsiniz [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) yerel düğüm üzerinde uygulamayı durdurma.</span><span class="sxs-lookup"><span data-stu-id="da37a-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="da37a-117">İşlem tamamlandıktan sonra tarafından döndürülen iş nesnesi aracılığıyla işlerin durumunu görüntüleyebilirsiniz [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="da37a-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="da37a-118">Görmek için **ayrıntılı** görüntülemek için aşağıdaki komutları kullanın, çıktı **ayrıntılı** her akış **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="da37a-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="da37a-119">PowerShell işleri hakkında daha fazla bilgi için bkz. [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="da37a-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="da37a-120">PowerShell 5. 0'den itibaren `-UseExisting` parametresi eklenmiş `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="da37a-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="da37a-121">Belirterek `-UseExisting`, biri tarafından belirtilen yerine var olan uygulanan yapılandırmasını kullanmak için cmdlet toplamasını `-Path` parametresi.</span><span class="sxs-lookup"><span data-stu-id="da37a-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="da37a-122">Bir yapılandırmayı test etme</span><span class="sxs-lookup"><span data-stu-id="da37a-122">Test a Configuration</span></span>

<span data-ttu-id="da37a-123">Şu anda uygulanan yapılandırmayı kullanarak test [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="da37a-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="da37a-124">`Test-DSCConfiguration` döndüreceği `True` düğümü uyumlu ise ve `False` değilse.</span><span class="sxs-lookup"><span data-stu-id="da37a-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="da37a-125">PowerShell 5. 0'den itibaren `-Detailed` parametresi, bir nesne koleksiyonları döndüren eklenen **ResourcesInDesiredState** ve **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="da37a-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="da37a-126">PowerShell 5. 0 ', başlangıç uygulanmadan cse'den bir yapılandırmasını test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da37a-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="da37a-127">`-ReferenceConfiguration` Parametreyi kabul eden düğümü karşı test etmek için ".mof" dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="da37a-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="da37a-128">Hayır **ayarlamak** eylemleri düğümü karşı alınır.</span><span class="sxs-lookup"><span data-stu-id="da37a-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="da37a-129">PowerShell 4. 0'da, bu uygulamadan bir yapılandırmasını test etmek için geçici çözümler vardır, ancak burada açıklanmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="da37a-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="da37a-130">Yapılandırma değerlerini alma</span><span class="sxs-lookup"><span data-stu-id="da37a-130">Get Configuration Values</span></span>

<span data-ttu-id="da37a-131">[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet şu anda uygulanan yapılandırmasında yapılandırılan tüm kaynaklar için geçerli değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="da37a-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="da37a-132">Bizim örnek yapılandırma çıkışı başarıyla uygulandığında şuna benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="da37a-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="da37a-133">Yapılandırma durumunu Al</span><span class="sxs-lookup"><span data-stu-id="da37a-133">Get Configuration Status</span></span>

<span data-ttu-id="da37a-134">PowerShell 5. 0'den itibaren [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet'i düğüme uygulanan yapılandırmaları geçmişini görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="da37a-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="da37a-135">PowerShell DSC uygulanan son {{N}} yapılandırmaları izler **anında iletme** veya **çekme** modu.</span><span class="sxs-lookup"><span data-stu-id="da37a-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="da37a-136">Bu, tüm içerir *tutarlılık* LCM tarafından yürütülen denetler.</span><span class="sxs-lookup"><span data-stu-id="da37a-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="da37a-137">Varsayılan olarak, `Get-DSCConfigurationStatus` yalnızca son geçmiş girişinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="da37a-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="da37a-138">Kullanım `-All` tüm yapılandırma durumu geçmişini görmek için parametre.</span><span class="sxs-lookup"><span data-stu-id="da37a-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="da37a-139">Konuyu uzatmamak amacıyla çıktı kesildi.</span><span class="sxs-lookup"><span data-stu-id="da37a-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="da37a-140">Yapılandırma belgelerini yönetme</span><span class="sxs-lookup"><span data-stu-id="da37a-140">Manage Configuration Documents</span></span>

<span data-ttu-id="da37a-141">Birlikte çalışarak LCM yapılandırma düğümünün yönetir **yapılandırma belgelerini**.</span><span class="sxs-lookup"><span data-stu-id="da37a-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="da37a-142">Bu ".mof" dosyalar "C:\Windows\System32\Configuration" dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="da37a-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="da37a-143">PowerShell 5. 0'den itibaren [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) gelecekteki tutarlılık denetimleri durdurmak veya uygulandığında hatalı bir yapılandırma kaldırmak için ".mof" dosyaları kaldırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da37a-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="da37a-144">`-Stage` Parametresi, kaldırmak istediğiniz hangi ".mof" dosyası belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="da37a-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="da37a-145">PowerShell 4. 0'da, yine de kullanarak doğrudan bu ".mof" dosyaları kaldırabilirsiniz [Kaldır öğesini](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="da37a-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="da37a-146">Yapılandırmaları yayımlama</span><span class="sxs-lookup"><span data-stu-id="da37a-146">Publish Configurations</span></span>

<span data-ttu-id="da37a-147">PowerShell 5. 0'den itibaren [Yayımla-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet'i eklendi.</span><span class="sxs-lookup"><span data-stu-id="da37a-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="da37a-148">Bu cmdlet'i ".mof" dosyasını uzak bilgisayara uygulanmadan cse'den yayımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="da37a-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="da37a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da37a-149">See also</span></span>

- [<span data-ttu-id="da37a-150">, Test, alma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="da37a-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
