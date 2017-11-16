---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Kaynak geliştirme denetim listesi"
ms.openlocfilehash: 9e9855f4ad4ee6db4d9e3b90d3c9a03d81429805
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="30ac8-103">Kaynak geliştirme denetim listesi</span><span class="sxs-lookup"><span data-stu-id="30ac8-103">Resource authoring checklist</span></span>
<span data-ttu-id="30ac8-104">Bu denetim listesini yeni bir DSC kaynağı yazarken en iyi yöntemler bir listedir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="30ac8-105">.Psd1 dosya ve schema.mof her kaynak için kaynak modülü içerir</span><span class="sxs-lookup"><span data-stu-id="30ac8-105">Resource module contains .psd1 file and schema.mof for every resource</span></span> 
<span data-ttu-id="30ac8-106">Kaynağınız doğru yapısına sahip ve tüm gerekli dosyaları içeren denetleyin.</span><span class="sxs-lookup"><span data-stu-id="30ac8-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="30ac8-107">Her kaynak modül .psd1 dosyası içermelidir ve her bileşik olmayan kaynak schema.mof dosya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30ac8-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="30ac8-108">Şema içermeyen kaynaklar tarafından listelenmez **Get-DscResource** ve kullanıcıların IntelliSense kodu bu modüller karşı ISE'de yazarken kullanmak mümkün olmayacak.</span><span class="sxs-lookup"><span data-stu-id="30ac8-108">Resources that do not contain schema will not be listed by **Get-DscResource** and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span> <span data-ttu-id="30ac8-109">Parçasıdır xRemoteFile kaynak dizin yapısı, [xPSDesiredStateConfiguration kaynak Modülü](https://github.com/PowerShell/xPSDesiredStateConfiguration), aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="30ac8-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="30ac8-110">Kaynak ve şema doğru ##</span><span class="sxs-lookup"><span data-stu-id="30ac8-110">Resource and schema are correct##</span></span>
<span data-ttu-id="30ac8-111">Kaynak şemasını doğrulayın (*. schema.mof) dosyası.</span><span class="sxs-lookup"><span data-stu-id="30ac8-111">Verify the resource schema (*.schema.mof) file.</span></span> <span data-ttu-id="30ac8-112">Kullanabileceğiniz [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) geliştirmenizi ve test şemanızı yardımcı olacak.</span><span class="sxs-lookup"><span data-stu-id="30ac8-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to help develop and test your schema.</span></span> <span data-ttu-id="30ac8-113">Olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="30ac8-113">Make sure that:</span></span>
- <span data-ttu-id="30ac8-114">Özellik türleri doğru (dize, sayısal değerleri kabul özelliklerini örn kullanmayın, bunun yerine uint32 diğer sayısal türler kullanmalısınız)</span><span class="sxs-lookup"><span data-stu-id="30ac8-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="30ac8-115">Özellik öznitelikleri doğru olarak belirtilir: ([anahtarı], [gerekli], [yazma], [okuma])</span><span class="sxs-lookup"><span data-stu-id="30ac8-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="30ac8-116">[Anahtar] olarak işaretlenecek şemasında en az bir parametre içeriyor</span><span class="sxs-lookup"><span data-stu-id="30ac8-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="30ac8-117">[özelliği olmayan bir arada herhangi biri ile birlikte okuma]: [gerekli], [anahtarı], [yazma]</span><span class="sxs-lookup"><span data-stu-id="30ac8-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="30ac8-118">Birden çok niteleyicileri [dışında oku] belirtilmişse [anahtarı] öncelik kazanır</span><span class="sxs-lookup"><span data-stu-id="30ac8-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="30ac8-119">Varsa [yazma] ve [gerekli] belirtilen sonra [gerekli] önceliğe</span><span class="sxs-lookup"><span data-stu-id="30ac8-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="30ac8-120">ValueMap uygun yerlerde belirtilmiştir</span><span class="sxs-lookup"><span data-stu-id="30ac8-120">ValueMap is specified where appropriate</span></span>

<span data-ttu-id="30ac8-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="30ac8-121">Example:</span></span>
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- <span data-ttu-id="30ac8-122">Kolay ad belirtilir ve DSC adlandırma kurallarına onaylar</span><span class="sxs-lookup"><span data-stu-id="30ac8-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

