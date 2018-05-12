---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Arama sonuçlarını filtreleme
ms.openlocfilehash: 5a7ea8207619318efd8195ee3d1c8f8ab51209da
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="filtering-search-results"></a>Arama sonuçlarını filtreleme

[Öğeleri sekmesini](https://www.powershellgallery.com/items) PowerShell galerisinde tüm kullanılabilir öğeleri görüntüler.

Filtre, sıralama ve öğeleri aramak için birkaç yolu vardır.
Belirli bir öğe hakkında daha fazla ayrıntı görmek için öğeyi tıklatın.

## <a name="filter-by"></a>Filtre ölçütü

Aşağı açılan "Filtre tarafından" altında sonuçlarına göre filtre uygulamak kullanıcıların sağlar:
- Yayın öncesi içerir
- Yalnızca kararlı

"Yayın öncesi" ve "Kararlı" hakkında daha fazla bilgi için bkz: [yayın öncesi sürüm eklenen PowerShellGet ve PowerShell Galerisi](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) PowerShell ekip blogu içinde.

Aşağı açılan altında onay kutularını sonuçlarına göre filtre uygulamak kullanıcılara izin ver:
- Öğesi türleri
  - Modül
  - Betik
- kategorileri
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
- Popülerliği - popülerliği karşıdan sayısı tarafından belirlenir.
- A-Z - ada göre öğesi
- Son - öğeleri Yayımla tarih sırasına göre görünür

## <a name="search-box"></a>Arama kutusu

Arama kutusuna anahtar sözcükleri öğeleri aramak kullanıcıların sağlar.
Daha fazla bilgi için bkz: [galeri arama söz dizimi](search-syntax.md).