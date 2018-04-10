---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 66ceea383b78b2654caa4f1de16a30beea0e7fd3
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="92cb2-102">İstenen durum yapılandırması (DSC) bilinen sorunlar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="92cb2-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="92cb2-103">Yeni değişiklik: DSC yapılandırmaları parolalarda şifreleme/şifre çözme için kullanılan sertifikaları WMF 5.0 RTM yükledikten sonra çalışmayabilir</span><span class="sxs-lookup"><span data-stu-id="92cb2-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="92cb2-104">WMF 4.0 ve WMF 5.0 Önizleme sürümlerde DSC parolaları uzunlukta yapılandırmasında izin vermez birden fazla 121 karakter.</span><span class="sxs-lookup"><span data-stu-id="92cb2-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="92cb2-105">DSC uzun ve güçlü parola gerekli olsa bile kısa parolalarını zorlama.</span><span class="sxs-lookup"><span data-stu-id="92cb2-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="92cb2-106">Bu önemli değişiklik parolaları DSC yapılandırması, rastgele uzunlukta olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="92cb2-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="92cb2-107">**Çözüm:** verileri şifreleme veya anahtar şifreleme anahtarı kullanımını ve belge şifreleme Gelişmiş anahtar kullanımı (1.3.6.1.4.1.311.80.1) sertifikayla yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92cb2-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="92cb2-108">TechNet makalesine <https://technet.microsoft.com/library/dn807171.aspx> daha fazla bilgi bulunur.</span><span class="sxs-lookup"><span data-stu-id="92cb2-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="92cb2-109">DSC cmdlet'leri WMF 5.0 RTM yükledikten sonra başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="92cb2-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>
------------------------------------------------------------------------------------
<span data-ttu-id="92cb2-110">Başlangıç DscConfiguration ve diğer DSC cmdlet'lerini şu hata ile WMF 5.0 RTM yükledikten sonra başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="92cb2-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="92cb2-111">**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak DSCEngineCache.mof silin:</span><span class="sxs-lookup"><span data-stu-id="92cb2-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="92cb2-112">WMF 5.0 RTM WMF 5.0 üretim Önizleme üzerinde yüklüyse, DSC cmdlet'leri çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="92cb2-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>
------------------------------------------------------
<span data-ttu-id="92cb2-113">**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="92cb2-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="92cb2-114">LCM'yi yönteminde Get-DscConfiguration kullanırken kararsız bir duruma gidebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="92cb2-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>
-------------------------------------------------------------------------------