<span data-ttu-id="30ac8-123">Örnek: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span><span class="sxs-lookup"><span data-stu-id="30ac8-123">Example: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span></span>

- <span data-ttu-id="30ac8-124">Her alanı anlamlı bir açıklama içeriyor.</span><span class="sxs-lookup"><span data-stu-id="30ac8-124">Every field has meaningful description.</span></span> <span data-ttu-id="30ac8-125">PowerShell GitHub deposuna iyi örnek, aşağıdaki gibi olan [. xRemoteFile schema.mof](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="30ac8-125">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="30ac8-126">Ayrıca, kullanmanız gereken **Test xDscResource** ve **Test xDscSchema** cmdlet'leri [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) kaynak ve şema otomatik olarak doğrulanamadı:</span><span class="sxs-lookup"><span data-stu-id="30ac8-126">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to automatically verify the resource and schema:</span></span>
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
<span data-ttu-id="30ac8-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="30ac8-127">For example:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="30ac8-128">Kaynak hatasız yükler</span><span class="sxs-lookup"><span data-stu-id="30ac8-128">Resource loads without errors</span></span> ##
<span data-ttu-id="30ac8-129">Kaynak modülü başarıyla yüklü olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="30ac8-129">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="30ac8-130">Bu el ile çalıştırarak elde edilebilir `Import-Module <resource_module> -force ` ve hiçbir hata oluştuğunu onaylayarak veya göre test Otomasyonu yazma.</span><span class="sxs-lookup"><span data-stu-id="30ac8-130">This can be achieved manually, by running `Import-Module <resource_module> -force ` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="30ac8-131">İkinci durumunda, bu yapıyı test durumunuzda izleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30ac8-131">In case of the latter, you can follow this structure in your test case:</span></span>
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="30ac8-132">Idempotent pozitif durumda kaynaktır</span><span class="sxs-lookup"><span data-stu-id="30ac8-132">Resource is idempotent in the positive case</span></span> 
<span data-ttu-id="30ac8-133">DSC kaynakları temel özelliklerini idempotence olması biridir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-133">One of the fundamental characteristics of DSC resources is be idempotence.</span></span> <span data-ttu-id="30ac8-134">Bu, birden çok kez bu kaynak içeren bir DSC yapılandırma uygulama her zaman aynı sonucu elde edecek olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="30ac8-135">Örneğin, aşağıdaki dosya kaynağı içeren bir yapılandırma oluşturuyoruz varsa:</span><span class="sxs-lookup"><span data-stu-id="30ac8-135">For example, if we create a configuration which contains the following File resource:</span></span>
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
<span data-ttu-id="30ac8-136">İlk kez uyguladıktan sonra dosya sınama.txt C:\test klasöründeki görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-136">After applying it for the first time, file test.txt should appear in C:\test folder.</span></span> <span data-ttu-id="30ac8-137">Ancak, aynı yapılandırmaya sahip sonraki çalıştırır (örn. hiçbir kopya sınama.txt dosyasının oluşturulmalıdır) makinenin durumunu değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="30ac8-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the test.txt file should be created).</span></span>
<span data-ttu-id="30ac8-138">Bir kaynak art arda çağırabilir ıdempotent olduğundan emin olmak için **kümesi TargetResource** kaynak doğrudan test veya çağrı **başlangıç DscConfiguration** birden çok kez uçtan uca test yaparken.</span><span class="sxs-lookup"><span data-stu-id="30ac8-138">To ensure a resource is idempotent you can repeatedly call **Set-TargetResource** when testing the resource directly, or call **Start-DscConfiguration** multiple times when doing end to end testing.</span></span> <span data-ttu-id="30ac8-139">Sonuç sonra her çalıştırılışında aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-139">The result should be the same after every run.</span></span> 


