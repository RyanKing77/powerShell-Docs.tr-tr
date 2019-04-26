---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Kaynak yazma denetim listesi
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076591"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="da4cc-103">Kaynak yazma denetim listesi</span><span class="sxs-lookup"><span data-stu-id="da4cc-103">Resource authoring checklist</span></span>

<span data-ttu-id="da4cc-104">Bu denetim yeni bir DSC kaynağı yazma en iyi bir listedir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="da4cc-105">Kaynak modülü .psd1 dosya ve her kaynak için schema.mof içerir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="da4cc-106">Kaynağınızı doğru yapıya sahiptir ve tüm gerekli dosyaları içeren denetleyin.</span><span class="sxs-lookup"><span data-stu-id="da4cc-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="da4cc-107">Her kaynak modülü .psd1 dosya içermelidir ve her bileşik olmayan kaynak schema.mof dosyanız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="da4cc-108">Şema içermeyen kaynaklar tarafından listelenmez `Get-DscResource` ve kullanıcıların ISE'de modüller karşı kod yazarken IntelliSense kullanmanız mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="da4cc-109">Parçası olan xRemoteFile kaynak dizin yapısı, [xPSDesiredStateConfiguration resource Modülü](https://github.com/PowerShell/xPSDesiredStateConfiguration), şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="da4cc-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

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

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="da4cc-110">Kaynak ve şema doğru</span><span class="sxs-lookup"><span data-stu-id="da4cc-110">Resource and schema are correct</span></span>

<span data-ttu-id="da4cc-111">Kaynak şemayı doğrulayın (\*. schema.mof) dosyası.</span><span class="sxs-lookup"><span data-stu-id="da4cc-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="da4cc-112">Kullanabileceğiniz [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) geliştirip test şemanızı yardımcı olmak için.</span><span class="sxs-lookup"><span data-stu-id="da4cc-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="da4cc-113">Emin olun:</span><span class="sxs-lookup"><span data-stu-id="da4cc-113">Make sure that:</span></span>

- <span data-ttu-id="da4cc-114">Özellik türleri doğru (dize, sayısal değerleri kabul etmek için özellikleri örn kullanmayın, bunun yerine UInt32 ya da diğer sayısal türleri kullanmalısınız)</span><span class="sxs-lookup"><span data-stu-id="da4cc-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="da4cc-115">Özellik öznitelikleri doğru olarak belirtilir: ([anahtarı] [gerekli], [yazma], [okuma])</span><span class="sxs-lookup"><span data-stu-id="da4cc-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="da4cc-116">Şema en az bir parametresi [anahtar] olarak işaretlenmesi gerekir</span><span class="sxs-lookup"><span data-stu-id="da4cc-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="da4cc-117">[özelliği olmayan bir arada herhangi biri ile birlikte okuyun]: [gerekli], [key] [yazma]</span><span class="sxs-lookup"><span data-stu-id="da4cc-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="da4cc-118">Birden çok niteleyicileri dışında [oku] belirtilirse, [key] öncelik kazanır</span><span class="sxs-lookup"><span data-stu-id="da4cc-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="da4cc-119">Varsa [yazma] ve [gerekli] belirtilen sonra [gerekli] önceliğe</span><span class="sxs-lookup"><span data-stu-id="da4cc-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="da4cc-120">ValueMap belirtilen örnek uygun olduğunda:</span><span class="sxs-lookup"><span data-stu-id="da4cc-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="da4cc-121">Kolay ad belirtilir ve DSC adlandırma kurallarına onaylar</span><span class="sxs-lookup"><span data-stu-id="da4cc-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="da4cc-122">Örnek: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="da4cc-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="da4cc-123">Her alan anlamlı bir açıklama bulunur.</span><span class="sxs-lookup"><span data-stu-id="da4cc-123">Every field has meaningful description.</span></span> <span data-ttu-id="da4cc-124">PowerShell GitHub deposunu iyi örnekler vardır [. schema.mof xRemoteFile için](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="da4cc-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="da4cc-125">Ayrıca, kullanmanız gereken **Test xDscResource** ve **Test xDscSchema** cmdlet'lerinden [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) kaynak ve şema otomatik olarak doğrulamak için:</span><span class="sxs-lookup"><span data-stu-id="da4cc-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="da4cc-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="da4cc-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="da4cc-127">Kaynak hatasız yükler.</span><span class="sxs-lookup"><span data-stu-id="da4cc-127">Resource loads without errors</span></span>

