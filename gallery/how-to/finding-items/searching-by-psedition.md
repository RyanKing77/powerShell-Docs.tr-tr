---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Öğeleri ile uyumlu PowerShell sürümleri
ms.openlocfilehash: f661c2cd076acb9c11394ba0b752ebd154965ff4
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="f1cc0-103">Öğeleri ile uyumlu PowerShell sürümleri</span><span class="sxs-lookup"><span data-stu-id="f1cc0-103">Items with compatible PowerShell Editions</span></span>

<span data-ttu-id="f1cc0-104">Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f1cc0-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="f1cc0-105">**Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1cc0-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="f1cc0-106">**Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1cc0-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="f1cc0-107">PowerShell Galerisi desteklenen PSEditions meta verileri ayıklar ve filtreleri öğeler için özel PowerShell sürümleri uyumlu sağlar</span><span class="sxs-lookup"><span data-stu-id="f1cc0-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="f1cc0-108">Bir öğe uyumlu olup olmadığını PSEditions, belirtilen 'PowerShell sürümleri' bir parçası olarak listelenir öğesi görünen sayfa hem de öğeleri sonuçları.</span><span class="sxs-lookup"><span data-stu-id="f1cc0-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>

![PSEditions öğesi görüntüleme sayfası](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="f1cc0-110">Galeri PowerShellCore üzerinde çalışan kullanıcı Arabirimi öğeleri arayın</span><span class="sxs-lookup"><span data-stu-id="f1cc0-110">Search for items in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="f1cc0-111">Etiketler kullanın: "PSEdition_Desktop" ve etiketler: filtreleri PowerShell Galerisi öğeler için "PSEdition_Core".</span><span class="sxs-lookup"><span data-stu-id="f1cc0-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="f1cc0-112">Etiketler kullanın: PowerShell çekirdek Edition ile uyumlu öğeleri aramak için "PSEdition_Core".</span><span class="sxs-lookup"><span data-stu-id="f1cc0-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Çekirdek PSEdition ile uyumlu öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="f1cc0-114">Etiketler kullanın: PowerShell Masaüstü Edition ile uyumlu öğeleri aramak için "PSEdition_Desktop".</span><span class="sxs-lookup"><span data-stu-id="f1cc0-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Masaüstü PSEdition ile uyumlu öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="f1cc0-116">Yazma ve ile uyumlu PowerShell sürümleri öğeleri bulma hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="f1cc0-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="f1cc0-117">PSEditions’ı olan Modüller</span><span class="sxs-lookup"><span data-stu-id="f1cc0-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="f1cc0-118">PSEditions’ı olan Betikler</span><span class="sxs-lookup"><span data-stu-id="f1cc0-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)