## <a name="test-user-modification-scenario"></a><span data-ttu-id="30ac8-140">Test kullanıcı değişiklik senaryosu</span><span class="sxs-lookup"><span data-stu-id="30ac8-140">Test user modification scenario</span></span> ##
<span data-ttu-id="30ac8-141">Makinenin durumunu değiştirme ve DSC yeniden çalıştırma olduğunu doğrulayabilirsiniz **kümesi TargetResource** ve **Test TargetResource** düzgün.</span><span class="sxs-lookup"><span data-stu-id="30ac8-141">By changing the state of the machine and then rerunning DSC, you can verify that **Set-TargetResource** and **Test-TargetResource** function properly.</span></span> <span data-ttu-id="30ac8-142">Almanız gereken adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="30ac8-142">Here are steps you should take:</span></span>
1.  <span data-ttu-id="30ac8-143">İstenilen durumda değil kaynak başlayın.</span><span class="sxs-lookup"><span data-stu-id="30ac8-143">Start with the resource not in the desired state.</span></span>
2.  <span data-ttu-id="30ac8-144">Kaynağınız ile çalışma yapılandırması</span><span class="sxs-lookup"><span data-stu-id="30ac8-144">Run configuration with your resource</span></span>
3.  <span data-ttu-id="30ac8-145">Doğrulama **Test DscConfiguration** True değerini döndürür</span><span class="sxs-lookup"><span data-stu-id="30ac8-145">Verify **Test-DscConfiguration** returns True</span></span>
4.  <span data-ttu-id="30ac8-146">İstenen durumdan yapılandırılmış öğeyi değiştirin</span><span class="sxs-lookup"><span data-stu-id="30ac8-146">Modify the configured item to be out of the desired state</span></span>
5.  <span data-ttu-id="30ac8-147">Doğrulama **Test DscConfiguration** döndürür yanlış kayıt defteri kaynak kullanımına daha somut bir örnek şudur:</span><span class="sxs-lookup"><span data-stu-id="30ac8-147">Verify **Test-DscConfiguration** returns false Here’s a more concrete example using Registry resource:</span></span>
1.  <span data-ttu-id="30ac8-148">Kayıt defteri anahtarı istenilen durumda değil başlayın</span><span class="sxs-lookup"><span data-stu-id="30ac8-148">Start with registry key not in the desired state</span></span>
2.  <span data-ttu-id="30ac8-149">Çalıştırma **başlangıç DscConfiguration** istenilen durumda koyun ve doğrulamak için bir yapılandırmayla geçirir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-149">Run **Start-DscConfiguration** with a configuration to put it in the desired state and verify it passes.</span></span>
3.  <span data-ttu-id="30ac8-150">Çalıştırma **Test DscConfiguration** ve doğru döndürdüğü doğrulayın</span><span class="sxs-lookup"><span data-stu-id="30ac8-150">Run **Test-DscConfiguration** and verify it returns true</span></span>
4.  <span data-ttu-id="30ac8-151">İstenilen durumda olmaması anahtarının değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="30ac8-151">Modify the value of the key so that it is not in the desired state</span></span>
5.  <span data-ttu-id="30ac8-152">Çalıştırma **Test DscConfiguration** ve false döndürdüğü doğrulayın</span><span class="sxs-lookup"><span data-stu-id="30ac8-152">Run **Test-DscConfiguration** and verify it returns false</span></span>
6.  <span data-ttu-id="30ac8-153">Get-TargetResource işlevselliği Get-DscConfiguration kullanılarak doğrulandı</span><span class="sxs-lookup"><span data-stu-id="30ac8-153">Get-TargetResource functionality was verified using Get-DscConfiguration</span></span>

<span data-ttu-id="30ac8-154">Get-TargetResource kaynağın geçerli durumuyla ayrıntılarını döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-154">Get-TargetResource should return details of the current state of the resource.</span></span> <span data-ttu-id="30ac8-155">Get-DscConfiguration yapılandırmayı uyguladıktan sonra arama ve çıkış doğru makinenin geçerli durumunu yansıtır doğrulama testi emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-155">Make sure to test it by calling Get-DscConfiguration after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="30ac8-156">Bu alandaki sorunları başlangıç DscConfiguration çağrılırken görünmez beri ayrı ayrı test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-156">It's important to test it separately, since any issues in this area won't appear when calling Start-DscConfiguration.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="30ac8-157">Çağrı **Get/Set/Test-TargetResource** doğrudan işlevleri</span><span class="sxs-lookup"><span data-stu-id="30ac8-157">Call **Get/Set/Test-TargetResource** functions directly</span></span> ##

