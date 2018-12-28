---
ms.date: 08/25/2017
keywords: PowerShell cmdlet'i
title: ObjectModelRoot Nesnesi
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406032"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot Nesnesi

**$PsISE** asıl kök nesnesi içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) nesne Microsoft.PowerShell.Host.ISE.ObjectModelRoot sınıfı bir örneğidir.
Bu konuda özellikleri açıklanmıştır **ObjectModelRoot** nesne.

## <a name="properties"></a>Özellikler

### <a name="currentfile"></a>CurrentFile

> Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

O anda odağı içeren bu konak nesnesi ile ilişkili dosya salt okunur özelliği.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Odaklanmış PowerShell sekme salt okunur özelliği.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği Düzenleyicisi altındaki yatay araç bölmesinde bulunur.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği, düzenleyicinin sağ taraftaki dikey aracı bölmesinde bulunur.

### <a name="options"></a>Seçenekler

> Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Çeşitli seçenekler, salt okunur özelliği Windows PowerShell ıse'de ayarlarını değiştirebilirsiniz.

### <a name="powershelltabs"></a>PowerShellTabs

> Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Windows PowerShell ISE'de açık olan PowerShell sekme koleksiyon salt okunur özelliği. Varsayılan olarak, bu nesne bir PowerShell sekmesi içerir. Ancak, betikleri kullanarak veya Windows PowerShell ISE'de menülerini kullanarak bu nesne için daha fazla PowerShell sekme ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)