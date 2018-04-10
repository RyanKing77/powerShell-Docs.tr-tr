---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a>Öğeler sekmesi

[Öğeleri sekmesini](https://www.powershellgallery.com/items) PowerShell galerisinde tüm kullanılabilir öğeleri görüntüler.

Filtre, sıralama ve öğeleri aramak için birkaç yolu vardır.
Belirli bir öğe hakkında daha fazla ayrıntı görmek için öğeyi tıklatın.

## <a name="filter-by"></a>Filtre ölçütü

Aşağı açılan "Filtre tarafından" altında sonuçlarına göre filtre uygulamak kullanıcıların sağlar:
* Yayın öncesi içerir
* Yalnızca kararlı

"Yayın öncesi" ve "Kararlı" hakkında daha fazla bilgi için bkz: [yayın öncesi sürüm eklenen PowerShellGet ve PowerShell Galerisi](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) PowerShell ekip blogu içinde.

Aşağı açılan altında onay kutularını sonuçlarına göre filtre uygulamak kullanıcılara izin ver:
* Öğesi türleri
  - Modül
  - Betik
* kategorileri
  - Cmdlet
  - DSC kaynağı
  - İşlev
  - Rol özelliği
  - İş akışı

Yalnızca PowerShell Galerisi modülleri, modül öğesi türleri denetleyin.
Benzer şekilde, yalnızca PowerShell galerisinde komut dosyaları, komut dosyasında öğesi türlerini denetleyin.

> [!NOTE]
> Filtreler dahildir.
> Örnek: Cmdlet'ler ve işlevler içeren bir öğeyi cmdlet'ini veya işlevi (veya her ikisi de) işaretlediyseniz görünür.
> Hiçbiri seçili ise, öğenin görünmez.
> Benzer şekilde, tüm kategorileri seçtiyseniz, yalnızca bu kategorilerden birini içeren öğeleri görünür.
> **Bu kategorilerin hiçbirine ait olmadığından öğeleri görünmez.**

## <a name="sort-by"></a>Sıralama ölçütü

Sıralama ölçütü açılan sonuçlarına göre sıralamak kullanıcıların sağlar:
* Popülerliği - popülerliği karşıdan sayısı tarafından belirlenir.
* A-Z - ada göre öğesi
* Son - öğeleri Yayımla tarih sırasına göre görünür

## <a name="search-box"></a>Arama kutusu

Arama kutusuna anahtar sözcükleri öğeleri aramak kullanıcıların sağlar.
Daha fazla bilgi için bkz: [galeri arama söz dizimi](psgallery_search_syntax.md).