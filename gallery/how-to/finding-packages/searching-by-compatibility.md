---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galeri, powershell, cmdlet, psgallery
title: Paketler uyumlu PowerShell sürümleri veya işletim sistemi
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084581"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>PowerShell sürümleri veya işletim sistemleriyle uyumlu paketleri

5.1 sürümünden itibaren PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde kullanılabilir.

## <a name="searching-by-powershell-edition"></a>PowerShell sürümüne göre arama

PowerShell'ın iki sürümü vardır:
- **Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş ve Windows Masaüstü ve Windows Server Core gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek sürümü:** .NET Core üzerine yapılandırılan ve Nano Server gibi Windows ve Windows IOT azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell Galerisi özel PowerShell sürümleri için paketler uyumlu filtrelemenize olanak sağlar.

Bir paket uyumlu varsa pseditions'ı, belirtilen 'PowerShell sürümleri' bir parçası olarak listelenen paketi görüntüleme sayfasında hem de paketleri sonuçları.
PowerShell kullanarak uyumlu paketleri için arama da yapabilirsiniz.

![Pseditions'ı olan sayfa öğesi görüntüle](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>PowerShell Core üzerinde çalışan paketleri UI Galerisi'nde Ara

Etiketleri kullanma: "PSEdition_Desktop" ve etiketler: "PSEdition_Core" filtreleri PowerShell Galerisi paketleri.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Etiketleri kullanma: "PowerShell Core Edition ile uyumlu olan öğeleri aramasına izin PSEdition_Core".

![Çekirdek PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Etiketleri kullanma: "PowerShell Masaüstü sürümü ile uyumlu olan öğeleri aramasına izin PSEdition_Desktop".

![Masaüstü PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>PowerShell kullanarak uyumlu sürümlerini bulmak paketleri Ara
PowerShell sürümü ve işletim sistemi için filtrelemek için etiketler belirtebilirsiniz.
Kullandığınız `Find-Package` cmdlet'i belirtme `-Tag` sürümü (ve işletim sistemi) belirtmek için parametre hedeflediğiniz.
Böyle:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>İşletim sistemi tarafından arama

PowerShell Core Windows, Linux ve MacOS için kullanılabilir olduğundan, paketleri galerisinde bu işletim sistemlerinden herhangi bir birleşimini için tasarlanmış olabilir. UI galeride, işletim sistemi tarafından etiketlenmiş paketler bulmak için aşağıdaki depolamaya etiketleri kullanın:

- Etiketler: "Windows"
- Etiketler: "Linux"
- Etiketler: "MacOS"

Bu etiketler belirtebileceğiniz `Find-Module` (ve diğer cmdlet'ler PowerShellGet Modülü) şöyle:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Birden çok uyumluluğunu için arama

Söz dizimi kullanılarak birden çok uyumluluğunu olan bir paketi arayabilirsiniz:

Etiketler: "Compatibility1" "Compatibility2"

Örneğin, bir paket my Windows ve Linux makinelerinde çalışır, PowerShell Core uyumluluğu için arıyorsanız, arama etiketleri kullanın:

Etiketler: "PSEdition_Core", "Windows" "Linux"

PowerShell kullanarak arama yapmak için kullanabileceğiniz `Find-Module` (ve diğer PowerShellGet modülündeki cmdlet'ler) şöyle:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Geliştirme ve paketler uyumlu PowerShell sürümleriyle bulma hakkında daha fazla bilgi

- [PSEditions’ı olan Modüller](../../concepts/module-psedition-support.md)
- [PSEditions’ı olan Betikler](../../concepts/script-psedition-support.md)
