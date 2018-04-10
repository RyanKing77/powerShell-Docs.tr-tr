---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: WMF 5.1 Sürüm Notları
ms.openlocfilehash: eb22267c1af28a9fcdd049c76d363fff687f6167
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="2f251-103">Windows Management Framework (WMF) 5.1 sürüm notları</span><span class="sxs-lookup"><span data-stu-id="2f251-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="2f251-104">WMF 5.1, Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve yazılım envanteri günlüğü (SIL) bileşenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2f251-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="2f251-105">WMF 5.1; Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2’ye yüklenebilir ve WMF 5.0 RTM’ye şu gibi iyileştirmeler getirir:</span><span class="sxs-lookup"><span data-stu-id="2f251-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="2f251-106">Yeni cmdlet’ler: yerel kullanıcılar ve gruplar; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="2f251-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="2f251-107">PowerShellGet iyileştirmeleri arasında imzalı modülleri zorlama ve JEA modülleri yükleme bulunur</span><span class="sxs-lookup"><span data-stu-id="2f251-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="2f251-108">PackageManagement; Kapsayıcılar, CBS Kurulumu, EXE temelli kurulum ve CAD paketleri için destek ekledi</span><span class="sxs-lookup"><span data-stu-id="2f251-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="2f251-109">DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2f251-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="2f251-110">PowerShellGet cmdlet’leri kullanırken Çekme Sunucusundan gelen katalog imzalı modülleri zorlamayı da içeren güvenlik iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2f251-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="2f251-111">Birkaç kullanıcı talebi ve sorununa yanıt</span><span class="sxs-lookup"><span data-stu-id="2f251-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="2f251-112">**Önemli Notlar:**</span><span class="sxs-lookup"><span data-stu-id="2f251-112">**Important notes:**</span></span>

- <span data-ttu-id="2f251-113">**WMF 5.1 için .NET Framework 4.5.2** (veya üstü).</span><span class="sxs-lookup"><span data-stu-id="2f251-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="2f251-114">Yükleme başarılı olur, ancak temel özellikleri başarısız olur, .NET 4.5.2 (veya üstü) yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="2f251-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="2f251-115">Yönergeler bulunan [yükleme ve yapılandırma WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) konu.</span><span class="sxs-lookup"><span data-stu-id="2f251-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="2f251-116">5.1 WMF RTM yüklenmeden önce WMF 5.1 önizleme kaldırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f251-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="2f251-117">WMF 5.1 doğrudan WMF 5.0 veya WMF 4.0 üzerinden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2f251-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="2f251-118">Bu __gerekli değil__ WMF 5.1 Windows 7 ve Windows Server 2008 R2 yüklenmeden önce WMF 4.0 sürümünü yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="2f251-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="2f251-119">WMF 5.1 önizleme sürümü için bir sorun oluştu ve çözümlendi.</span><span class="sxs-lookup"><span data-stu-id="2f251-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>