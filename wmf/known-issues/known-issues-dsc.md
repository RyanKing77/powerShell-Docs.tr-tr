---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Desired State Configuration (DSC) bilinen sorunlar ve sınırlamalar
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856199"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="b6fc8-103">Desired State Configuration (DSC) bilinen sorunlar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="b6fc8-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="b6fc8-104">Yeni değişiklik: DSC yapılandırmaları parolaları şifreleme/şifre çözme için kullanılan sertifikaları WMF 5.0 RTM'ye yükledikten sonra çalışmayabilir</span><span class="sxs-lookup"><span data-stu-id="b6fc8-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="b6fc8-105">WMF 4.0 ve WMF 5.0 Önizleme sürümlerinde DSC parolaları uzunlukta yapılandırmada izin vermez 121'den fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="b6fc8-106">DSC bile uzun ve güçlü bir parola istenen kısa parolalarını zorlama.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="b6fc8-107">Bu değişiklik, parolalar DSC yapılandırma rastgele uzunlukta olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="b6fc8-108">**Çözüm:** Veri şifreleme veya anahtar şifreleme anahtarı kullanım yanı sıra, belge şifreleme Gelişmiş anahtar kullanımı (1.3.6.1.4.1.311.80.1) sertifikayla yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="b6fc8-109">Daha fazla bilgi için [Koru CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="b6fc8-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="b6fc8-110">WMF 5.0 RTM'ye yükledikten sonra DSC cmdlet başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="b6fc8-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="b6fc8-111">`Start-DscConfiguration` ve diğer DSC cmdlet'leri WMF 5.0 RTM'ye şu hata ile yükledikten sonra başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="b6fc8-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="b6fc8-112">**Çözüm:** (Yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak DSCEngineCache.mof silin:</span><span class="sxs-lookup"><span data-stu-id="b6fc8-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="b6fc8-113">WMF 5.0 RTM'ye WMF 5.0 üretim önizlemesi üzerine yüklenirse, DSC cmdlet'leri çalışmayabilir</span><span class="sxs-lookup"><span data-stu-id="b6fc8-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="b6fc8-114">**Çözüm:** (Yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b6fc8-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="b6fc8-115">Get-DscConfiguration yönteminde kullanırken kararsız bir duruma LCM gidebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b6fc8-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="b6fc8-116">Yönteminde LCM ise işlenmesini durdurmak için CTRL + C tuşlarına `Get-DscConfiguration` Git LCM neden olabilir, DSC cmdlet'leri çoğunu bir kararsız duruma gibi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="b6fc8-117">**Çözüm:** Hata ayıklama sırasında CTRL + C tuşlarına yoksa `Get-DscConfiguration` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="b6fc8-118">Stop-DscConfiguration yönteminde yanıtlayamayabilir</span><span class="sxs-lookup"><span data-stu-id="b6fc8-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="b6fc8-119">LCM yönteminde, ise `Stop-DscConfiguration` başlatan bir işlem durdurulmaya çalışılırken sırada yanıtlayamayabilir `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="b6fc8-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="b6fc8-120">**Çözüm:** Başlatan işlemin hata ayıklamasını bitirdiğinizde `Get-DscConfiguration` açıklandığı şekilde [hata ayıklama DSC kaynakları](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="b6fc8-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="b6fc8-121">Hiçbir ayrıntılı hata iletilerini yönteminde gösterilir</span><span class="sxs-lookup"><span data-stu-id="b6fc8-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="b6fc8-122">LCM ise **DebugMode**, DSC kaynaklarından herhangi bir ayrıntılı hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="b6fc8-123">**Çözüm:** Devre dışı **DebugMode** kaynaktan ayrıntılı iletileri görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="b6fc8-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="b6fc8-124">Invoke-DscResource işlemler Get-DscConfigurationStatus cmdlet'i tarafından geri alınamaz</span><span class="sxs-lookup"><span data-stu-id="b6fc8-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="b6fc8-125">Kullandıktan sonra `Invoke-DscResource` kayıtlar gibi işleminin herhangi bir kaynağın yöntemleri doğrudan çağırmak için cmdlet'i aracılığıyla alınamaz `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="b6fc8-126">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="b6fc8-127">Get-DscConfigurationStatus döndürür çekme döngüsü işlemleri türü olarak **tutarlılık**</span><span class="sxs-lookup"><span data-stu-id="b6fc8-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="b6fc8-128">Bir düğüm her çekme işleminde gerçekleştirilen, ÇEKME yenileme modu ayarlandığında `Get-DscConfigurationStatus` cmdlet'i işlem türü olarak raporlar **tutarlılık** yerine *ilk*</span><span class="sxs-lookup"><span data-stu-id="b6fc8-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="b6fc8-129">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="b6fc8-130">Invoke-DscResource cmdlet'i üretilmiş olan sırayla ileti döndürmez</span><span class="sxs-lookup"><span data-stu-id="b6fc8-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="b6fc8-131">`Invoke-DscResource` Cmdlet'i uyarı, ayrıntılı döndürmüyor ve bunlar üretilen LCM veya DSC kaynağı sırada bir hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="b6fc8-132">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="b6fc8-133">DSC kaynakları kolayca Invoke-DscResource ile kullanıldığında ayıklanamıyor</span><span class="sxs-lookup"><span data-stu-id="b6fc8-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="b6fc8-134">LCM hata ayıklama modunda çalışırken `Invoke-DscResource` cmdlet'i, hata ayıklama için bağlanmak için çalışma alanı hakkında bilgi vermek değil.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="b6fc8-135">Daha fazla bilgi için [hata ayıklama DSC kaynakları](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="b6fc8-135">For more information, see [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="b6fc8-136">**Çözüm:** Bulma ve cmdlet'lerini kullanarak bir çalışma ekleme `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` ve `Debug-Runspace` DSC kaynak hata ayıklamak için.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="b6fc8-137">Aynı kaynak adları aynı düğüm için çeşitli kısmi yapılandırma belgelerini sahip olamaz</span><span class="sxs-lookup"><span data-stu-id="b6fc8-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="b6fc8-138">Tek bir düğüme dağıtılır birkaç kısmi yapılandırmalar için kaynakları neden aynı adları çalıştırma hatası.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="b6fc8-139">**Çözüm:** Kısmi farklı yapılandırmalarda bile aynı kaynakları için farklı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="b6fc8-140">Start-DscConfiguration – UseExisting çalışmıyor - ile kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="b6fc8-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="b6fc8-141">Kullanırken `Start-DscConfiguration` ile **UseExisting** parametresi **kimlik bilgisi** parametresi yok sayıldı.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="b6fc8-142">DSC, işleme devam etmek için varsayılan işlem kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="b6fc8-143">Uzak düğüm üzerinde devam etmek için farklı bir kimlik bilgisi gerektiğinde bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="b6fc8-144">**Çözüm:** CIM oturumu, uzak DSC işlemleri için kullanın:</span><span class="sxs-lookup"><span data-stu-id="b6fc8-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="b6fc8-145">DSC yapılandırmaları düğüm adları olarak IPv6 adresleri</span><span class="sxs-lookup"><span data-stu-id="b6fc8-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="b6fc8-146">IPv6 adresleri DSC yapılandırma betiklerini düğüm adları olarak bu sürümde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="b6fc8-147">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="b6fc8-148">Hata ayıklama `Class-Based` DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="b6fc8-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="b6fc8-149">DSC kaynakları sınıf tabanlı hata ayıklama bu sürümde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="b6fc8-150">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="b6fc8-151">Değişkenlerin ve işlevlerin DSC sınıf tabanlı kaynak $script kapsamda tanımlanan birden çok çağrı DSC kaynak arasında korunmaz</span><span class="sxs-lookup"><span data-stu-id="b6fc8-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="b6fc8-152">Birden çok ardışık çağrı `Start-DSCConfiguration` yapılandırma değişkenleri olan tüm sınıf tabanlı kaynak kullanıyor veya tanımlı işlevler başarısız `$script` kapsam.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="b6fc8-153">**Çözüm:** Tüm değişkenlerin ve işlevlerin DSC kaynak kendisini tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="b6fc8-154">Hayır `$script` kapsam değişkenleri/işlevleri.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="b6fc8-155">DSC kaynak bir kaynak PSDscRunAsCredential kullanılırken hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b6fc8-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="b6fc8-156">DSC kaynak bir kaynak kullanılırken hata ayıklama **PSDscRunAsCredential** Yapılandırma özelliği bu sürümde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="b6fc8-157">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="b6fc8-158">PsDscRunAsCredential bileşik DSC kaynakları için desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b6fc8-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="b6fc8-159">**Çözüm:** Kimlik bilgisi özelliği varsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="b6fc8-160">Örnek ServiceSet ve WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="b6fc8-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="b6fc8-161">Get-DscResource-söz dizimi PsDscRunAsCredential düzgün yansıtmıyor</span><span class="sxs-lookup"><span data-stu-id="b6fc8-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="b6fc8-162">**Söz dizimi** parametresi yansıtmıyor **PsDscRunAsCredential** doğru zaman kaynağı zorunlu olarak işaretler veya bunu desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="b6fc8-163">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-163">**Resolution:** None.</span></span> <span data-ttu-id="b6fc8-164">Ancak, işe yapılandırmasında yazma doğru meta verileri hakkında yansıtır **PsDscRunAsCredential** IntelliSense kullanırken özelliği.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="b6fc8-165">WindowsOptionalFeature Windows 7'de kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="b6fc8-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="b6fc8-166">**WindowsOptionalFeature** DSC kaynağı, Windows 7'de kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="b6fc8-167">Bu kaynak, DISM modülünü ve Windows 8 Windows işletim sisteminin daha yeni sürümlerde başlayarak kullanılabilir olan DISM cmdlet'leri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="b6fc8-168">Sınıf tabanlı DSC kaynakları için Import-DscResource - ModuleVersion beklendiği gibi çalışmayabilir</span><span class="sxs-lookup"><span data-stu-id="b6fc8-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="b6fc8-169">Derleme düğümü DSC kaynak sınıf tabanlı modülü birden fazla sürümü varsa `Import-DscResource -ModuleVersion` belirtilen sürümde çekme değil ve aşağıdaki derleme hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="b6fc8-170">**Çözüm:** Tanımlayarak gerekli sürümü alma **ModuleSpecification** nesnesini **ModuleName** parametresiyle **RequiredVersion** gibi belirtilen bir anahtarı:</span><span class="sxs-lookup"><span data-stu-id="b6fc8-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="b6fc8-171">Registry kaynağı gibi bazı DSC kaynakları isteği işlemek için uzun süren başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="b6fc8-172">**1. çözüm:** Aşağıdaki klasörü düzenli aralıklarla temizleyen bir zamanlama görev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="b6fc8-173">**2. çözüm:** Temizlemek için DSC yapılandırmasını değiştirmek *CommandAnalysis* yapılandırmanın sonunda klasör.</span><span class="sxs-lookup"><span data-stu-id="b6fc8-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
