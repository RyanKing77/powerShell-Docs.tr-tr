---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Paket ile uyumlu PowerShell sürümleri
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004152"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="f2bc0-103">Paket ile uyumlu PowerShell sürümleri</span><span class="sxs-lookup"><span data-stu-id="f2bc0-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="f2bc0-104">Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="f2bc0-105">**Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="f2bc0-106">**Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="f2bc0-107">PowerShell Galerisi desteklenen pseditions'ı meta verileri ayıklar ve filtreleri paketleri için özel PowerShell sürümleri uyumlu sağlar</span><span class="sxs-lookup"><span data-stu-id="f2bc0-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="f2bc0-108">Bir paket uyumlu varsa pseditions'ı, belirtilen 'PowerShell sürümleri' bir parçası olarak listelenecektir paketi görüntüleme sayfasında hem de paketleri sonuçları.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Pseditions'ı olan sayfa öğesi görüntüle](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="f2bc0-110">Paketleri PowerShellCore üzerinde çalışan UI Galerisi'nde Ara</span><span class="sxs-lookup"><span data-stu-id="f2bc0-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="f2bc0-111">Etiketleri kullanma: "PSEdition_Desktop" ve etiketler: "PSEdition_Core" filtreleri PowerShell Galerisi paketleri.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="f2bc0-112">Etiketleri kullanma: "PowerShell Core Edition ile uyumlu olan öğeleri aramasına izin PSEdition_Core".</span><span class="sxs-lookup"><span data-stu-id="f2bc0-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Çekirdek PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="f2bc0-114">Etiketleri kullanma: "PowerShell Masaüstü sürümü ile uyumlu olan öğeleri aramasına izin PSEdition_Desktop".</span><span class="sxs-lookup"><span data-stu-id="f2bc0-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Masaüstü PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="f2bc0-116">Geliştirme ve paketler uyumlu PowerShell sürümleriyle bulma hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="f2bc0-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="f2bc0-117">PSEditions’ı olan Modüller</span><span class="sxs-lookup"><span data-stu-id="f2bc0-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="f2bc0-118">PSEditions’ı olan Betikler</span><span class="sxs-lookup"><span data-stu-id="f2bc0-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
