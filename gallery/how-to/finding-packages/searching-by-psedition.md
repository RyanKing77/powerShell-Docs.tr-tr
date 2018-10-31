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
# <a name="packages-with-compatible-powershell-editions"></a>Paket ile uyumlu PowerShell sürümleri

Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.

- **Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>PowerShell Galerisi desteklenen pseditions'ı meta verileri ayıklar ve filtreleri paketleri için özel PowerShell sürümleri uyumlu sağlar

Bir paket uyumlu varsa pseditions'ı, belirtilen 'PowerShell sürümleri' bir parçası olarak listelenecektir paketi görüntüleme sayfasında hem de paketleri sonuçları.

![Pseditions'ı olan sayfa öğesi görüntüle](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>Paketleri PowerShellCore üzerinde çalışan UI Galerisi'nde Ara

Etiketleri kullanma: "PSEdition_Desktop" ve etiketler: "PSEdition_Core" filtreleri PowerShell Galerisi paketleri.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Etiketleri kullanma: "PowerShell Core Edition ile uyumlu olan öğeleri aramasına izin PSEdition_Core".

![Çekirdek PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Etiketleri kullanma: "PowerShell Masaüstü sürümü ile uyumlu olan öğeleri aramasına izin PSEdition_Desktop".

![Masaüstü PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Geliştirme ve paketler uyumlu PowerShell sürümleriyle bulma hakkında daha fazla bilgi

- [PSEditions’ı olan Modüller](../../concepts/module-psedition-support.md)
- [PSEditions’ı olan Betikler](../../concepts/script-psedition-support.md)