<span data-ttu-id="30ac8-158">Test emin olun **Get/Set/Test-TargetResource** , kaynak doğrudan çağırma ve beklendiği gibi çalıştığını doğrulama uygulanan işlevler.</span><span class="sxs-lookup"><span data-stu-id="30ac8-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="30ac8-159">Uçtan uca kullanarak doğrulayın **başlangıç DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="30ac8-159">Verify End to End using **Start-DscConfiguration**</span></span> ##

<span data-ttu-id="30ac8-160">Sınama **Get/Set/Test-TargetResource** işlevlerini doğrudan çağırma tarafından önemlidir, ancak bu şekilde tüm sorunları bulunacaktır.</span><span class="sxs-lookup"><span data-stu-id="30ac8-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="30ac8-161">Testinizin kullanarak önemli bir bölümü durmalısınız **başlangıç DscConfiguration** veya çekme sunucusunda.</span><span class="sxs-lookup"><span data-stu-id="30ac8-161">You should focus significant part of your testing on using **Start-DscConfiguration** or the pull server.</span></span> <span data-ttu-id="30ac8-162">Aslında, kullanıcıların bu tür testleri önemini daha düşük olmayan şekilde kaynak nasıl kullanacağını budur.</span><span class="sxs-lookup"><span data-stu-id="30ac8-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span> <span data-ttu-id="30ac8-163">Olası sorunlar türleri:</span><span class="sxs-lookup"><span data-stu-id="30ac8-163">Possible types of issues:</span></span>
- <span data-ttu-id="30ac8-164">DSC Aracısı hizmeti olarak çalıştığından kimlik bilgisi/oturum farklı davranabilir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="30ac8-165">Burada herhangi bir özellik uçtan uca mutlaka test edin.</span><span class="sxs-lookup"><span data-stu-id="30ac8-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="30ac8-166">Hataları çıktı tarafından **başlangıç DscConfiguration** çağrılırken görüntülenen olanlar farklı olabilir **kümesi TargetResource** doğrudan işlev.</span><span class="sxs-lookup"><span data-stu-id="30ac8-166">Errors output by **Start-DscConfiguration** may be different than those displayed when calling the **Set-TargetResource** function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="30ac8-167">Test uyumluluk tüm DSC üzerinde desteklenen platformlar</span><span class="sxs-lookup"><span data-stu-id="30ac8-167">Test compatability on all DSC supported platforms</span></span> ##
<span data-ttu-id="30ac8-168">Kaynak tüm DSC desteklenen platformlarda çalışmalıdır (Windows Server 2008 R2 ve daha yeni).</span><span class="sxs-lookup"><span data-stu-id="30ac8-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="30ac8-169">En son WMF (Windows Management Framework) DSC en son sürümünü almak için işletim sistemine yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="30ac8-170">Kaynağınız bazı bu platformlar tarafından tasarım çalışmazsa, belirli bir hata iletisi döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="30ac8-171">Ayrıca, kaynak, aradığınız cmdlet'leri belirli makinede mevcut olup olmadığını denetler emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="30ac8-172">Windows Server 2012, çok sayıda bile WMF yüklü Windows Server 2008R2 üzerinde kullanılabilir değil yeni cmdlet'ler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span> 

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="30ac8-173">Windows istemcisinde (varsa) doğrulayın</span><span class="sxs-lookup"><span data-stu-id="30ac8-173">Verify on Windows Client (if applicable)</span></span> ##
<span data-ttu-id="30ac8-174">Yaygın bir test boşluk yalnızca, Windows server sürümlerinde kaynak doğruluyor.</span><span class="sxs-lookup"><span data-stu-id="30ac8-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="30ac8-175">Birçok kaynağa ayrıca istemci SKU'larında çalışması için tasarlanmış, sizin durumunuzda true ise, bu platformlarda test unutmayın şekilde.</span><span class="sxs-lookup"><span data-stu-id="30ac8-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span> 
## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="30ac8-176">Get-DSCResource kaynak listeleri</span><span class="sxs-lookup"><span data-stu-id="30ac8-176">Get-DSCResource lists the resource</span></span> ##
<span data-ttu-id="30ac8-177">Modül dağıttıktan sonra Get-DscResource çağırma diğerlerinin yanı sıra, kaynak sonucunda listelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-177">After deploying the module, calling Get-DscResource should list your resource among others as a result.</span></span> <span data-ttu-id="30ac8-178">Kaynağınız listede bulamazsanız, bu kaynak mevcut için o schema.mof dosya emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span> 
## <a name="resource-module-contains-examples"></a><span data-ttu-id="30ac8-179">Kaynak modülü örnekleri içerir</span><span class="sxs-lookup"><span data-stu-id="30ac8-179">Resource module contains examples</span></span> ##
<span data-ttu-id="30ac8-180">Başkalarının yardımcı olacak oluşturma nitelikli örnekler nasıl kullanılacağını anlayın.</span><span class="sxs-lookup"><span data-stu-id="30ac8-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="30ac8-181">Özellikle çok sayıda kullanıcı örnek kod belgeleri davran beri bu, çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-181">This is crucial, especially since many users treat sample code as documentation.</span></span> 
- <span data-ttu-id="30ac8-182">İlk olarak, en az – modülüyle eklenecek örnekler belirlemeniz gerekir, kaynak için en önemli kullanım örneklerini kapsamalıdır:</span><span class="sxs-lookup"><span data-stu-id="30ac8-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="30ac8-183">Temel uçtan uca örnek ideal olarak, modül bir uçtan uca senaryo için birlikte çalışmak için gereken çeşitli kaynaklar içeriyorsa, ilk olacaktır.</span><span class="sxs-lookup"><span data-stu-id="30ac8-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="30ac8-184">İlk örnek çok basit--nasıl kaynaklarınızı (örn. yeni bir VHD oluşturma) küçük yönetilebilir yığınlar kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="30ac8-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="30ac8-185">Sonraki örnekleri (örn. bir VM VM değiştirme VM kaldırma bir VHD'den oluşturma) Bu örnekleri oluşturmak ve gerekir (örn. bir VM ile dinamik bellek oluşturma) gelişmiş işlevselliği Göster</span><span class="sxs-lookup"><span data-stu-id="30ac8-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="30ac8-186">Örnek yapılandırmaları parametreli (tüm değerleri yapılandırmaya parametre olarak geçirilen ve sabit kodlanmış değerler olmalıdır):</span><span class="sxs-lookup"><span data-stu-id="30ac8-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
} 
```
- <span data-ttu-id="30ac8-187">Örnek komut dosyası sonunda gerçek değerlerle yapılandırma çağırmak nasıl (out açıklamalı) örneği dahil etmek için iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="30ac8-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span> <span data-ttu-id="30ac8-188">Örneğin, yukarıdaki yapılandırmada UserAgent belirtmek için en iyi yolu olduğunu mutlaka açık değil:</span><span class="sxs-lookup"><span data-stu-id="30ac8-188">For example, in the configuration above it isn't neccessarily obvious that the best way to specify UserAgent is:</span></span>

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
<span data-ttu-id="30ac8-189">Bu durumda bir yorum yapılandırmasının hedeflenen yürütme açıklık getirebilir:</span><span class="sxs-lookup"><span data-stu-id="30ac8-189">In which case a comment can clarify the intended execution of the configuration:</span></span>
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
- <span data-ttu-id="30ac8-190">Her örneğin ne yaptığını açıklayan kısa bir açıklama ve parametreleri anlamını yazma.</span><span class="sxs-lookup"><span data-stu-id="30ac8-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span> 
- <span data-ttu-id="30ac8-191">Örnekler, kaynak için en önemli senaryolarını kapsamak ve varsa eksik, hiçbir şey Tümünü Yürüt ve makine istenilen durumda put doğrulayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>  

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="30ac8-192">Hata iletileri anlamak ve kullanıcıların sorunlarını gidermenize yardımcı olmak kolay</span><span class="sxs-lookup"><span data-stu-id="30ac8-192">Error messages are easy to understand and help users solve problems</span></span> ##
<span data-ttu-id="30ac8-193">İyi hata iletileri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="30ac8-193">Good error messages should be:</span></span>
- <span data-ttu-id="30ac8-194">: Hata iletileri büyük sorun yoktur genellikle yoksa, bu nedenle bunlar bulunmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span> 
- <span data-ttu-id="30ac8-195">Kolay anlaşılır: İnsan okunabilir, Hayır belirsiz hata kodları</span><span class="sxs-lookup"><span data-stu-id="30ac8-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="30ac8-196">Kesin: tam olarak sorunun ne olduğunu açıklar</span><span class="sxs-lookup"><span data-stu-id="30ac8-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="30ac8-197">Yapıcı: Öneri sorunu gidermeye yönelik</span><span class="sxs-lookup"><span data-stu-id="30ac8-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="30ac8-198">Yumuşak: nedenlerle kullanıcı ya da bunları eşitleyerek hatalı yapma uçtan uca senaryolarda hataları doğrulayın emin yok (kullanarak **başlangıç DscConfiguration**), kaynak işlevlerini doğrudan çalıştırırken döndürülen olanlardan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-198">Polite: Don’t blame user or make them feel bad Make sure you verify errors in End to End scenarios (using **Start-DscConfiguration**), because they may differ from those returned when running resource functions directly.</span></span> 

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="30ac8-199">Günlük iletilerini kolay anlaşılır ve bilgilendirici (dahil – ayrıntılı, – hata ayıklama hem de ETW günlükleri)</span><span class="sxs-lookup"><span data-stu-id="30ac8-199">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span> ##
<span data-ttu-id="30ac8-200">Kaynak tarafından yüzdelik günlükleri anlama ve kullanıcıya değeri sağlamak kolay olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-200">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="30ac8-201">Kaynakları kullanıcı için yararlı olabilecek tüm bilgileri çıkış, ancak daha fazla günlükleri değil her zaman daha iyi.</span><span class="sxs-lookup"><span data-stu-id="30ac8-201">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="30ac8-202">Artıklık önlemek ve gerekir içermeyen veri çıktısı ek değer sağlamanız – birisi aradıklarını bulmak için günlük girişlerini yüzlerce Git yapmayın.</span><span class="sxs-lookup"><span data-stu-id="30ac8-202">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="30ac8-203">Elbette, hiçbir günlük değil Bu sorun için kabul edilebilir bir çözüm ya da.</span><span class="sxs-lookup"><span data-stu-id="30ac8-203">Of course, no logs is not an acceptable solution for this problem either.</span></span> 

<span data-ttu-id="30ac8-204">Test edilirken de ayrıntılı çözümleyebilir ve hata ayıklama günlüklerini (çalıştırarak **başlangıç DscConfiguration** ile – ayrıntılı ve – anahtarları uygun şekilde hata ayıklama), yanı ETW günlükleri olarak.</span><span class="sxs-lookup"><span data-stu-id="30ac8-204">When testing, you should also analyze verbose and debug logs (by running **Start-DscConfiguration** with –verbose and –debug switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="30ac8-205">DSC ETW günlükleri görmek için Olay Görüntüleyici'ye gidin ve şu klasörü açın: uygulamaları ve Hizmetleri - Microsoft - Windows - istenen durum yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="30ac8-205">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="30ac8-206">Varsayılan olarak var. işletimsel kanal olabilir, ancak analitik etkinleştirdiğinizden emin olun ve kanallar yapılandırma çalıştırmadan önce hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="30ac8-206">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span> <span data-ttu-id="30ac8-207">Analitik/Debug kanalları etkinleştirmek için aşağıdaki komut dosyası çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30ac8-207">To enable Analytic/Debug channels, you can execute script below:</span></span>
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug" 
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}     
Invoke-Expression $commandToExecute 
```
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="30ac8-208">Kaynak uygulama sabit kodlanmış yolları içermiyor</span><span class="sxs-lookup"><span data-stu-id="30ac8-208">Resource implementation does not contain hardcoded paths</span></span> ##
<span data-ttu-id="30ac8-209">Özellikle bu bunlar dil olduğunu varsayarsak kaynak uygulamasında hiçbir sabit kodlanmış yol olmadığından emin olun (en-us), veya kullanılabilir sistem değişkenleri olduğunda.</span><span class="sxs-lookup"><span data-stu-id="30ac8-209">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="30ac8-210">Kaynağınız belirli yollar erişmesi gerekirse, ortam değişkenleri diğer makinelerde farklı olabileceği yerine cmdlet'e kod yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="30ac8-210">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="30ac8-211">Örnek:</span><span class="sxs-lookup"><span data-stu-id="30ac8-211">Example:</span></span>