<span data-ttu-id="92cb2-115">LCM'yi yönteminde ise, Get-DscConfiguration işlenmesini durdurmak için CTRL + C tuşlarına basarak gitmek LCM'yi neden olabilir bir kararsız duruma gibi bu DSC cmdlet'leri çoğunluğu çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="92cb2-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="92cb2-116">**Çözüm:** Get-DscConfiguration cmdlet'i hata ayıklama sırasında CTRL + C tuşlarına yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a><span data-ttu-id="92cb2-117">Stop-DscConfiguration yönteminde kilitlenebilir</span><span class="sxs-lookup"><span data-stu-id="92cb2-117">Stop-DscConfiguration may hang in DebugMode</span></span>
------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="92cb2-118">LCM'yi yönteminde ise, Get-DscConfiguration tarafından başlatılan bir işlem durdurulmaya çalışılırken sırasında durdurma DscConfiguration kilitlenebilir</span><span class="sxs-lookup"><span data-stu-id="92cb2-118">If LCM is in DebugMode, Stop-DscConfiguration may hang while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="92cb2-119">**Çözüm:** bölümde özetlendiği gibi Get-DscConfiguration tarafından başlatılan işlem hata ayıklaması son '[hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource)'.</span><span class="sxs-lookup"><span data-stu-id="92cb2-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="92cb2-120">Yönteminde hiçbir ayrıntılı hata iletileri gösterilir</span><span class="sxs-lookup"><span data-stu-id="92cb2-120">No Verbose Error Messages are shown in DebugMode</span></span>
-----------------------------------------------------------------------------------
<span data-ttu-id="92cb2-121">LCM'yi yönteminde ise, DSC kaynaklarından herhangi bir ayrıntılı hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="92cb2-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="92cb2-122">**Çözüm:** devre dışı *DebugMode* kaynaktan ayrıntılı iletiler görmek için</span><span class="sxs-lookup"><span data-stu-id="92cb2-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="92cb2-123">Get-DscConfigurationStatus cmdlet'i tarafından çağırma DscResource işlemler alınamıyor</span><span class="sxs-lookup"><span data-stu-id="92cb2-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>
--------------------------------------------------------------------------------------
<span data-ttu-id="92cb2-124">Invoke-DscResource cmdlet'i herhangi kaynağın yöntemlerini doğrudan çağırmak için kullandıktan sonra bu tür işlemi kayıtları Get-DscConfigurationStatus daha sonraki bir zamanda alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="92cb2-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="92cb2-125">**Çözüm:** yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-125">**Resolution:** None.</span></span>


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="92cb2-126">Get-DscConfigurationStatus döndürür çekme döngüsü işlemleri türü olarak *tutarlılık*</span><span class="sxs-lookup"><span data-stu-id="92cb2-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="92cb2-127">Bir düğüm gerçekleştirilen, her bir çekme işlemin ÇEKME yenileme modu ayarlandığında Get-DscConfigurationStatus cmdlet'i işlemi türü olarak raporlar *tutarlılık* yerine *ilk*</span><span class="sxs-lookup"><span data-stu-id="92cb2-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="92cb2-128">**Çözüm:** yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-128">**Resolution:** None.</span></span>

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="92cb2-129">Çağırma DscResource cmdlet üretilmiş olan sırada ileti döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="92cb2-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="92cb2-130">Invoke-DscResource cmdlet'i uyarı, ayrıntılı döndürmüyor ve LCM'yi veya DSC kaynağı tarafından üretilmiş olan sırada bir hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="92cb2-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="92cb2-131">**Çözüm:** yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-131">**Resolution:** None.</span></span>


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="92cb2-132">DSC kaynakları kolayca Invoke-DscResource ile kullanıldığında hata ayıklaması yapılabilir olamaz</span><span class="sxs-lookup"><span data-stu-id="92cb2-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>
-----------------------------------------------------------------------
<span data-ttu-id="92cb2-133">Hata ayıklama modunda LCM'yi çalışırken (bkz [hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource) daha fazla ayrıntı için), Invoke-DscResource cmdlet'i hata ayıklama için bağlanmak için çalışma alanı hakkında bilgi vermek değil.</span><span class="sxs-lookup"><span data-stu-id="92cb2-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="92cb2-134">**Çözüm:** bulma ve cmdlet'lerini kullanarak çalışma attach **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-çalışma** ve **Hata ayıklama çalışma** DSC kaynağı hata ayıklamak için.</span><span class="sxs-lookup"><span data-stu-id="92cb2-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

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


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="92cb2-135">Çeşitli kısmi yapılandırma belgeleri aynı düğüm için aynı kaynak adları olamaz</span><span class="sxs-lookup"><span data-stu-id="92cb2-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>
------------------------------------------------------------------------------------------

<span data-ttu-id="92cb2-136">Tek bir düğüme dağıtılan birkaç kısmi yapılandırmaları için kaynakları neden aynı adlarını çalıştırma hatası.</span><span class="sxs-lookup"><span data-stu-id="92cb2-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="92cb2-137">**Çözüm:** farklı kısmi yapılandırmalarında bile aynı kaynakları için farklı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="92cb2-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="92cb2-138">Başlangıç DscConfiguration – UseExisting çalışmıyor ile - kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="92cb2-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>
------------------------------------------------------------------

<span data-ttu-id="92cb2-139">Başlangıç DscConfiguration – UseExisting parametresiyle kullanırken kimlik bilgisi parametresi yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="92cb2-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="92cb2-140">DSC işlemi devam etmek için varsayılan işlem kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="92cb2-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="92cb2-141">Uzak düğümde devam etmek için farklı bir kimlik bilgisi gerektiğinde bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="92cb2-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="92cb2-142">**Çözüm:** kullanım CIM oturumu uzak DSC işlemler için:</span><span class="sxs-lookup"><span data-stu-id="92cb2-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="92cb2-143">IPv6 adresleri DSC yapılandırmalarında düğüm adı olarak</span><span class="sxs-lookup"><span data-stu-id="92cb2-143">IPv6 Addresses as Node Names in DSC configurations</span></span>
--------------------------------------------------
<span data-ttu-id="92cb2-144">IPv6 adresleri düğüm adları DSC yapılandırma komut olarak bu sürümde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="92cb2-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="92cb2-145">**Çözüm:** yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-145">**Resolution:** None.</span></span>


