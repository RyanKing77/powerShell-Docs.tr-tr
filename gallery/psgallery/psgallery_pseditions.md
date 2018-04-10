---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_pseditions
ms.openlocfilehash: 0b30c1da53832a6b74be7aa14ed9331b1e9fe643
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="items-with-compatible-powershell-editions"></a>Öğeleri ile uyumlu PowerShell sürümleri
Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.

- **Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>PowerShell Galerisi desteklenen PSEditions meta verileri ayıklar ve filtreleri öğeler için özel PowerShell sürümleri uyumlu sağlar

Bir öğe uyumlu olup olmadığını PSEditions, belirtilen 'PowerShell sürümleri' bir parçası olarak listelenir öğesi görünen sayfa hem de öğeleri sonuçları.
![PSEditions öğesi görüntüleme sayfası](Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Galeri PowerShellCore üzerinde çalışan kullanıcı Arabirimi öğeleri arayın
Etiketler kullanın: "PSEdition_Desktop" ve etiketler: filtreleri PowerShell Galerisi öğeler için "PSEdition_Core".

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.
![Çekirdek PSEdition ile uyumlu öğeleri için arama sonuçları](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.
![Masaüstü PSEdition ile uyumlu öğeleri için arama sonuçları](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Yazma ve ile uyumlu PowerShell sürümleri öğeleri bulma hakkında daha fazla bilgi
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[PSEditions’ı olan Modüller](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[PSEditions’ı olan Betikler](../psget/script/scriptwithpseditionsupport.md)