---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795156"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="751f9-102">Desired State Configuration (DSC) bilinen sorunlar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="751f9-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="751f9-103">Yeni değişiklik: DSC yapılandırmaları parolaları şifreleme/şifre çözme için kullanılan sertifikaları WMF 5.0 RTM'ye yükledikten sonra çalışmayabilir</span><span class="sxs-lookup"><span data-stu-id="751f9-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="751f9-104">WMF 4.0 ve WMF 5.0 Önizleme sürümlerinde DSC parolaları uzunlukta yapılandırmada izin vermez 121'den fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="751f9-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="751f9-105">DSC bile uzun ve güçlü bir parola istenen kısa parolalarını zorlama.</span><span class="sxs-lookup"><span data-stu-id="751f9-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="751f9-106">Bu değişiklik, parolalar DSC yapılandırma rastgele uzunlukta olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="751f9-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="751f9-107">**Çözüm:** Veri şifreleme veya anahtar şifreleme anahtarı kullanım yanı sıra, belge şifreleme Gelişmiş anahtar kullanımı (1.3.6.1.4.1.311.80.1) sertifikayla yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="751f9-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="751f9-108">TechNet makalesine <https://technet.microsoft.com/library/dn807171.aspx> daha fazla bilgi bulunur.</span><span class="sxs-lookup"><span data-stu-id="751f9-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="751f9-109">WMF 5.0 RTM'ye yükledikten sonra DSC cmdlet başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="751f9-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="751f9-110">Start-DscConfiguration ve diğer DSC cmdlet'leri WMF 5.0 RTM'ye şu hata ile yükledikten sonra başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="751f9-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="751f9-111">**Çözüm:** (Yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak DSCEngineCache.mof silin:</span><span class="sxs-lookup"><span data-stu-id="751f9-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="751f9-112">WMF 5.0 RTM'ye WMF 5.0 üretim önizlemesi üzerine yüklenirse, DSC cmdlet'leri çalışmayabilir</span><span class="sxs-lookup"><span data-stu-id="751f9-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="751f9-113">**Çözüm:** (Yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="751f9-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="751f9-114">Get-DscConfiguration yönteminde kullanırken kararsız bir duruma LCM gidebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="751f9-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="751f9-115">Yönteminde LCM ise, Get-DscConfiguration işlenmesini durdurmak için CTRL + C tuşlarına basarak Git LCM neden olabilir, DSC cmdlet'leri çoğunu bir kararsız duruma gibi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="751f9-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="751f9-116">**Çözüm:** Get-DscConfiguration cmdlet'i hata ayıklama sırasında CTRL + C tuşlarına basın yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="751f9-117">Stop-DscConfiguration yönteminde yanıtlayamayabilir</span><span class="sxs-lookup"><span data-stu-id="751f9-117">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="751f9-118">Yönteminde LCM ise bir işlem durdurulmaya çalışılırken Get-DscConfiguration başlatılırken Stop-DscConfiguration yanıtlayamayabilir</span><span class="sxs-lookup"><span data-stu-id="751f9-118">If LCM is in DebugMode, Stop-DscConfiguration may not respond while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="751f9-119">**Çözüm:** Son bölümde açıklandığı gibi Get-DscConfiguration tarafından başlatılan işlem hata ayıklama '[hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource)'.</span><span class="sxs-lookup"><span data-stu-id="751f9-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="751f9-120">Hiçbir ayrıntılı hata iletilerini yönteminde gösterilir</span><span class="sxs-lookup"><span data-stu-id="751f9-120">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="751f9-121">LCM yönteminde, DSC kaynaklarından herhangi bir ayrıntılı hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="751f9-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="751f9-122">**Çözüm:** Devre dışı *DebugMode* kaynaktan ayrıntılı iletileri görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="751f9-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="751f9-123">Invoke-DscResource işlemler Get-DscConfigurationStatus cmdlet'i tarafından geri alınamaz</span><span class="sxs-lookup"><span data-stu-id="751f9-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="751f9-124">Herhangi bir kaynağın yöntemleri doğrudan çağırmak için Invoke-DscResource cmdlet'i kullandıktan sonra bu işlemi kayıtlarını Get-DscConfigurationStatus daha sonraki bir zamanda alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="751f9-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="751f9-125">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-125">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="751f9-126">Get-DscConfigurationStatus döndürür çekme döngüsü işlemleri türü olarak *tutarlılık*</span><span class="sxs-lookup"><span data-stu-id="751f9-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>

