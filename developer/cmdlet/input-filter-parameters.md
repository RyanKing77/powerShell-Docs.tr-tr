---
title: Giriş filtre parametrelerini | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845741"
---
# <a name="input-filter-parameters"></a>Filtre Parametreleri Girişi

Bir cmdlet tanımlayabilirsiniz `Filter`, `Include`, ve `Exclude` cmdlet etkiler giriş nesne kümesini filtrelemek parametreleri.

Genellikle, giriş nesne tarafından belirtilen bir `InputObject`, `Path`, veya `Name` parametresi. Örneğin, bir cmdlet olabilir bir `Path` joker karakterler ve her bir giriş nesnesi için yol noktalarını kullanarak birden çok yol kabul eden bir parametre. Birlikte kullanılan `Filter`, `Include`, ve `Exclude` parametreleri daha uygun yolları cmdlet çalıştırıldığında her saat çalışır.

## <a name="include-and-exclude-parameters"></a>Dahil etme ve dışlama parametreleri

`Include` Ve `Exclude` parametreleri dahil ya da cmdlet'e geçirilen giriş nesneler kümesinden dışlanan nesneleri belirleyin. Filtre standart bir joker karakter dilinde ifade edilebilir olduğunda bu parametreleri kullanın. (Joker karakterler hakkında daha fazla bilgi için bkz: [joker karakterleri destekleme Cmdlet parametreleri](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include` Parametre adları ekleme filtre eşleşen tüm nesneleri içerir. `Exclude` Parametre adları eşleşen filtre tüm nesneleri dahil değildir.

## <a name="filter-parameter"></a>Filtre parametresi

`Filter` Parametresi, standart bir joker karakter dilde değil ifade bir filtre belirtir. Örneğin, Active Directory hizmet arabirimi (ADSI) veya SQL filtreleri cmdlet'ine geçirilebilir kendi `Filter` parametresi. Windows PowerShell tarafından sağlanan Cmdlet'lerde, bu filtreler, cmdlet bir veri deposuna erişmek için Windows PowerShell sağlayıcıları tarafından belirtilir. Her bir sağlayıcı, genellikle kendi filtre tanımlar.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Hiçbir giriş nesne kümesini belirtilirse filtreleme

Hiçbir giriş nesne kümesini belirtilirse, bu genellikle karşı tüm nesneleri filtrelemek anlamına gelir. Daha fazla bilgi için[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)