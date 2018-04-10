---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Nano Server’da DSC Kullanma
ms.openlocfilehash: 9ebc1f046893c360538009b5ecbcfb6456f92bbb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="4c9a8-103">Nano Server’da DSC Kullanma</span><span class="sxs-lookup"><span data-stu-id="4c9a8-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="4c9a8-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4c9a8-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4c9a8-105">**DSC Nano Server üzerinde** isteğe bağlı bir pakette `NanoServer\Packages` klasörü Windows Server 2016 medya.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="4c9a8-106">Belirterek Nano Server için bir VHD oluşturduğunuzda paket yüklenebilir **Microsoft NanoServer DSC paket** değeri olarak **paketleri** parametresinin **yeni NanoServerImage**  işlevi.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="4c9a8-107">Örneğin, bir sanal makineye ait bir VHD'ye oluşturuyorsanız, komut aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="4c9a8-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="4c9a8-108">Yükleme ve PowerShell uzaktan iletişimi Nano Server yönetme yanı sıra, Nano Server kullanma hakkında daha fazla bilgi için bkz: [Nano Server ile çalışmaya başlama](https://technet.microsoft.com/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="4c9a8-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="4c9a8-109">DSC özellikleri Nano Server üzerinde kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="4c9a8-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="4c9a8-110">Nano Server yalnızca sınırlı sayıda tam bir Windows Server sürümüne karşılaştırıldığında API'leri desteklediğinden, DSC Nano Server üzerinde tam işlevsel eşlik şimdilik tam SKU'ları üzerinde çalışan DSC ile yok.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="4c9a8-111">DSC Nano Server üzerinde etkin geliştirme ve henüz tam özelliği değil.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

 <span data-ttu-id="4c9a8-112">Şu DSC özellikleri Nano Server üzerinde şu anda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4c9a8-112">The following DSC features are currently available on Nano Server:</span></span>


* <span data-ttu-id="4c9a8-113">Hem İtme hem de çekme modları</span><span class="sxs-lookup"><span data-stu-id="4c9a8-113">Both push and pull modes</span></span>

* <span data-ttu-id="4c9a8-114">Windows Server, aşağıdakiler dahil tam bir sürümünü mevcut tüm DSC cmdlet:</span><span class="sxs-lookup"><span data-stu-id="4c9a8-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
  * [<span data-ttu-id="4c9a8-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4c9a8-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="4c9a8-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4c9a8-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)
  * [<span data-ttu-id="4c9a8-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="4c9a8-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="4c9a8-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="4c9a8-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [<span data-ttu-id="4c9a8-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c9a8-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="4c9a8-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c9a8-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="4c9a8-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c9a8-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="4c9a8-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c9a8-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [<span data-ttu-id="4c9a8-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="4c9a8-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [<span data-ttu-id="4c9a8-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c9a8-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="4c9a8-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c9a8-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="4c9a8-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="4c9a8-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="4c9a8-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="4c9a8-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="4c9a8-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="4c9a8-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="4c9a8-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="4c9a8-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="4c9a8-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="4c9a8-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="4c9a8-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="4c9a8-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* <span data-ttu-id="4c9a8-132">Derleme yapılandırmaları (bkz [DSC yapılandırmaları](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="4c9a8-133">**Sorun:** parola şifreleme (bkz [MOF dosyası güvenli hale getirme](securemof.md)) yapılandırması sırasında derleme çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="4c9a8-134">Metaconfigurations derleme (bkz [yerel Configuration Manager Yapılandırma](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="4c9a8-135">Bir kaynak kullanıcı bağlamında çalışan (bkz [kullanıcı kimlik bilgileri (Farklı Çalıştır) ile çalışan DSC](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="4c9a8-136">Sınıf tabanlı kaynaklar (bkz [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="4c9a8-137">DSC kaynakları, hata ayıklama (bkz [hata ayıklama DSC kaynakları](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>

  <span data-ttu-id="4c9a8-138">**Sorun:** kaynak PsDscRunAsCredential kullanıyorsa, işe yaramazsa (bkz [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="4c9a8-139">Çapraz düğüm bağımlılıklarını belirtme</span><span class="sxs-lookup"><span data-stu-id="4c9a8-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md)

* [<span data-ttu-id="4c9a8-140">Kaynak sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c9a8-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="4c9a8-141">Çekme istemci (yapılandırmaları ve kaynakları) (bkz [yapılandırma adları kullanarak bir çekme istemcisi kurarken](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="4c9a8-142">Kısmi yapılandırmaları (çekme ve itme)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="4c9a8-143">Çekme sunucusuna raporlama</span><span class="sxs-lookup"><span data-stu-id="4c9a8-143">Reporting to pull server</span></span>](reportServer.md)

* <span data-ttu-id="4c9a8-144">MOF şifreleme</span><span class="sxs-lookup"><span data-stu-id="4c9a8-144">MOF encryption</span></span>

* <span data-ttu-id="4c9a8-145">Olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="4c9a8-145">Event logging</span></span>

* <span data-ttu-id="4c9a8-146">Azure Otomasyonu DSC raporlama</span><span class="sxs-lookup"><span data-stu-id="4c9a8-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="4c9a8-147">Tam olarak işlevsel kaynakları</span><span class="sxs-lookup"><span data-stu-id="4c9a8-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="4c9a8-148">Arşiv</span><span class="sxs-lookup"><span data-stu-id="4c9a8-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="4c9a8-149">Ortamı</span><span class="sxs-lookup"><span data-stu-id="4c9a8-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="4c9a8-150">Dosya</span><span class="sxs-lookup"><span data-stu-id="4c9a8-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="4c9a8-151">Log</span><span class="sxs-lookup"><span data-stu-id="4c9a8-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="4c9a8-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="4c9a8-152">ProcessSet</span></span>
  * [<span data-ttu-id="4c9a8-153">Kayıt defteri</span><span class="sxs-lookup"><span data-stu-id="4c9a8-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="4c9a8-154">Script</span><span class="sxs-lookup"><span data-stu-id="4c9a8-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="4c9a8-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="4c9a8-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="4c9a8-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="4c9a8-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="4c9a8-157">WaitForAll (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="4c9a8-158">WaitForAny (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="4c9a8-159">WaitForSome (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="4c9a8-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="4c9a8-160">Kısmen işlev kaynakları</span><span class="sxs-lookup"><span data-stu-id="4c9a8-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="4c9a8-161">Grup</span><span class="sxs-lookup"><span data-stu-id="4c9a8-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="4c9a8-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="4c9a8-162">GroupSet</span></span>

  <span data-ttu-id="4c9a8-163">**Sorun:** kaynaklar başarısız belirli örneği iki kez çağrıldıysa (aynı yapılandırmayı iki kez çalışan)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  * [<span data-ttu-id="4c9a8-164">Hizmeti</span><span class="sxs-lookup"><span data-stu-id="4c9a8-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="4c9a8-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="4c9a8-165">ServiceSet</span></span>

  <span data-ttu-id="4c9a8-166">**Sorun:** yalnızca çalışır (durum) hizmeti başlatma/durdurma.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="4c9a8-167">Başarısız bir startuptype, kimlik bilgileri, açıklama vb. gibi diğer hizmeti öznitelikleri değiştirmeye çalışırsa..</span><span class="sxs-lookup"><span data-stu-id="4c9a8-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="4c9a8-168">Oluşturulan hata benzer:</span><span class="sxs-lookup"><span data-stu-id="4c9a8-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="4c9a8-169">*Türü [management.managementobject] bulunamıyor: Bu türü içeren derlemenin yüklü olduğunu doğrulayın.*</span><span class="sxs-lookup"><span data-stu-id="4c9a8-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

* <span data-ttu-id="4c9a8-170">İşlev olmayan kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4c9a8-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="4c9a8-171">Kullanıcı</span><span class="sxs-lookup"><span data-stu-id="4c9a8-171">User</span></span>](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="4c9a8-172">DSC özellikleri Nano sunucuda mevcut değil</span><span class="sxs-lookup"><span data-stu-id="4c9a8-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="4c9a8-173">Şu DSC özellikleri Nano Server üzerinde şu anda kullanılabilir değil:</span><span class="sxs-lookup"><span data-stu-id="4c9a8-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="4c9a8-174">Şifrelenmiş parolası MOF belgeyle şifre çözme</span><span class="sxs-lookup"><span data-stu-id="4c9a8-174">Decrypting MOF document with encrypted password(s)</span></span>
* <span data-ttu-id="4c9a8-175">Çekme sunucusuna--şu anda Nano Server çekme sunucusunda ayarlayamazsınız</span><span class="sxs-lookup"><span data-stu-id="4c9a8-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="4c9a8-176">Özellik works listede olmayan herhangi bir şey</span><span class="sxs-lookup"><span data-stu-id="4c9a8-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="4c9a8-177">Nano sunucusunda özel DSC kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="4c9a8-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="4c9a8-178">Windows API'ları ve CLR kitaplıkları Nano Server üzerinde kullanılabilir sınırlı bir kümelerini nedeniyle Windows tam CLR sürümü üzerinde çalışan DSC kaynakları, Nano Server üzerinde çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="4c9a8-179">DSC özel kaynakları üretim ortamına dağıtmadan önce uçtan uca test tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c9a8-180">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4c9a8-180">See Also</span></span>
- [<span data-ttu-id="4c9a8-181">Nano Server ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="4c9a8-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/library/mt126167.aspx)