---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Arama sonuçlarını filtreleme
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084411"
---
# <a name="filtering-search-results"></a>Arama sonuçlarını filtreleme

[Paketleri sekmesinde](https://www.powershellgallery.com/packages) PowerShell galerisinde kullanılabilir tüm paketleri görüntüler.

Filtrelemek, sıralamak ve paketleri aramak için birkaç yol vardır.
Belirli bir paket hakkında daha fazla ayrıntı görmek için paket'a tıklayın.

## <a name="filter-by"></a>Filtreleme Ölçütü

"Filtresi tarafından" altındaki açılan sonuçlarına göre filtre uygulamak kullanıcıların sağlar:
- Ön sürümü dahil et
- Yalnızca kararlı

"Ön" ve "Kararlı" hakkında daha fazla bilgi için bkz: [yayın öncesi sürüm eklenen PowerShellGet ve PowerShell Galerisi](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) PowerShell Ekibi blogunda.

Aşağı açılan altındaki onay kutularını sonuçlarına göre filtre uygulamak kullanıcılara izin ver:
- Paket türleri
  - Modül
  - Betik
- Categories
  - Cmdlet
  - DSC kaynak
  - İşlev
  - Rol özelliği
  - İş akışı

Yalnızca PowerShell Galerisi modülleri görmek için paket türleri bir modülde denetleyin.
Benzer şekilde, yalnızca betikler PowerShell galerisinde görmek için paket türleri betikte denetleyin.

> [!NOTE]
> Filtreler dahildir.
> Örnek: Cmdlet'ini veya işlevinde (veya her ikisi de) işaretlediyseniz hem cmdlet'ler ve işlevler içeren bir paket görünür.
> Ne seçili değilse, paket görünmez.
> Benzer şekilde, tüm kategorileri seçilirse yalnızca bu kategorilerden birindeyse içeren paketler görüntülenir.
> **Bu kategorilerin hiçbirine ait olmayan paketleri görünmez.**

## <a name="sort-by"></a>Sıralama ölçütü

Sıralama açılan sonuçlarına göre sıralama olanağı sağlar:
- Popülerlik - popülerliği indirme sayısına göre belirlenir
- A-Z - paket adına göre alfabetik
- Son - paketleri yayımlama tarih sırasına göre görünür

## <a name="search-box"></a>Arama kutusu

Arama kutusuna anahtar sözcükleri paketleri aramak kullanıcıların sağlar.
Daha fazla bilgi için [galeri arama söz dizimi](search-syntax.md).