<span data-ttu-id="da4cc-128">Kaynak modülü başarıyla yüklenmiş olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="da4cc-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="da4cc-129">Bu el ile çalıştırarak ulaşılabilecek `Import-Module <resource_module> -force` ve herhangi bir hata oluştuğunu onayladıktan veya göre test Otomasyonu yazma.</span><span class="sxs-lookup"><span data-stu-id="da4cc-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="da4cc-130">İkinci olması durumunda, bu yapı, test çalışmasında izleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da4cc-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="da4cc-131">Kaynak etkilidir pozitif durumda</span><span class="sxs-lookup"><span data-stu-id="da4cc-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="da4cc-132">DSC kaynakları temel özelliklerini Eşkuvvetlilik biridir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="da4cc-133">Bu, birden çok kez bu kaynağı içeren bir DSC yapılandırması uygulama her zaman aynı sonucu elde edecek, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="da4cc-134">Örneğin aşağıdaki dosya kaynağı içeren bir yapılandırma oluşturacağız:</span><span class="sxs-lookup"><span data-stu-id="da4cc-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="da4cc-135">İlk kez uyguladıktan sonra dosya test.txt gözükeceğini `C:\test` klasör.</span><span class="sxs-lookup"><span data-stu-id="da4cc-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="da4cc-136">Ancak, aynı yapılandırmayı sonraki çalışmaları makinenin durumunu değiştirmemesi gerekir (örneğin hiçbir kopyalarını `test.txt` dosya oluşturulmalıdır).</span><span class="sxs-lookup"><span data-stu-id="da4cc-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="da4cc-137">Bir kaynağa tekrar tekrar çağırmak bir kez etkili olduğundan emin olmak için `Set-TargetResource` kaynak doğrudan test veya çağrı `Start-DscConfiguration` birden çok kez baştan sona test yaparken.</span><span class="sxs-lookup"><span data-stu-id="da4cc-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="da4cc-138">Her sonrasında çalıştırma sonucu aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="da4cc-139">Test kullanıcı değişiklik senaryosu</span><span class="sxs-lookup"><span data-stu-id="da4cc-139">Test user modification scenario</span></span>

