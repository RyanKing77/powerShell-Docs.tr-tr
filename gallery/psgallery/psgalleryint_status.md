---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgalleryint_status
ms.openlocfilehash: 4f7d300bb07fcbdb100c2fb029f8f66ab260fe7a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="6d1c6-103">PowerShell Galerisi durumu</span><span class="sxs-lookup"><span data-stu-id="6d1c6-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="6d1c6-104">03/27/2017 - ÇÖZÜMLENDİ: tek tek modülü ve komut dosyası sayfalarında Görülemedi</span><span class="sxs-lookup"><span data-stu-id="6d1c6-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="6d1c6-105">__Özet etkisi__: doğrudan bağlantılar ayrı ayrı modülü ve komut dosyası sayfalara https://www.powershellgallery.com bozulur.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="6d1c6-106">Bu bölgeler arasında raporlandığını.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-106">This was being reported across all the regions.</span></span> <span data-ttu-id="6d1c6-107">Bu PowerShellGet cmdlet'lerinden herhangi birini IE etkisi olmuştur değil., yükleme betiği, Update-modülü, Update-komut dosyası, yayımlama-Module Yayımla-komut dosyası yükleme-Module devam çalışmak.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="6d1c6-108">__Kök neden__: mühendisleri neden sayfaya düğmeleri gibi Facebook sosyal medya getiren bir sorun olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="6d1c6-109">__Çözümleme__: mühendisleri Facebook sayımı bilgilerini devre dışı bırakarak sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="6d1c6-110">__Sonraki adımlar__: biz Facebook API'si bizim kullanımını düzeltmek için bir iç izleme sorunu açılır.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="6d1c6-111">12/15/2016 - PowerShellGallery Web sitesi aracılığıyla e-posta gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="6d1c6-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="6d1c6-112">__Özet etkisi__: 13/12/2016 ile 15/12/2016 arasında kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye gönderilen iletiler PowerShell Galerisi yöneticileri tarafından alınmadı.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="6d1c6-113">__Kök neden__: mühendisleri bir kimlik doğrulama sorunu nedeni SMTP sunucusu ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="6d1c6-114">__Çözümleme__: mühendisleri kimlik doğrulama sorunu çözün ve SMTP sunucusuna bağlantı geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="6d1c6-115">__Sonraki adımlar__: ileti göndermek için kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye bağlantılar kullandıysanız cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="6d1c6-116">Verdiğimiz rahatsızlıktan dolayı özür dileriz.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-116">We apologize for the inconvenience.</span></span>


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="6d1c6-117">8/10/2016 - çözümlendi: e-postalar için gönderilemedi cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="6d1c6-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="6d1c6-118">__Özet etkisi__: 8/5/2016 ile 8/10/2016 arasında müşteriler için e-posta gönderemiyor cgadmin@microsoft.com, ya da bize özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="6d1c6-119">__Kök neden__: mühendisleri tanımlanan neden e-posta hesabı bir yapılandırma değişikliği.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="6d1c6-120">__Çözümleme__: mühendisleri çalışılan yapılandırma sorunu gidermek için.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="6d1c6-121">__Sonraki adımlar__: bize bağlantı kullanılan veya posta gönderilen cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="6d1c6-122">Anlayışınız için teşekkür ederiz.</span><span class="sxs-lookup"><span data-stu-id="6d1c6-122">Thank you for your patience.</span></span>