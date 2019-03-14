---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: 'wmf,powershell,setup'
title: WMF 5.1 Sürüm Notları
---

# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="d75b3-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="d75b3-103">Windows Management Framework (WMF) 5.1</span></span>

<span data-ttu-id="d75b3-104">WMF; kullanıcılara mevcut Windows sistemlerini Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve Yazılım Envanter Günlüğü (SIL) bileşenleri ile güncelleştirme imkanı verir.</span><span class="sxs-lookup"><span data-stu-id="d75b3-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="d75b3-105">WMF 5.1; Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2’ye yüklenebilir ve WMF 5.0 RTM’ye şu gibi iyileştirmeler getirir:</span><span class="sxs-lookup"><span data-stu-id="d75b3-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="d75b3-106">Yeni cmdlet’ler: yerel kullanıcılar ve gruplar; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="d75b3-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="d75b3-107">PowerShellGet iyileştirmeleri arasında imzalı modülleri zorlama ve JEA modülleri yükleme bulunur</span><span class="sxs-lookup"><span data-stu-id="d75b3-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="d75b3-108">PackageManagement; Kapsayıcılar, CBS Kurulumu, EXE temelli kurulum ve CAD paketleri için destek ekledi</span><span class="sxs-lookup"><span data-stu-id="d75b3-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="d75b3-109">DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d75b3-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="d75b3-110">PowerShellGet cmdlet’leri kullanırken Çekme Sunucusundan gelen katalog imzalı modülleri zorlamayı da içeren güvenlik iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d75b3-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="d75b3-111">Birkaç kullanıcı talebi ve sorununa yanıt</span><span class="sxs-lookup"><span data-stu-id="d75b3-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="d75b3-112">Bu sürümdeki yenilikler hakkında daha fazla bilgi için [Yeni Senaryolar ve Özellikler](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features) başlığı altında listelenen konulara göz atın.</span><span class="sxs-lookup"><span data-stu-id="d75b3-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="d75b3-113">[Yükleme ve Yapılandırma](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) konusunda gereksinimler listelenmiş ve WMF yükleme yönergeleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d75b3-113">The [Install and Configure](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="d75b3-114">[Uyumluluk](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) konusunda, hangi Windows sürümünde hangi WMF sürümünün yüklü olabileceği listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d75b3-114">The [Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="d75b3-115">[Ürün Uyumluluğu](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) konusunda WMF 5.1’in kullanımını henüz onaylamamış olan Microsoft uygulamaları listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d75b3-115">[Product Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="d75b3-116">WMF bileşenleri hakkında ayrıntılı bilgi, MSDN belgelerinde bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="d75b3-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="d75b3-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d75b3-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/powershell/)
- <span data-ttu-id="d75b3-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="d75b3-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="d75b3-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="d75b3-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="d75b3-120">[Yazılım Envanter Günlüğü](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="d75b3-120">[Software Inventory Logging](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span></span>