<span data-ttu-id="da4cc-140">Makinenin durumunu değiştirme ve DSC artırarak algoritmanın yeniden çalıştırılması doğrulayabilirsiniz `Set-TargetResource` ve `Test-TargetResource` düzgün.</span><span class="sxs-lookup"><span data-stu-id="da4cc-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="da4cc-141">Uygulamanız gereken adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="da4cc-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="da4cc-142">İstenen durumda değil kaynakla başlayın.</span><span class="sxs-lookup"><span data-stu-id="da4cc-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="da4cc-143">Kaynağınız ile çalıştırma yapılandırma</span><span class="sxs-lookup"><span data-stu-id="da4cc-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="da4cc-144">Doğrulama `Test-DscConfiguration` True döndürür</span><span class="sxs-lookup"><span data-stu-id="da4cc-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="da4cc-145">İstenen durum dışında olacak şekilde yapılandırılmış öğesini değiştirin</span><span class="sxs-lookup"><span data-stu-id="da4cc-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="da4cc-146">Doğrulama `Test-DscConfiguration` false döndürür</span><span class="sxs-lookup"><span data-stu-id="da4cc-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="da4cc-147">Registry kaynağı kullanarak daha somut bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="da4cc-147">Here’s a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="da4cc-148">Kayıt defteri anahtarı istenen durumda değil başlayın</span><span class="sxs-lookup"><span data-stu-id="da4cc-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="da4cc-149">Çalıştırma `Start-DscConfiguration` istenen durumda yerleştirin ve doğrulamak için bir yapılandırmayla geçirir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="da4cc-150">Çalıştırma `Test-DscConfiguration` ve doğrulayın, true döndürür</span><span class="sxs-lookup"><span data-stu-id="da4cc-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="da4cc-151">İstenen durumda değil anahtarının değerini değiştirin</span><span class="sxs-lookup"><span data-stu-id="da4cc-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="da4cc-152">Çalıştırma `Test-DscConfiguration` ve false döndürür doğrulayın</span><span class="sxs-lookup"><span data-stu-id="da4cc-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="da4cc-153">`Get-TargetResource` işlevleri kullanılarak doğrulandı `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="da4cc-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="da4cc-154">`Get-TargetResource` Kaynağın geçerli durumu ayrıntıları döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="da4cc-155">Çağırarak sınayın `Get-DscConfiguration` sonra yapılandırmayı uygulamak ve çıktısını almak için doğru Bu doğrulama makinenin geçerli durumunu yansıtır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="da4cc-156">Bu alandaki tüm sorunları çağırırken görünmez olduğundan ayrı ayrı test etmek önemlidir `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="da4cc-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="da4cc-157">Çağrı **Get/Set/Test-TargetResource** doğrudan işlevleri</span><span class="sxs-lookup"><span data-stu-id="da4cc-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="da4cc-158">Test emin **Get/Set/Test-TargetResource** kaynağınızda doğrudan çağırmak ve beklendiği gibi çalıştığını doğrulama uygulanan işlevleri.</span><span class="sxs-lookup"><span data-stu-id="da4cc-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="da4cc-159">Uçtan uca kullanarak doğrulama **Başlat-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="da4cc-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="da4cc-160">Test **Get/Set/Test-TargetResource** işlevlerini doğrudan çağırma tarafından önemlidir, ancak bu şekilde tüm sorunları bulunacaktır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="da4cc-161">Testinizin kullanma ile ilgili önemli bir bölümü durmalısınız `Start-DscConfiguration` veya çekme sunucusu.</span><span class="sxs-lookup"><span data-stu-id="da4cc-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="da4cc-162">Aslında, bu kullanıcılar bu tür testler önemini düşük gösterdiğini olmayan şekilde kaynak nasıl kullanacağınız değerdir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="da4cc-163">Olası sorunları türleri:</span><span class="sxs-lookup"><span data-stu-id="da4cc-163">Possible types of issues:</span></span>

- <span data-ttu-id="da4cc-164">DSC aracı bir hizmet olarak çalıştığı için kimlik bilgisi/oturum farklı davranabilir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="da4cc-165">Burada herhangi bir özellik baştan sona test etmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="da4cc-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="da4cc-166">Hataları çıktı tarafından `Start-DscConfiguration` çağırırken görüntülenen alınanlardan farklı olabilir `Set-TargetResource` doğrudan işlev.</span><span class="sxs-lookup"><span data-stu-id="da4cc-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="da4cc-167">Test uyumluluk tüm DSC üzerinde desteklenen platformlar</span><span class="sxs-lookup"><span data-stu-id="da4cc-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="da4cc-168">Kaynak DSC desteklenen tüm platformlarda iş (Windows Server 2008 R2 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="da4cc-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="da4cc-169">DSC en son sürümünü almak için işletim sisteminize en son WMF (Windows Management Framework) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="da4cc-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="da4cc-170">Kaynağınızı bu platformları bazılarında tasarım gereği çalışmazsa, belirli bir hata iletisi döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="da4cc-171">Ayrıca kaynağınızın aradığınız cmdlet'leri belirli makinede mevcut olup olmadığını denetler emin olun.</span><span class="sxs-lookup"><span data-stu-id="da4cc-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="da4cc-172">Windows Server 2012, çok sayıda bile WMF yüklü Windows Server 2008R2 üzerinde mevcut olmayan yeni cmdlet'ler eklendi.</span><span class="sxs-lookup"><span data-stu-id="da4cc-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="da4cc-173">(Eğer varsa) Windows istemcide doğrulayın</span><span class="sxs-lookup"><span data-stu-id="da4cc-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="da4cc-174">Çok yaygın bir test boşluk kaynağın yalnızca Windows server sürümlerini doğruluyor.</span><span class="sxs-lookup"><span data-stu-id="da4cc-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="da4cc-175">Çok sayıda kaynağı da istemci SKU'ları üzerinde çalışacak şekilde tasarlanmıştır, sizin durumunuzda true ise, bu platformlarda test unutmamak.</span><span class="sxs-lookup"><span data-stu-id="da4cc-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="da4cc-176">Get-DSCResource kaynak listeler</span><span class="sxs-lookup"><span data-stu-id="da4cc-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="da4cc-177">Modül dağıttıktan sonra çağırma `Get-DscResource` kaynağınızı diğerlerinin yanı sıra sonucunda listelemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="da4cc-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="da4cc-178">Kaynağınızı listede bulamazsanız, bu kaynağın mevcut için schema.mof osyanın emin olun.</span><span class="sxs-lookup"><span data-stu-id="da4cc-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="da4cc-179">Kaynak modülü örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-179">Resource module contains examples</span></span>

<span data-ttu-id="da4cc-180">Başkalarının yardımcı olacak oluşturma kalite örnekleri nasıl kullanılacağını anlamak.</span><span class="sxs-lookup"><span data-stu-id="da4cc-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="da4cc-181">Özellikle çok sayıda kullanıcı belgeleri örnek kod işle olduğundan bu, çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="da4cc-182">İlk olarak, en azından – modülüyle dahil edilecek örnekler belirlemelisiniz, kaynağınız için en önemli kullanım örneklerini kapsamalıdır:</span><span class="sxs-lookup"><span data-stu-id="da4cc-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="da4cc-183">Temel uçtan uca örnek ideal olarak, modül bir uçtan uca senaryo için birlikte çalışmak için gereken çeşitli kaynaklar varsa, ilk olacaktır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="da4cc-184">İlk örnek çok basit--nasıl (örneğin yeni bir VHD oluşturma) küçük yönetilebilir yığınlar kaynaklarınızı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="da4cc-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="da4cc-185">Sonraki örneklerde (örneğin VM VM değiştirme, kaldırma, bir VHD'den VM oluşturma) Bu örnekleri oluşturmak ve gelişmiş işlevleri (örneğin dinamik bellek ile VM oluşturma) göster</span><span class="sxs-lookup"><span data-stu-id="da4cc-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="da4cc-186">Örnek yapılandırma parametreli (tüm değerler için yapılandırma parametreleri olarak geçirilmelidir ve sabit kodlanmış değer olması gerekir):</span><span class="sxs-lookup"><span data-stu-id="da4cc-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

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

- <span data-ttu-id="da4cc-187">Yapılandırmanın sonunda örnek betik, gerçek değerlerle çağırmak nasıl (out açıklamalı) örneği eklemek iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="da4cc-188">Örneğin, yukarıdaki yapılandırmada UserAgent belirtmek için en iyi yolu olduğunu mutlaka belirgin değildir:</span><span class="sxs-lookup"><span data-stu-id="da4cc-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="da4cc-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Bu durumda bir açıklama yapılandırmasının hedeflenen yürütme açıklık getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da4cc-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="da4cc-190">Her örneğin ne yaptığını açıklayan kısa bir açıklama ve parametreleri anlamını yazın.</span><span class="sxs-lookup"><span data-stu-id="da4cc-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="da4cc-191">Örnekler kaynağınızın birçok önemli senaryoyu kapsar ve şey eksik, yoksa tüm yürütün ve istenen durumda makine yerleştirebilir doğrulayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="da4cc-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="da4cc-192">Anlama ve kullanıcılar sorunları çözmesine yardımcı olmak hata iletileri kolaydır</span><span class="sxs-lookup"><span data-stu-id="da4cc-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="da4cc-193">İyi hata iletileri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="da4cc-193">Good error messages should be:</span></span>

- <span data-ttu-id="da4cc-194">Vardır: En büyük hata iletileri sorundur genellikle yoksa, bu nedenle bunlar olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="da4cc-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="da4cc-195">Kolay anlaşılır: İnsan tarafından okunabilir, Hayır belirsiz hata kodları</span><span class="sxs-lookup"><span data-stu-id="da4cc-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="da4cc-196">Kesin: Tam olarak sorunun ne olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="da4cc-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="da4cc-197">Yapıcı: Öneri sorunun nasıl çözüleceğini</span><span class="sxs-lookup"><span data-stu-id="da4cc-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="da4cc-198">Yumuşak: Kullanıcı sorumlu veya onları hatalı düşünüyorsanız kullanmayın</span><span class="sxs-lookup"><span data-stu-id="da4cc-198">Polite: Don’t blame user or make them feel bad</span></span>

<span data-ttu-id="da4cc-199">Uçtan uca senaryolar Hataları Doğrula emin olun (kullanarak `Start-DscConfiguration`), kaynak işlevleri doğrudan çalıştırılırken döndürülen olanlardan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="da4cc-200">Kolay anlaşılır ve bilgilendirici günlük iletisi (dahil-verbose,-hata ayıklama ve ETW günlükleri)</span><span class="sxs-lookup"><span data-stu-id="da4cc-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="da4cc-201">Kaynak tarafından yüzdelik günlükleri anlama ve kullanıcıya değeri sağlamak kolay olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="da4cc-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="da4cc-202">Kaynakları, kullanıcıya yardımcı olabilecek tüm bilgileri oluşturmalıdır, ancak daha fazla günlükleri değil her zaman daha iyi.</span><span class="sxs-lookup"><span data-stu-id="da4cc-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="da4cc-203">Yedeklilik önlemek ve gerekir içermeyen veri çıktısı ek değer sağlayın: birisi aradıklarını bulmak amacıyla günlük girişlerini yüzlerce Git yapmayın.</span><span class="sxs-lookup"><span data-stu-id="da4cc-203">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="da4cc-204">Elbette, günlük değil Bu sorun için kabul edilebilir bir çözüm ya da.</span><span class="sxs-lookup"><span data-stu-id="da4cc-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="da4cc-205">Test ederken de ayrıntılı analiz etmek ve hata ayıklama günlüklerini (çalıştırarak `Start-DscConfiguration` ile `–Verbose` ve `–Debug` uygun şekilde geçer) da ETW günlükleri olarak.</span><span class="sxs-lookup"><span data-stu-id="da4cc-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="da4cc-206">DSC ETW günlükleri görmek için Olay Görüntüleyicisi'ne gidin ve şu klasörü açın: Uygulamaları ve Hizmetleri - Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="da4cc-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="da4cc-207">Varsayılan olarak yok işlevsel kanal olabilir, ancak analitik etkinleştirdiğinizden emin olun ve yapılandırmayı çalıştırmadan önce kanalları hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="da4cc-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="da4cc-208">Analitik/Debug kanalları etkinleştirmek için aşağıdaki betiği yürütebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da4cc-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="da4cc-209">Kaynak uygulama, sabit kodlanmış yollar içermiyor</span><span class="sxs-lookup"><span data-stu-id="da4cc-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="da4cc-210">Özellikle dil varsayarsanız kaynak uygulamasında, sabit kodlanmış yol olmadığından emin olun (en-us), veya kullanılabilir sistem değişkenlerini olduğunda.</span><span class="sxs-lookup"><span data-stu-id="da4cc-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="da4cc-211">Kaynağınızı belirli yollar erişmeniz gerekiyorsa, diğer makinelere değişebilir gibi ortam değişkenleri yerine runbook'a kod yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="da4cc-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="da4cc-212">Örnek:</span><span class="sxs-lookup"><span data-stu-id="da4cc-212">Example:</span></span>

<span data-ttu-id="da4cc-213">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="da4cc-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="da4cc-214">şunu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da4cc-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="da4cc-215">Kaynak uygulaması kullanıcı bilgisi içermiyor</span><span class="sxs-lookup"><span data-stu-id="da4cc-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="da4cc-216">E-posta adları, hesap bilgileri veya kod kişilerin adları yok emin olun.</span><span class="sxs-lookup"><span data-stu-id="da4cc-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="da4cc-217">Kaynak geçerli/geçersiz kimlik bilgileri ile test edilmiştir</span><span class="sxs-lookup"><span data-stu-id="da4cc-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="da4cc-218">Kaynağınızı parametre olarak bir kimlik bilgisi sürerse:</span><span class="sxs-lookup"><span data-stu-id="da4cc-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="da4cc-219">Yerel Sistem (veya uzak kaynaklara yönelik bilgisayar hesabının) erişimi olmadığında, kaynak çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="da4cc-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="da4cc-220">Bir kimlik bilgisi için belirtilen kaynak çalışır Al Ayarla ve Test doğrulayın</span><span class="sxs-lookup"><span data-stu-id="da4cc-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="da4cc-221">Kaynak paylaşımları erişirse, desteği, aşağıdaki gibi ihtiyacınız olan tüm çeşitleri test edin:</span><span class="sxs-lookup"><span data-stu-id="da4cc-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="da4cc-222">Standart windows paylaşımları.</span><span class="sxs-lookup"><span data-stu-id="da4cc-222">Standard windows shares.</span></span>
  - <span data-ttu-id="da4cc-223">DFS paylaşımları.</span><span class="sxs-lookup"><span data-stu-id="da4cc-223">DFS shares.</span></span>
  - <span data-ttu-id="da4cc-224">SAMBA paylaşımları (Linux desteklemek isterseniz.)</span><span class="sxs-lookup"><span data-stu-id="da4cc-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="da4cc-225">Kaynak etkileşimli giriş gerektirmez</span><span class="sxs-lookup"><span data-stu-id="da4cc-225">Resource does not require interactive input</span></span>

<span data-ttu-id="da4cc-226">**Get/Set/Test-TargetResource** işlevleri otomatik olarak yürütülüp ve kullanıcının herhangi bir yürütme aşamasında girişinin için beklemeyip gerekir (örneğin kullanmamalısınız `Get-Credential` bu işlevler içinde).</span><span class="sxs-lookup"><span data-stu-id="da4cc-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="da4cc-227">Kullanıcının giriş sağlamanız gerekiyorsa, yapılandırma için parametre olarak derleme aşaması sırasında geçirdiğiniz.</span><span class="sxs-lookup"><span data-stu-id="da4cc-227">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="da4cc-228">Kaynak işlevselliği kapsamlı olarak test edildi</span><span class="sxs-lookup"><span data-stu-id="da4cc-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="da4cc-229">Bu denetim, test edilecek önemlidir ve/veya genellikle eksik öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="da4cc-230">Testler, test ve burada belirtilmeyen kaynak belirli olacağı çoğunlukla işlevsel olanları sürü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="da4cc-231">Negatif test çalışmaları hakkında unutmayın.</span><span class="sxs-lookup"><span data-stu-id="da4cc-231">Don’t forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="da4cc-232">En iyi yöntem: Testleri klasörde ResourceDesignerTests.ps1 betiğiyle Resource Modülü</span><span class="sxs-lookup"><span data-stu-id="da4cc-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="da4cc-233">Kaynak modülü içinde "testleri" klasör oluşturma, için iyi bir uygulamadır `ResourceDesignerTests.ps1` kullanarak testleri ekleyin ve dosya **Test xDscResource** ve **Test xDscSchema** içinde tüm kaynaklar için verilen modülü.</span><span class="sxs-lookup"><span data-stu-id="da4cc-233">It’s a good practice to create folder “Tests” inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="da4cc-234">Bu şekilde tüm kaynakların bir sağlamlık denetleyin yayımlanmadan önce belirtilen modülleri ve şemaları hızlı bir şekilde doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da4cc-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="da4cc-235">XRemoteFile için `ResourceTests.ps1` kadar basit görünebilir:</span><span class="sxs-lookup"><span data-stu-id="da4cc-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="da4cc-236">En iyi yöntem: Kaynak klasör şema oluşturmak için kaynak Tasarımcı betiği içerir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="da4cc-237">Her kaynak bir kaynağın mof şema oluşturur bir kaynak Tasarımcı betiği içermelidir.</span><span class="sxs-lookup"><span data-stu-id="da4cc-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="da4cc-238">Bu dosya yerleştirilmelidir `<ResourceName>\ResourceDesignerScripts` ve Oluştur adlandırılması `<ResourceName>Schema.ps1` xRemoteFile kaynağı için bu dosyayı çağırılan `GenerateXRemoteFileSchema.ps1` ve içerir:</span><span class="sxs-lookup"><span data-stu-id="da4cc-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

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

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="da4cc-239">En iyi yöntem: Kaynak - WhatIf destekler</span><span class="sxs-lookup"><span data-stu-id="da4cc-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="da4cc-240">Kaynağınızı "tehlikeli" işlemleri gerçekleştiriliyorsa, uygulamak için iyi bir uygulamadır `-WhatIf` işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="da4cc-240">If your resource is performing “dangerous” operations, it’s a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="da4cc-241">Bunu yaptıktan sonra emin olun `-WhatIf` çıkış doğru olmadan komut yürütülürse olacağını işlemleri açıklar `-WhatIf` geçin.</span><span class="sxs-lookup"><span data-stu-id="da4cc-241">After it’s done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="da4cc-242">Ayrıca, operations yürütülmez doğrulayın (düğümün durumu için hiçbir değişiklik yapılmaz) olduğunda `–WhatIf` anahtar.</span><span class="sxs-lookup"><span data-stu-id="da4cc-242">Also, verify that operations does not execute (no changes to the node’s state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="da4cc-243">Örneğin, şu dosya kaynak test varsayalım.</span><span class="sxs-lookup"><span data-stu-id="da4cc-243">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="da4cc-244">Aşağıdaki dosya oluşturan basit yapılandırmadır `test.txt` "test" içeriğiyle:</span><span class="sxs-lookup"><span data-stu-id="da4cc-244">Below is simple configuration which creates file `test.txt` with contents “test”:</span></span>

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

<span data-ttu-id="da4cc-245">Derleme ve sonra yapılandırmasıyla yürütün `-WhatIf` anahtarı, çıkış unsurdur bize yapılandırma çalıştırıyoruz, tam olarak ne olacağını.</span><span class="sxs-lookup"><span data-stu-id="da4cc-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="da4cc-246">Yapılandırma ancak yürütülmedi (`test.txt` dosyası oluşturulmadı).</span><span class="sxs-lookup"><span data-stu-id="da4cc-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
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

<span data-ttu-id="da4cc-247">Bu liste kapsamlı değildir, ancak tasarlama, geliştirme ve test etme DSC kaynakları hatayla karşılaşıldı, birçok önemli sorunları kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="da4cc-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