<span data-ttu-id="30ac8-212">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="30ac8-212">Instead of:</span></span>
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
<span data-ttu-id="30ac8-213">Şunu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30ac8-213">You can write:</span></span>
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="30ac8-214">Kaynak uygulaması kullanıcı bilgisi içermiyor</span><span class="sxs-lookup"><span data-stu-id="30ac8-214">Resource implementation does not contain user information</span></span> ##
<span data-ttu-id="30ac8-215">E-posta adlarını, hesap bilgilerini ya kodda kişilerin adlarını olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-215">Make sure there are no email names, account information, or names of people in the code.</span></span>
## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="30ac8-216">Kaynağın geçerli/geçersiz kimlik bilgileri ile test edilmiştir</span><span class="sxs-lookup"><span data-stu-id="30ac8-216">Resource was tested with valid/invalid credentials</span></span> ##
<span data-ttu-id="30ac8-217">Kaynağınız parametre olarak bir kimlik bilgisi sürerse:</span><span class="sxs-lookup"><span data-stu-id="30ac8-217">If your resource takes a credential as parameter:</span></span>
- <span data-ttu-id="30ac8-218">Yerel Sistem (veya uzak kaynaklar için bilgisayar hesabı) erişimi olmadığında kaynak çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="30ac8-218">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="30ac8-219">Belirtilen kimlik bilgileriyle kaynak works Al ayarlayın ve sınayın doğrulayın</span><span class="sxs-lookup"><span data-stu-id="30ac8-219">Verify the resource works with a credential specified for Get, Set and Test</span></span> 
- <span data-ttu-id="30ac8-220">Kaynağınız paylaşımları erişirse, gibi desteklemeniz gereken tüm çeşitleri test edin:</span><span class="sxs-lookup"><span data-stu-id="30ac8-220">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="30ac8-221">Standart windows paylaşımları.</span><span class="sxs-lookup"><span data-stu-id="30ac8-221">Standard windows shares.</span></span>
  - <span data-ttu-id="30ac8-222">DFS paylaşımları.</span><span class="sxs-lookup"><span data-stu-id="30ac8-222">DFS shares.</span></span>
  - <span data-ttu-id="30ac8-223">SAMBA paylaşımları (Linux desteklemek istiyorsanız,.)</span><span class="sxs-lookup"><span data-stu-id="30ac8-223">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="30ac8-224">Kaynak etkileşimli giriş gerektirmez</span><span class="sxs-lookup"><span data-stu-id="30ac8-224">Resource does not require interactive input</span></span> ##
