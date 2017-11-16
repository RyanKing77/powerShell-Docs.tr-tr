---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="c135b-103">PowerShell Galerisi durumu</span><span class="sxs-lookup"><span data-stu-id="c135b-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="c135b-104">10/10/2017-2 saat kullanılamaz PowerShell Galerisi 10/10/17</span><span class="sxs-lookup"><span data-stu-id="c135b-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="c135b-105">__Özet etkisi__: PowerShell Galerisi aralıklı bağlantısı sorunları yaklaşık 5 pm (saati) itibaren kaynaklanan bir süre çok yüksek gecikme yaşadı 10/10/17.</span><span class="sxs-lookup"><span data-stu-id="c135b-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="c135b-106">Sorunu çözerken, site için yaklaşık 10 pm (saati) başlangıç 2 saat çevrimdışı duruma.</span><span class="sxs-lookup"><span data-stu-id="c135b-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="c135b-107">Site gece yarısından kısa süre önce geri 10/10/2017.</span><span class="sxs-lookup"><span data-stu-id="c135b-107">The site was restored shortly before midnight 10/10/2017.</span></span> 
 
<span data-ttu-id="c135b-108">__Kök neden__: yüksek gecikme kök nedenini hala incelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c135b-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="c135b-109">__Çözümleme__: web hizmetleri çevrimdışına gerekiyordu ve birincil sorunu gidermek için geri.</span><span class="sxs-lookup"><span data-stu-id="c135b-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span> 

