---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: "WMF 5.1 sürüm notları"
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="f4868-103">Windows Management Framework (WMF) 5.1 sürüm notları</span><span class="sxs-lookup"><span data-stu-id="f4868-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="f4868-104">WMF 5.1, Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve yazılım envanteri günlüğü (SIL) bileşenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f4868-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="f4868-105">WMF 5.1 yüklenebilmesi için Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2 ve WMF 5.0 RTM dahil olmak üzere üzerinden bazı geliştirmeler sağlar:</span><span class="sxs-lookup"><span data-stu-id="f4868-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="f4868-106">Yeni cmdlet'leri: yerel kullanıcılar ve gruplar; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="f4868-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="f4868-107">PowerShellGet geliştirmeler imzalı modülleri, zorlama ve JEA modülleri yükleme</span><span class="sxs-lookup"><span data-stu-id="f4868-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="f4868-108">PackageManagement kapsayıcıları, CBS Kurulum EXE tabanlı Kurulum, CAB paketleri için destek eklendi</span><span class="sxs-lookup"><span data-stu-id="f4868-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="f4868-109">DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="f4868-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="f4868-110">Zorlama PowerShellGet cmdlet'lerini kullanırken çekme sunucudan gelen ve gelen katalog imzalı modüllerin dahil olmak üzere güvenlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="f4868-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="f4868-111">Çok sayıda kullanıcı isteklerini ve sorunları yanıtlarını</span><span class="sxs-lookup"><span data-stu-id="f4868-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="f4868-112">**Önemli Notlar:**</span><span class="sxs-lookup"><span data-stu-id="f4868-112">**Important notes:**</span></span>

- <span data-ttu-id="f4868-113">**WMF 5.1 için .NET Framework 4.5.2** (veya üstü).</span><span class="sxs-lookup"><span data-stu-id="f4868-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="f4868-114">Yükleme başarılı olur, ancak temel özellikleri başarısız olur, .NET 4.5.2 (veya üstü) yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="f4868-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="f4868-115">Yönergeler bulunan [yükleme ve yapılandırma WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) konu.</span><span class="sxs-lookup"><span data-stu-id="f4868-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="f4868-116">5.1 WMF RTM yüklenmeden önce WMF 5.1 önizleme kaldırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4868-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="f4868-117">WMF 5.1 doğrudan WMF 5.0 veya WMF 4.0 üzerinden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f4868-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="f4868-118">Bu __gerekli değil__ WMF 5.1 Windows 7 ve Windows Server 2008 R2 yüklenmeden önce WMF 4.0 sürümünü yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="f4868-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="f4868-119">WMF 5.1 önizleme sürümü için bir sorun oluştu ve çözümlendi.</span><span class="sxs-lookup"><span data-stu-id="f4868-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