<span data-ttu-id="30ac8-225">**Get/Set/Test-TargetResource** işlevleri otomatik olarak yürütülüp ve kullanıcının herhangi bir yürütme aşamasında giriş için beklemesi gereken değil (örneğin kullanılamaz **Get-Credential** bu işlevler içinde).</span><span class="sxs-lookup"><span data-stu-id="30ac8-225">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use **Get-Credential** inside these functions).</span></span> <span data-ttu-id="30ac8-226">Kullanıcının giriş sağlamak ihtiyacınız varsa, bu yapılandırmaya parametre olarak derleme aşamasında geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="30ac8-226">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span> 
## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="30ac8-227">Kaynak işlevselliği baştan sona test edilmiştir</span><span class="sxs-lookup"><span data-stu-id="30ac8-227">Resource functionality was thoroughly tested</span></span> ##
<span data-ttu-id="30ac8-228">Bu denetim, sınanacak önemlidir ve/veya genellikle eksik öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-228">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="30ac8-229">Testleri, test ve burada belirtilmeyen kaynak belirli olacağı çoğunlukla işlevsel olanları demet olacaktır.</span><span class="sxs-lookup"><span data-stu-id="30ac8-229">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="30ac8-230">Negatif test çalışmaları hakkında unutmayın.</span><span class="sxs-lookup"><span data-stu-id="30ac8-230">Don’t forget about negative test cases.</span></span> 
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="30ac8-231">Açısından en iyisi: kaynak modülü ResourceDesignerTests.ps1 betik klasörle testleri içerir</span><span class="sxs-lookup"><span data-stu-id="30ac8-231">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span> ##
<span data-ttu-id="30ac8-232">İçinde kaynak modül klasörü "testleri" oluşturun, ResourceDesignerTests.ps1 dosyası oluşturun ve kullanarak testleri eklemek için iyi bir uygulamadır **Test xDscResource** ve **Test xDscSchema** belirtilen tüm kaynakların ilişkin Modül.</span><span class="sxs-lookup"><span data-stu-id="30ac8-232">It’s a good practice to create folder “Tests” inside resource module, create ResourceDesignerTests.ps1 file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span> <span data-ttu-id="30ac8-233">Bu şekilde tüm kaynakların bir sağlamlık denetleyin yayımlanmadan önce belirtilen modülleri ve şemaları hızla doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30ac8-233">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="30ac8-234">XRemoteFile için ResourceTests.ps1 kadar basit görünebilir:</span><span class="sxs-lookup"><span data-stu-id="30ac8-234">For xRemoteFile, ResourceTests.ps1 could look as simple as:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="30ac8-235">Açısından en iyisi: kaynak klasörünü içeren kaynak Tasarımcı betik şema ## oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="30ac8-235">Best practice: Resource folder contains resource designer script for generating schema##</span></span>
<span data-ttu-id="30ac8-236">Her bir kaynağın kaynak mof şeması oluşturan bir kaynak Tasarımcı betik içermelidir.</span><span class="sxs-lookup"><span data-stu-id="30ac8-236">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="30ac8-237">Bu dosya yerleştirilmelidir <ResourceName>\ResourceDesignerScripts ve Generate adlandırılması<ResourceName>xRemoteFile kaynak Schema.ps1 için bu dosyayı GenerateXRemoteFileSchema.ps1 çağrılır ve içerir:</span><span class="sxs-lookup"><span data-stu-id="30ac8-237">This file should be placed in <ResourceName>\ResourceDesignerScripts and be named Generate<ResourceName>Schema.ps1 For xRemoteFile resource this file would be called GenerateXRemoteFileSchema.ps1 and contain:</span></span>
```powershell 
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.' 
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile 
```
## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="30ac8-238">Açısından en iyisi: kaynak - whatIf destekler</span><span class="sxs-lookup"><span data-stu-id="30ac8-238">Best practice: Resource supports -whatif</span></span> ##
<span data-ttu-id="30ac8-239">Kaynağınız "tehlikeli" işlemleri çalışıyorsa, - whatIf işlevselliği uygulamak için iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="30ac8-239">If your resource is performing “dangerous” operations, it’s a good practice to implement -whatif functionality.</span></span> <span data-ttu-id="30ac8-240">Bunu yaptıktan sonra whatIf çıkış doğru whatIf anahtarı olmadan komut yürütülürse olacağını işlemleri açıklayan emin olun.</span><span class="sxs-lookup"><span data-stu-id="30ac8-240">After it’s done, make sure that whatif output correctly describes operations which would happen if command was executed without whatif switch.</span></span>
<span data-ttu-id="30ac8-241">Ayrıca, operations yürütülmez doğrulayın (düğümün durumuna değişiklik yapılmaz) – whatIf anahtar olduğunda mevcut.</span><span class="sxs-lookup"><span data-stu-id="30ac8-241">Also, verify that operations does not execute (no changes to the node’s state are made) when –whatif switch is present.</span></span> <span data-ttu-id="30ac8-242">Örneğin, dosya kaynağı test ettiğiniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="30ac8-242">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="30ac8-243">"Test" dosyası "sınama.txt" içeriğiyle oluşturan basit yapılandırma aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="30ac8-243">Below is simple configuration which creates file “test.txt” with contents “test”:</span></span>
```powershell
configuration config
{
    node localhost 
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config 
```
<span data-ttu-id="30ac8-244">Derleme ve yapılandırma – whatIf anahtarıyla yürütmek, çıktı bize biz yapılandırma çalıştırdığınızda tam olarak ne olacağını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="30ac8-244">If we compile and then execute the configuration with the –whatif switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="30ac8-245">Yapılandırma ancak yürütülmedi (sınama.txt dosyası oluşturulmadı).</span><span class="sxs-lookup"><span data-stu-id="30ac8-245">The configuration itself however was not executed (test.txt file was not created).</span></span>
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="30ac8-246">Bu liste geniş kapsamlı değildir, ancak tasarlama, geliştirme ve test etme DSC kaynakları hatayla karşılaştı birçok önemli sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30ac8-246">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>