<span data-ttu-id="c135b-110">__Sonraki adımlar__: özgün sorunun kök nedeni incelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c135b-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="c135b-111">Azure Automation şu anda kullanılabilir 06/01/2017-'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="c135b-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="c135b-112">__Özet etkisi__: bağımlılıkları olan öğeleri için Azure Otomasyonu PowerShell Galerisi'nden dağıtma şu anda kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c135b-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="c135b-113">PowerShell Galerisi'nden öğeleri içeri aktarma içinde Azure Otomasyonu hala kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="c135b-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="c135b-114">__Kök nedeni__: bazılarında bağımlılıklara sahip ve Azure otomasyonu için daha önce dağıtmış olan öğeleri için Azure Otomasyonu değil dağıtılacak.</span><span class="sxs-lookup"><span data-stu-id="c135b-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="c135b-115">Mühendisleri nasıl ARM şablonlarını öğeleri için bağımlılıkları olan Azure Otomasyonu işlevine dağıtma için oluşturulan ile ilgili bir sorun tanımladınız.</span><span class="sxs-lookup"><span data-stu-id="c135b-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="c135b-116">__Çözümleme__: mühendisleri sorunu gidermek için çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="c135b-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="c135b-117">PowerShell Galerisi'nden öğe aktarmak için kullanıcılar için geçerli geçici çözümü olan Azure Otomasyonu içinde.</span><span class="sxs-lookup"><span data-stu-id="c135b-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="c135b-118">__Sonraki adımlar__: mühendisleri yayın düzeltme kısa süre içinde.</span><span class="sxs-lookup"><span data-stu-id="c135b-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="c135b-119">Bu arada, önerilen geçici çözüm Lütfen kullanın.</span><span class="sxs-lookup"><span data-stu-id="c135b-119">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="c135b-120">11/04/2017 - kullanıcıların Azure Active Directory (AAD) hesaplarıyla oturum oturum açamıyor</span><span class="sxs-lookup"><span data-stu-id="c135b-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="c135b-121">__Özet etkisi__: Azure AD hesapları kullanan bazı kullanıcılar için PowerShell Galerisi oturum açamıyor.</span><span class="sxs-lookup"><span data-stu-id="c135b-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="c135b-122">__Kök nedeni__: daha güvenli bir şekilde AAD ile etkileşim kurmak için bir güncelleştirme sırasında bir ayar değişikliğinin eksik.</span><span class="sxs-lookup"><span data-stu-id="c135b-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="c135b-123">Dağıtım proceeded şekilde değişikliğini doğrulamak için yapılan sınama, AAD hesaplarının, belirli türde içermiyordu.</span><span class="sxs-lookup"><span data-stu-id="c135b-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="c135b-124">__Çözümleme__: mühendisleri eksik ayarı tanımlanır ve sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c135b-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="c135b-125">__Sonraki adımlar__: biz bizim AAD hesap türleri için daha geniş bir dizi dahil etmek için test değiştirme.</span><span class="sxs-lookup"><span data-stu-id="c135b-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="c135b-126">03/27/2017 - ÇÖZÜMLENDİ: tek tek modülü ve komut dosyası sayfalarında Görülemedi</span><span class="sxs-lookup"><span data-stu-id="c135b-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="c135b-127">__Özet etkisi__: https://www.powershellgallery.com üzerinde tek tek modülü ve komut dosyası sayfalarına bağlantılar bozuk doğrudan.</span><span class="sxs-lookup"><span data-stu-id="c135b-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="c135b-128">Bu bölgeler arasında raporlandığını.</span><span class="sxs-lookup"><span data-stu-id="c135b-128">This was being reported across all the regions.</span></span> <span data-ttu-id="c135b-129">Bu PowerShellGet cmdlet'lerinden herhangi birini IE etkisi olmuştur değil., Install-Module, yükleme betiği, Update-modülü, Update-komut dosyası, yayımlama-Module Yayımla-Scirpt devam çalışmak.</span><span class="sxs-lookup"><span data-stu-id="c135b-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="c135b-130">__Kök neden__: mühendisleri neden sayfaya düğmeleri gibi Facebook sosyal medya getiren bir sorun olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c135b-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="c135b-131">__Çözümleme__: mühendisleri Facebook sayımı bilgilerini devre dışı bırakarak sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c135b-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="c135b-132">__Sonraki adımlar__: biz Facebook API'si bizim kullanımını düzeltmek için bir iç izleme sorunu açılır.</span><span class="sxs-lookup"><span data-stu-id="c135b-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="c135b-133">12/15/2016 - PowerShellGallery Web sitesi aracılığıyla e-posta gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="c135b-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="c135b-134">__Özet etkisi__: 13/12/2016 ile 15/12/2016 arasında kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye gönderilen iletiler PowerShell Galerisi yöneticileri tarafından alınmadı.</span><span class="sxs-lookup"><span data-stu-id="c135b-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="c135b-135">__Kök neden__: mühendisleri bir kimlik doğrulama sorunu nedeni SMTP sunucusu ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c135b-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="c135b-136">__Çözümleme__: mühendisleri kimlik doğrulama sorunu çözün ve SMTP sunucusuna bağlantı geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c135b-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="c135b-137">__Sonraki adımlar__: ileti göndermek için kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye bağlantılar kullandıysanız cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="c135b-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="c135b-138">Verdiğimiz rahatsızlıktan dolayı özür dileriz.</span><span class="sxs-lookup"><span data-stu-id="c135b-138">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="c135b-139">8/10/2016 - çözümlendi: e-postalar için gönderilemedicgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="c135b-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="c135b-140">__Özet etkisi__: 8/5/2016 ile 8/10/2016 arasında müşteriler için e-posta gönderemiyor cgadmin@microsoft.com, ya da bize özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c135b-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="c135b-141">__Kök neden__: mühendisleri tanımlanan neden e-posta hesabı bir yapılandırma değişikliği.</span><span class="sxs-lookup"><span data-stu-id="c135b-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="c135b-142">__Çözümleme__: mühendisleri çalışılan yapılandırma sorunu gidermek için.</span><span class="sxs-lookup"><span data-stu-id="c135b-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="c135b-143">__Sonraki adımlar__: bize bağlantı kullanılan veya posta gönderilen cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="c135b-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="c135b-144">Anlayışınız için teşekkür ederiz.</span><span class="sxs-lookup"><span data-stu-id="c135b-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="c135b-145">Başarısız olan öğe 7/13/2016 - indirin</span><span class="sxs-lookup"><span data-stu-id="c135b-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="c135b-146">__Özet etkisi__: 11/7/2016 ile 13/7/2016 arasında bir alt kümesini müşteriler PowerShell Galerisi'nden öğe indirme sorunları yaşadı.</span><span class="sxs-lookup"><span data-stu-id="c135b-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="c135b-147">Olası sorun kendisini yükleme Modül/yükleme betiği ve kaydetme modülü/Kaydet betiği döndürülen aşağıdaki hata iletisini bildirilmiş:</span><span class="sxs-lookup"><span data-stu-id="c135b-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="c135b-148">__Ön kök nedeni__: mühendisleri ile Azure içerik teslim ağı (PowerShell Galerisi 11/7/2016 tarihinde dağıtmış CDN), bir sorun tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="c135b-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="c135b-149">__Azaltma__: mühendisleri Azure CDN PowerShell galerisinde devre dışı.</span><span class="sxs-lookup"><span data-stu-id="c135b-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="c135b-150">__Sonraki adımlar__: temel alınan kök nedeni araştırın ve gelecekteki oluşumları önlemek için bir çözüm geliştirme.</span><span class="sxs-lookup"><span data-stu-id="c135b-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="c135b-151">Başarısız olan öğe sayısı 5/19/2016 - indirin</span><span class="sxs-lookup"><span data-stu-id="c135b-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="c135b-152">__Özet etkisi__: bir alt kümesini müşteriler 17/5/2016 ve 5/19/2016 arasında PowerShell Galerisi'nden öğe indirme sorunları yaşadı.</span><span class="sxs-lookup"><span data-stu-id="c135b-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="c135b-153">Olası sorun kendisini yükleme Modül/yükleme betiği ve kaydetme modülü/Kaydet betiği döndürülen aşağıdaki hata iletisini bildirilmiş:</span><span class="sxs-lookup"><span data-stu-id="c135b-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="c135b-154">__Ön kök nedeni__: mühendisleri kesinti, Azure içerik teslim ağı (PowerShell Galerisi 17/5/2016 tarihinde dağıtmış CDN), temel alınan sağlayıcı olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c135b-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="c135b-155">__Azaltma__: mühendisleri Azure CDN PowerShell galerisinde devre dışı.</span><span class="sxs-lookup"><span data-stu-id="c135b-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="c135b-156">__Sonraki adımlar__: temel alınan kök nedeni araştırın ve gelecekteki oluşumları önlemek için bir çözüm geliştirme.</span><span class="sxs-lookup"><span data-stu-id="c135b-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