<span data-ttu-id="751f9-127">Bir düğüm her çekme işleminde gerçekleştirilen, ÇEKME yenileme moduna ayarlandığında Get-DscConfigurationStatus cmdlet'i işlem türü olarak raporlar *tutarlılık* yerine *ilk*</span><span class="sxs-lookup"><span data-stu-id="751f9-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="751f9-128">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-128">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="751f9-129">Invoke-DscResource cmdlet'i üretilmiş olan sırayla ileti döndürmez</span><span class="sxs-lookup"><span data-stu-id="751f9-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="751f9-130">Invoke-DscResource cmdlet uyarı, ayrıntılı döndürmüyor ve LCM veya DSC kaynağı tarafından üretilmiş olan sırayla hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="751f9-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="751f9-131">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-131">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="751f9-132">DSC kaynakları kolayca Invoke-DscResource ile kullanıldığında ayıklanamıyor</span><span class="sxs-lookup"><span data-stu-id="751f9-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="751f9-133">LCM hata ayıklama modunda çalışırken (bkz [hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource) daha fazla ayrıntı için), Invoke-DscResource cmdlet'i, hata ayıklama için bağlanmak için çalışma alanı hakkında bilgi vermek değil.</span><span class="sxs-lookup"><span data-stu-id="751f9-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="751f9-134">**Çözüm:** Bulma ve cmdlet'lerini kullanarak bir çalışma ekleme **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-çalışma** ve **hataayıklama-çalışmaalanı** DSC kaynak hata ayıklamak için.</span><span class="sxs-lookup"><span data-stu-id="751f9-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="751f9-135">Aynı kaynak adları aynı düğüm için çeşitli kısmi yapılandırma belgelerini sahip olamaz</span><span class="sxs-lookup"><span data-stu-id="751f9-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="751f9-136">Tek bir düğüme dağıtılır birkaç kısmi yapılandırmalar için kaynakları neden aynı adları çalıştırma hatası.</span><span class="sxs-lookup"><span data-stu-id="751f9-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="751f9-137">**Çözüm:** Kısmi farklı yapılandırmalarda bile aynı kaynakları için farklı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="751f9-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="751f9-138">Start-DscConfiguration – UseExisting çalışmıyor - ile kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="751f9-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="751f9-139">Start-DscConfiguration – UseExisting parametresiyle birlikte kullanıldığında Credential parametresi yok sayıldı.</span><span class="sxs-lookup"><span data-stu-id="751f9-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="751f9-140">DSC, işleme devam etmek için varsayılan işlem kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="751f9-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="751f9-141">Uzak düğüm üzerinde devam etmek için farklı bir kimlik bilgisi gerektiğinde bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="751f9-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="751f9-142">**Çözüm:** CIM oturumu, uzak DSC işlemleri için kullanın:</span><span class="sxs-lookup"><span data-stu-id="751f9-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="751f9-143">DSC yapılandırmaları düğüm adları olarak IPv6 adresleri</span><span class="sxs-lookup"><span data-stu-id="751f9-143">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="751f9-144">IPv6 adresleri DSC yapılandırma betiklerini düğüm adları olarak bu sürümde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="751f9-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="751f9-145">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-145">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="751f9-146">Sınıf tabanlı DSC kaynaklarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="751f9-146">Debugging of Class-Based DSC Resources</span></span>

