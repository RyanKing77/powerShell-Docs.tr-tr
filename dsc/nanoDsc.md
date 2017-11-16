---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: DSC Nano sunucusunda kullanma
ms.openlocfilehash: 2233106bfd07144132f95ea7957ebfa3248ca219
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="adef5-103">DSC Nano sunucusunda kullanma</span><span class="sxs-lookup"><span data-stu-id="adef5-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="adef5-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="adef5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="adef5-105">**DSC Nano Server üzerinde** isteğe bağlı bir pakette `NanoServer\Packages` klasörü Windows Server 2016 medya.</span><span class="sxs-lookup"><span data-stu-id="adef5-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="adef5-106">Belirterek Nano Server için bir VHD oluşturduğunuzda paket yüklenebilir **Microsoft NanoServer DSC paket** değeri olarak **paketleri** parametresinin **yeni NanoServerImage**  işlevi.</span><span class="sxs-lookup"><span data-stu-id="adef5-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="adef5-107">Örneğin, bir sanal makineye ait bir VHD'ye oluşturuyorsanız, komut aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="adef5-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="adef5-108">Yükleme ve PowerShell uzaktan iletişimi Nano Server yönetme yanı sıra, Nano Server kullanma hakkında daha fazla bilgi için bkz: [Nano Server ile çalışmaya başlama](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="adef5-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="adef5-109">DSC özellikleri Nano Server üzerinde kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="adef5-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="adef5-110">Nano Server yalnızca sınırlı sayıda tam bir Windows Server sürümüne karşılaştırıldığında API'leri desteklediğinden, DSC Nano Server üzerinde tam işlevsel eşlik şimdilik tam SKU'ları üzerinde çalışan DSC ile yok.</span><span class="sxs-lookup"><span data-stu-id="adef5-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="adef5-111">DSC Nano Server üzerinde etkin geliştirme ve henüz tam özelliği değil.</span><span class="sxs-lookup"><span data-stu-id="adef5-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>
 
 <span data-ttu-id="adef5-112">Şu DSC özellikleri Nano Server üzerinde şu anda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="adef5-112">The following DSC features are currently available on Nano Server:</span></span> 


* <span data-ttu-id="adef5-113">Hem İtme hem de çekme modları</span><span class="sxs-lookup"><span data-stu-id="adef5-113">Both push and pull modes</span></span>

* <span data-ttu-id="adef5-114">Windows Server, aşağıdakiler dahil tam bir sürümünü mevcut tüm DSC cmdlet:</span><span class="sxs-lookup"><span data-stu-id="adef5-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span> 
  * [<span data-ttu-id="adef5-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="adef5-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [<span data-ttu-id="adef5-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="adef5-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [<span data-ttu-id="adef5-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="adef5-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="adef5-118">DscDebug devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="adef5-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [<span data-ttu-id="adef5-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="adef5-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="adef5-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="adef5-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="adef5-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="adef5-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="adef5-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="adef5-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [<span data-ttu-id="adef5-123">Yayımlama DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="adef5-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [<span data-ttu-id="adef5-124">Güncelleştirme DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="adef5-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="adef5-125">Geri yükleme DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="adef5-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="adef5-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="adef5-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="adef5-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="adef5-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="adef5-128">Çağırma DscResource</span><span class="sxs-lookup"><span data-stu-id="adef5-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="adef5-129">Bul DscResource</span><span class="sxs-lookup"><span data-stu-id="adef5-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="adef5-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="adef5-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="adef5-131">DscChecksum yeni</span><span class="sxs-lookup"><span data-stu-id="adef5-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* <span data-ttu-id="adef5-132">Derleme yapılandırmaları (bkz [DSC yapılandırmaları](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="adef5-133">**Sorun:** parola şifreleme (bkz [MOF dosyası güvenli hale getirme](securemof.md)) yapılandırması sırasında derleme çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="adef5-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="adef5-134">Metaconfigurations derleme (bkz [yerel Configuration Manager Yapılandırma](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="adef5-135">Bir kaynak kullanıcı bağlamında çalışan (bkz [kullanıcı kimlik bilgileri (Farklı Çalıştır) ile çalışan DSC](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="adef5-136">Sınıf tabanlı kaynaklar (bkz [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="adef5-137">DSC kaynakları, hata ayıklama (bkz [hata ayıklama DSC kaynakları](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>
  
  <span data-ttu-id="adef5-138">**Sorun:** kaynak PsDscRunAsCredential kullanıyorsa, işe yaramazsa (bkz [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="adef5-139">Geçici bir düğüm bağımlılıkları belirtme</span><span class="sxs-lookup"><span data-stu-id="adef5-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md) 

* [<span data-ttu-id="adef5-140">Kaynak sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="adef5-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="adef5-141">Çekme istemci (yapılandırmaları ve kaynakları) (bkz [yapılandırma adları kullanarak bir çekme istemcisi kurarken](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="adef5-142">Kısmi yapılandırmaları (çekme ve itme)</span><span class="sxs-lookup"><span data-stu-id="adef5-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="adef5-143">Çekme sunucusuna raporlama</span><span class="sxs-lookup"><span data-stu-id="adef5-143">Reporting to pull server</span></span>](reportServer.md) 

* <span data-ttu-id="adef5-144">MOF şifreleme</span><span class="sxs-lookup"><span data-stu-id="adef5-144">MOF encryption</span></span>

* <span data-ttu-id="adef5-145">Olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="adef5-145">Event logging</span></span>

* <span data-ttu-id="adef5-146">Azure Otomasyonu DSC raporlama</span><span class="sxs-lookup"><span data-stu-id="adef5-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="adef5-147">Tam olarak işlevsel kaynakları</span><span class="sxs-lookup"><span data-stu-id="adef5-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="adef5-148">Arşiv</span><span class="sxs-lookup"><span data-stu-id="adef5-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="adef5-149">Ortamı</span><span class="sxs-lookup"><span data-stu-id="adef5-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="adef5-150">Dosya</span><span class="sxs-lookup"><span data-stu-id="adef5-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="adef5-151">Günlük</span><span class="sxs-lookup"><span data-stu-id="adef5-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="adef5-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="adef5-152">ProcessSet</span></span>
  * [<span data-ttu-id="adef5-153">Kayıt defteri</span><span class="sxs-lookup"><span data-stu-id="adef5-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="adef5-154">Komut dosyası</span><span class="sxs-lookup"><span data-stu-id="adef5-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="adef5-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="adef5-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="adef5-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="adef5-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="adef5-157">WaitForAll (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="adef5-158">WaitForAny (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="adef5-159">WaitForSome (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="adef5-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="adef5-160">Kısmen işlev kaynakları</span><span class="sxs-lookup"><span data-stu-id="adef5-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="adef5-161">Grup</span><span class="sxs-lookup"><span data-stu-id="adef5-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="adef5-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="adef5-162">GroupSet</span></span>
  
  <span data-ttu-id="adef5-163">**Sorun:** kaynaklar başarısız belirli örneği iki kez çağrıldıysa (aynı yapılandırmayı iki kez çalışan)</span><span class="sxs-lookup"><span data-stu-id="adef5-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>
  
  * [<span data-ttu-id="adef5-164">Hizmeti</span><span class="sxs-lookup"><span data-stu-id="adef5-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="adef5-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="adef5-165">ServiceSet</span></span>
  
  <span data-ttu-id="adef5-166">**Sorun:** yalnızca çalışır (durum) hizmeti başlatma/durdurma.</span><span class="sxs-lookup"><span data-stu-id="adef5-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="adef5-167">Başarısız bir startuptype, kimlik bilgileri, açıklama vb. gibi diğer hizmeti öznitelikleri değiştirmeye çalışırsa..</span><span class="sxs-lookup"><span data-stu-id="adef5-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="adef5-168">Oluşturulan hata benzer:</span><span class="sxs-lookup"><span data-stu-id="adef5-168">The error thrown is similar to:</span></span>
  
  <span data-ttu-id="adef5-169">*Türü [management.managementobject] bulunamıyor: Bu türü içeren derlemenin yüklü olduğunu doğrulayın.*</span><span class="sxs-lookup"><span data-stu-id="adef5-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>
  
* <span data-ttu-id="adef5-170">İşlev olmayan kaynaklar</span><span class="sxs-lookup"><span data-stu-id="adef5-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="adef5-171">Kullanıcı</span><span class="sxs-lookup"><span data-stu-id="adef5-171">User</span></span>](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="adef5-172">DSC özellikleri Nano sunucuda mevcut değil</span><span class="sxs-lookup"><span data-stu-id="adef5-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="adef5-173">Şu DSC özellikleri Nano Server üzerinde şu anda kullanılabilir değil:</span><span class="sxs-lookup"><span data-stu-id="adef5-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="adef5-174">Şifrelenmiş parolası MOF belgeyle şifre çözme</span><span class="sxs-lookup"><span data-stu-id="adef5-174">Decrypting MOF document with encrypted password(s)</span></span> 
* <span data-ttu-id="adef5-175">Çekme sunucusuna--şu anda Nano Server çekme sunucusunda ayarlayamazsınız</span><span class="sxs-lookup"><span data-stu-id="adef5-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="adef5-176">Özellik works listede olmayan herhangi bir şey</span><span class="sxs-lookup"><span data-stu-id="adef5-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="adef5-177">Nano sunucusunda özel DSC kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="adef5-177">Using custom DSC resources on Nano Server</span></span>
 
<span data-ttu-id="adef5-178">Windows API'ları ve CLR kitaplıkları Nano Server üzerinde kullanılabilir sınırlı bir kümelerini nedeniyle Windows tam CLR sürümü üzerinde çalışan DSC kaynakları, Nano Server üzerinde çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="adef5-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span> <span data-ttu-id="adef5-179">DSC özel kaynakları üretim ortamına dağıtmadan önce uçtan uca test tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="adef5-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="adef5-180">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="adef5-180">See Also</span></span>
- [<span data-ttu-id="adef5-181">Nano Server ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="adef5-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/en-us/library/mt126167.aspx)