<a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="92cb2-146">Sınıf tabanlı DSC kaynakları hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="92cb2-146">Debugging of Class-Based DSC Resources</span></span>
--------------------------------------
<span data-ttu-id="92cb2-147">Sınıf tabanlı DSC kaynakları hata ayıklama bu sürümde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="92cb2-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="92cb2-148">**Çözüm:** yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-148">**Resolution:** None.</span></span>


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="92cb2-149">Değişkenleri & DSC sınıf tabanlı kaynak $script kapsamda tanımlanan işlevleri DSC kaynağı için birden fazla çağrı arasında korunmaz</span><span class="sxs-lookup"><span data-stu-id="92cb2-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>
-------------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="92cb2-150">Yapılandırma değişkenleri veya işlevleri $script kapsamda tanımlı olan tüm sınıf tabanlı kaynak kullanıyorsa, başlangıç DSCConfiguration birden çok ardışık çağrıları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="92cb2-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="92cb2-151">**Çözüm:** tüm değişkenleri ve işlevleri DSC kaynağı sınıfında kendisini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="92cb2-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="92cb2-152">No $script kapsam değişkenleri/işlevler.</span><span class="sxs-lookup"><span data-stu-id="92cb2-152">No $script scope variables/functions.</span></span>


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="92cb2-153">DSC kaynağı bir kaynak PSDscRunAsCredential kullanılırken hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="92cb2-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>
----------------------------------------------------------------------
<span data-ttu-id="92cb2-154">Bir kaynak kullanırken DSC kaynak hata ayıklama *PSDscRunAsCredential* yapılandırma özelliğinde desteklenen bu sürümde değil.</span><span class="sxs-lookup"><span data-stu-id="92cb2-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="92cb2-155">**Çözüm:** yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-155">**Resolution:** None.</span></span>


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="92cb2-156">PsDscRunAsCredential DSC bileşik kaynaklar için desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="92cb2-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>
----------------------------------------------------------------

<span data-ttu-id="92cb2-157">**Çözüm:** kullanım kimlik bilgisi özelliği varsa.</span><span class="sxs-lookup"><span data-stu-id="92cb2-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="92cb2-158">Örnek ServiceSet ve WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="92cb2-158">Example ServiceSet and WindowsFeatureSet</span></span>


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="92cb2-159">*Get-DscResource-sözdizimi* PsDscRunAsCredential doğru şekilde yansıtmaz</span><span class="sxs-lookup"><span data-stu-id="92cb2-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>
-------------------------------------------------------------------------
<span data-ttu-id="92cb2-160">Get-DscResource-sözdizimi değil yansıtacak PsDscRunAsCredential doğru kaynak zorunlu olarak işaretler veya bunu desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="92cb2-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="92cb2-161">**Çözüm:** yok.</span><span class="sxs-lookup"><span data-stu-id="92cb2-161">**Resolution:** None.</span></span> <span data-ttu-id="92cb2-162">Ancak, işe yapılandırmasında yazma PsDscRunAsCredential özelliği hakkında doğru meta veri IntelliSense kullanırken'yansıtır.</span><span class="sxs-lookup"><span data-stu-id="92cb2-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="92cb2-163">Windows 7'de WindowsOptionalFeature kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="92cb2-163">WindowsOptionalFeature is not available in Windows 7</span></span>
-----------------------------------------------------

<span data-ttu-id="92cb2-164">WindowsOptionalFeature DSC kaynağı, Windows 7'de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92cb2-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="92cb2-165">Bu kaynak DISM modülünü ve Windows 8 ve Windows işletim sisteminin daha yeni sürümleri başlayarak kullanılabilir DISM cmdlet'leri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="92cb2-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="92cb2-166">Sınıf tabanlı DSC kaynakları için içeri aktarma DscResource - ModuleVersion beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="92cb2-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>
------------------------------------------------------------------------------------------
<span data-ttu-id="92cb2-167">Derleme düğümü bir sınıf tabanlı DSC kaynağı modülü, birden fazla sürümü varsa `Import-DscResource -ModuleVersion` belirtilen sürüm çekme değil ve aşağıdaki derleme hata neden olur.</span><span class="sxs-lookup"><span data-stu-id="92cb2-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="92cb2-168">**Çözüm:** tanımlayarak gerekli sürümü alma *ModuleSpecification* nesnesini `-ModuleName` ile `RequiredVersion` gibi belirtilen anahtarı:</span><span class="sxs-lookup"><span data-stu-id="92cb2-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>
``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="92cb2-169">Kayıt defteri kaynak gibi bazı DSC kaynakları isteğini işlemek için uzun zaman başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="92cb2-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="92cb2-170">**Resolution1:** aşağıdaki klasörü düzenli aralıklarla temizlenir bir zamanlama görevi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92cb2-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>
``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="92cb2-171">**Resolution2:** temizlemek için DSC yapılandırmasını değiştirme *CommandAnalysis* yapılandırmasının sonunda klasör.</span><span class="sxs-lookup"><span data-stu-id="92cb2-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>
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