<span data-ttu-id="751f9-147">DSC kaynakları sınıf tabanlı hata ayıklama bu sürümde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="751f9-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="751f9-148">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-148">**Resolution:** None.</span></span>

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="751f9-149">Değişkenleri İşle & vleri DSC sınıf tabanlı kaynak $script kapsamda tanımlanan birden çok çağrı DSC kaynak arasında korunmaz</span><span class="sxs-lookup"><span data-stu-id="751f9-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="751f9-150">Yapılandırma değişkenleri veya $script kapsamında tanımlanan işlevleri olan tüm sınıf tabanlı kaynak kullanıyorsa, birden çok ardışık Başlat-DSCConfiguration çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="751f9-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="751f9-151">**Çözüm:** Tüm değişkenlerin ve işlevlerin DSC kaynak kendisini tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="751f9-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="751f9-152">No $script kapsam değişkenleri/işlevler.</span><span class="sxs-lookup"><span data-stu-id="751f9-152">No $script scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="751f9-153">DSC kaynak bir kaynak PSDscRunAsCredential kullanılırken hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="751f9-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="751f9-154">DSC kaynak bir kaynak kullanılırken hata ayıklama *PSDscRunAsCredential* Yapılandırma özelliği bu sürümde vnet'i değil.</span><span class="sxs-lookup"><span data-stu-id="751f9-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="751f9-155">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-155">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="751f9-156">PsDscRunAsCredential bileşik DSC kaynakları için desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="751f9-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="751f9-157">**Çözüm:** Kimlik bilgisi özelliği varsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="751f9-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="751f9-158">Örnek ServiceSet ve WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="751f9-158">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="751f9-159">*Get-DscResource-söz dizimi* PsDscRunAsCredential doğru şekilde yansıtmaz</span><span class="sxs-lookup"><span data-stu-id="751f9-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="751f9-160">Get-DscResource-söz dizimi yansıtmıyor PsDscRunAsCredential doğru kaynak zorunlu olarak işaretler ya da bunu desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="751f9-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="751f9-161">**Çözüm:** Yok.</span><span class="sxs-lookup"><span data-stu-id="751f9-161">**Resolution:** None.</span></span> <span data-ttu-id="751f9-162">Ancak, işe yapılandırmasında yazma PsDscRunAsCredential özelliği doğru meta verilerini IntelliSense kullanırken'yansıtır.</span><span class="sxs-lookup"><span data-stu-id="751f9-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="751f9-163">WindowsOptionalFeature Windows 7'de kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="751f9-163">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="751f9-164">WindowsOptionalFeature DSC kaynak, Windows 7'de kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="751f9-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="751f9-165">Bu kaynak, DISM modülünü ve Windows 8 Windows işletim sisteminin daha yeni sürümlerde başlayarak kullanılabilir olan DISM cmdlet'leri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="751f9-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="751f9-166">Sınıf tabanlı DSC kaynakları için Import-DscResource - ModuleVersion beklendiği gibi çalışmayabilir</span><span class="sxs-lookup"><span data-stu-id="751f9-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="751f9-167">Derleme düğümü DSC kaynak sınıf tabanlı modülü birden fazla sürümü varsa `Import-DscResource -ModuleVersion` belirtilen sürümde çekme değil ve aşağıdaki derleme hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="751f9-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="751f9-168">**Çözüm:** Tanımlayarak gerekli sürümü alma *ModuleSpecification* nesnesini `-ModuleName` ile `RequiredVersion` gibi belirtilen bir anahtarı:</span><span class="sxs-lookup"><span data-stu-id="751f9-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="751f9-169">Registry kaynağı gibi bazı DSC kaynakları isteği işlemek için uzun süren başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="751f9-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="751f9-170">**Resolution1:** Aşağıdaki klasörü düzenli aralıklarla temizleyen bir zamanlama görev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="751f9-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="751f9-171">**Resolution2:** Temizlemek için DSC yapılandırmasını değiştirmek *CommandAnalysis* yapılandırmanın sonunda klasör.</span><span class="sxs-lookup"><span data-stu-id="751f9-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

``` PowerShell
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
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
