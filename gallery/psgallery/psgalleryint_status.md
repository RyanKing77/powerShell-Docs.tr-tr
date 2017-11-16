---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="5bec0-103">PowerShell Galerisi durumu</span><span class="sxs-lookup"><span data-stu-id="5bec0-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="5bec0-104">03/27/2017 - ÇÖZÜMLENDİ: tek tek modülü ve komut dosyası sayfalarında Görülemedi</span><span class="sxs-lookup"><span data-stu-id="5bec0-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="5bec0-105">__Özet etkisi__: https://www.powershellgallery.com üzerinde tek tek modülü ve komut dosyası sayfalarına bağlantılar bozuk doğrudan.</span><span class="sxs-lookup"><span data-stu-id="5bec0-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="5bec0-106">Bu bölgeler arasında raporlandığını.</span><span class="sxs-lookup"><span data-stu-id="5bec0-106">This was being reported across all the regions.</span></span> <span data-ttu-id="5bec0-107">Bu PowerShellGet cmdlet'lerinden herhangi birini IE etkisi olmuştur değil., yükleme betiği, Update-modülü, Update-komut dosyası, yayımlama-Module Yayımla-komut dosyası yükleme-Module devam çalışmak.</span><span class="sxs-lookup"><span data-stu-id="5bec0-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="5bec0-108">__Kök neden__: mühendisleri neden sayfaya düğmeleri gibi Facebook sosyal medya getiren bir sorun olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5bec0-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="5bec0-109">__Çözümleme__: mühendisleri Facebook sayımı bilgilerini devre dışı bırakarak sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5bec0-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="5bec0-110">__Sonraki adımlar__: biz Facebook API'si bizim kullanımını düzeltmek için bir iç izleme sorunu açılır.</span><span class="sxs-lookup"><span data-stu-id="5bec0-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="5bec0-111">12/15/2016 - PowerShellGallery Web sitesi aracılığıyla e-posta gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="5bec0-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="5bec0-112">__Özet etkisi__: 13/12/2016 ile 15/12/2016 arasında kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye gönderilen iletiler PowerShell Galerisi yöneticileri tarafından alınmadı.</span><span class="sxs-lookup"><span data-stu-id="5bec0-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="5bec0-113">__Kök neden__: mühendisleri bir kimlik doğrulama sorunu nedeni SMTP sunucusu ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5bec0-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="5bec0-114">__Çözümleme__: mühendisleri kimlik doğrulama sorunu çözün ve SMTP sunucusuna bağlantı geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bec0-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="5bec0-115">__Sonraki adımlar__: ileti göndermek için kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye bağlantılar kullandıysanız cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="5bec0-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="5bec0-116">Verdiğimiz rahatsızlıktan dolayı özür dileriz.</span><span class="sxs-lookup"><span data-stu-id="5bec0-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="5bec0-117">8/10/2016 - çözümlendi: e-postalar için gönderilemedicgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="5bec0-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="5bec0-118">__Özet etkisi__: 8/5/2016 ile 8/10/2016 arasında müşteriler için e-posta gönderemiyor cgadmin@microsoft.com, ya da bize özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5bec0-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="5bec0-119">__Kök neden__: mühendisleri tanımlanan neden e-posta hesabı bir yapılandırma değişikliği.</span><span class="sxs-lookup"><span data-stu-id="5bec0-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="5bec0-120">__Çözümleme__: mühendisleri çalışılan yapılandırma sorunu gidermek için.</span><span class="sxs-lookup"><span data-stu-id="5bec0-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="5bec0-121">__Sonraki adımlar__: bize bağlantı kullanılan veya posta gönderilen cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="5bec0-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="5bec0-122">Anlayışınız için teşekkür ederiz.</span><span class="sxs-lookup"><span data-stu-id="5bec0-122">Thank you for your patience.</span></span>


