---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Öğeleri ile uyumlu PowerShell sürümleri
ms.openlocfilehash: dd2c67417994e960845f7cef09320a0f688a0212
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="items-with-compatible-powershell-editions"></a>Öğeleri ile uyumlu PowerShell sürümleri

Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.

- **Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>PowerShell Galerisi desteklenen PSEditions meta verileri ayıklar ve filtreleri öğeler için özel PowerShell sürümleri uyumlu sağlar

Bir öğe uyumlu olup olmadığını PSEditions, belirtilen 'PowerShell sürümleri' bir parçası olarak listelenir öğesi görünen sayfa hem de öğeleri sonuçları.

![PSEditions öğesi görüntüleme sayfası](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Galeri PowerShellCore üzerinde çalışan kullanıcı Arabirimi öğeleri arayın

Etiketler kullanın: "PSEdition_Desktop" ve etiketler: filtreleri PowerShell Galerisi öğeler için "PSEdition_Core".

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Etiketler kullanın: PowerShell çekirdek Edition ile uyumlu öğeleri aramak için "PSEdition_Core".

![Çekirdek PSEdition ile uyumlu öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Etiketler kullanın: PowerShell Masaüstü Edition ile uyumlu öğeleri aramak için "PSEdition_Desktop".

![Masaüstü PSEdition ile uyumlu öğeleri için arama sonuçları](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Yazma ve ile uyumlu PowerShell sürümleri öğeleri bulma hakkında daha fazla bilgi

- [PSEditions’ı olan Modüller](../../concepts/module-psedition-support.md)
- [PSEditions’ı olan Betikler](../../concepts/script-psedition-support.md)