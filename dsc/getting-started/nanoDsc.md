---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Nano Server’da DSC Kullanma
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079736"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="23729-103">Nano Server’da DSC Kullanma</span><span class="sxs-lookup"><span data-stu-id="23729-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="23729-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="23729-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="23729-105">**Nano Sunucu'da DSC** isteğe bağlı bir pakette `NanoServer\Packages` Windows Server 2016 medya klasörü.</span><span class="sxs-lookup"><span data-stu-id="23729-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="23729-106">Belirterek bir Nano sunucu için bir VHD oluşturduğunuzda, paketin yüklenebilir **Microsoft-NanoServer-DSC-Package** değeri olarak **paketleri** parametresinin **New-Nanoserverımage**  işlevi.</span><span class="sxs-lookup"><span data-stu-id="23729-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="23729-107">Örneğin, bir VHD için bir sanal makine oluşturuyorsanız, komut aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="23729-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="23729-108">Yükleme ve PowerShell uzaktan iletişimi ile Nano sunucuyu yönetmek nasıl yanı sıra, Nano Server'ı kullanma hakkında daha fazla bilgi için bkz: [Nano Server ile çalışmaya başlama](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="23729-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="23729-109">Nano Sunucu'da DSC Özellikler</span><span class="sxs-lookup"><span data-stu-id="23729-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="23729-110">Nano sunucu Windows Server'ın tam sürümüne kıyasla API'leri yalnızca sınırlı sayıda desteklediğinden, Nano Sunucu'da DSC tam işlevsel eşlik şimdilik tam SKU'ları üzerinde çalışan DSC ile yok.</span><span class="sxs-lookup"><span data-stu-id="23729-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="23729-111">Nano Sunucu'da DSC active geliştirme aşamasındadır ve henüz tam bir özellik değil.</span><span class="sxs-lookup"><span data-stu-id="23729-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="23729-112">Şu DSC özellikler şu anda Nano Sunucu'da kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="23729-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="23729-113">Hem İtme hem de çekme modu</span><span class="sxs-lookup"><span data-stu-id="23729-113">Both push and pull modes</span></span>

- <span data-ttu-id="23729-114">Aşağıdakiler dahil olmak üzere Windows Server'ın tam sürümünde mevcut tüm DSC cmdlet'leri:</span><span class="sxs-lookup"><span data-stu-id="23729-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="23729-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="23729-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="23729-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="23729-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="23729-117">DscDebug etkinleştir</span><span class="sxs-lookup"><span data-stu-id="23729-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="23729-118">DscDebug devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="23729-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="23729-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="23729-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="23729-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="23729-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="23729-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="23729-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="23729-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="23729-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="23729-123">Yayımlama-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="23729-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="23729-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="23729-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="23729-125">Geri yükleme-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="23729-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="23729-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="23729-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="23729-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="23729-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="23729-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="23729-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="23729-129">Bul-DscResource</span><span class="sxs-lookup"><span data-stu-id="23729-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="23729-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="23729-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="23729-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="23729-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="23729-132">Yapılandırmaları derleme (bkz [DSC yapılandırmaları](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="23729-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="23729-133">**Sorun:** Parola şifrelemesini (bkz [MOF dosyasının güvenliğini sağlama](../pull-server/secureMOF.md)) derleme yapılandırması sırasında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="23729-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="23729-134">Metaconfigurations derleme (bkz [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="23729-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="23729-135">Kullanıcı bağlamı altında bir kaynak çalıştıran (bkz [kullanıcı kimlik bilgilerini (Farklı Çalıştır) ile çalışan DSC](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="23729-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="23729-136">Sınıf tabanlı kaynaklar (bkz [PowerShell sınıfları ile özel bir DSC kaynağı yazma](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="23729-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="23729-137">DSC kaynakları hata ayıklama (bkz [hata ayıklama DSC kaynakları](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="23729-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="23729-138">**Sorun:** Bir kaynak PsDscRunAsCredential kullanıyorsa, işe yaramazsa (bkz [DSC çalıştıran kullanıcı kimlik bilgileriyle](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="23729-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="23729-139">Çapraz düğüm bağımlılıklarını belirtme</span><span class="sxs-lookup"><span data-stu-id="23729-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="23729-140">Kaynak sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="23729-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="23729-141">Çekme istemcisi (yapılandırmaları ve kaynakları) (bkz [yapılandırma adlarını kullanarak çekme istemcisi ayarlama](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="23729-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="23729-142">Kısmi yapılandırmalar (çekme ve itme)</span><span class="sxs-lookup"><span data-stu-id="23729-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="23729-143">Çekme sunucusuna raporlama</span><span class="sxs-lookup"><span data-stu-id="23729-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="23729-144">MOF şifreleme</span><span class="sxs-lookup"><span data-stu-id="23729-144">MOF encryption</span></span>

- <span data-ttu-id="23729-145">Olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="23729-145">Event logging</span></span>

- <span data-ttu-id="23729-146">Azure Automation DSC raporlama</span><span class="sxs-lookup"><span data-stu-id="23729-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="23729-147">Tamamen işlevseldir, kaynakları</span><span class="sxs-lookup"><span data-stu-id="23729-147">Resources that are fully functional</span></span>

- <span data-ttu-id="23729-148">**Arşiv**</span><span class="sxs-lookup"><span data-stu-id="23729-148">**Archive**</span></span>
- <span data-ttu-id="23729-149">**Ortam**</span><span class="sxs-lookup"><span data-stu-id="23729-149">**Environment**</span></span>
- <span data-ttu-id="23729-150">**Dosya**</span><span class="sxs-lookup"><span data-stu-id="23729-150">**File**</span></span>
- <span data-ttu-id="23729-151">**Günlük**</span><span class="sxs-lookup"><span data-stu-id="23729-151">**Log**</span></span>
- <span data-ttu-id="23729-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="23729-152">**ProcessSet**</span></span>
- <span data-ttu-id="23729-153">**Kayıt defteri**</span><span class="sxs-lookup"><span data-stu-id="23729-153">**Registry**</span></span>
- <span data-ttu-id="23729-154">**Komut Dosyası**</span><span class="sxs-lookup"><span data-stu-id="23729-154">**Script**</span></span>
- <span data-ttu-id="23729-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="23729-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="23729-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="23729-156">**WindowsProcess**</span></span>
- <span data-ttu-id="23729-157">**WaitForAll** (bkz [çapraz düğüm bağımlılıklarını belirtme](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="23729-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="23729-158">**WaitForAny** (bkz [çapraz düğüm bağımlılıklarını belirtme](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="23729-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="23729-159">**WaitForSome** (bkz [çapraz düğüm bağımlılıklarını belirtme](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="23729-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="23729-160">Kısmen işlevsel olan kaynaklar</span><span class="sxs-lookup"><span data-stu-id="23729-160">Resources that are partially functional</span></span>
- <span data-ttu-id="23729-161">**Grup**</span><span class="sxs-lookup"><span data-stu-id="23729-161">**Group**</span></span>
- <span data-ttu-id="23729-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="23729-162">**GroupSet**</span></span>

  <span data-ttu-id="23729-163">**Sorun:** Belirli bir örneği iki kez çağrılırsa üzerinde kaynak başarısız (aynı yapılandırmanın iki kez çalıştıran)</span><span class="sxs-lookup"><span data-stu-id="23729-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="23729-164">**Hizmet**</span><span class="sxs-lookup"><span data-stu-id="23729-164">**Service**</span></span>
- <span data-ttu-id="23729-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="23729-165">**ServiceSet**</span></span>

  <span data-ttu-id="23729-166">**Sorun:** Yalnızca çalışır (durum) hizmeti başlatma/durdurma.</span><span class="sxs-lookup"><span data-stu-id="23729-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="23729-167">Bir başlangıç türü, kimlik bilgileri, açıklama vb. gibi diğer hizmet öznitelikleri değiştirmeye çalışırsa başarısız..</span><span class="sxs-lookup"><span data-stu-id="23729-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="23729-168">Söz konusu hata benzer:</span><span class="sxs-lookup"><span data-stu-id="23729-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="23729-169">*[Management.managementobject] türü bulunamıyor: Bu tür içeren derlemenin yüklü olduğundan emin olun.*</span><span class="sxs-lookup"><span data-stu-id="23729-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="23729-170">İşlevsel olmayan kaynaklar</span><span class="sxs-lookup"><span data-stu-id="23729-170">Resources that are not functional</span></span>
- <span data-ttu-id="23729-171">**Kullanıcı**</span><span class="sxs-lookup"><span data-stu-id="23729-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="23729-172">DSC özelliklerini Nano Sunucu'da kullanılabilir değil</span><span class="sxs-lookup"><span data-stu-id="23729-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="23729-173">Şu DSC özellikler şu anda Nano Sunucu'da kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="23729-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="23729-174">MOF belgesi şifrelenmiş parolası ile şifre çözme</span><span class="sxs-lookup"><span data-stu-id="23729-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="23729-175">Çekme sunucusu--şu anda Nano Sunucu'da bir çekme sunucusu ayarlayamazsınız</span><span class="sxs-lookup"><span data-stu-id="23729-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="23729-176">Özellik works listesinde değil herhangi bir şey</span><span class="sxs-lookup"><span data-stu-id="23729-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="23729-177">Nano Sunucu'da özel DSC kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="23729-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="23729-178">Windows API'ları ve kitaplıkları CLR Nano Sunucu'da kullanılabilir sınırlı kümesi nedeniyle Windows tam CLR sürümü üzerinde çalışan DSC kaynakları, Nano Sunucu'da çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="23729-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="23729-179">Uçtan uca DSC özel kaynaklar herhangi bir üretim ortamına dağıtmadan önce test tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="23729-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="23729-180">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="23729-180">See Also</span></span>

- [<span data-ttu-id="23729-181">Nano Server ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="23729-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
