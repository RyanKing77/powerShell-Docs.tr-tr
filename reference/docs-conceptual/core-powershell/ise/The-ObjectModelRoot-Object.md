---
ms.date: 08/25/2017
keywords: PowerShell cmdlet'i
title: ObjectModelRoot Nesnesi
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot Nesnesi

**$PsISE** asıl kök nesnesi içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) olan nesne, Microsoft.PowerShell.Host.ISE.ObjectModelRoot sınıfının bir örneği değil.
Bu konuda, özelliklerini açıklar **ObjectModelRoot** nesnesi.

## <a name="properties"></a>Özellikler

### <a name="currentfile"></a>CurrentFile

> Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Şu anda odağa sahip bu konağı nesnesi ile ilişkilendirilmiş dosya alır salt okunur özellik.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Odaklanmış PowerShell sekmesini alır salt okunur özellik.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Şu anda görünür Windows PowerShell ISE eklenti aracı alır salt okunur özellik düzenleyicisinin alt yatay aracı bölmesinde bulunur.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Şu anda görünür Windows PowerShell ISE eklenti aracı alır salt okunur özellik Düzenleyicisinin sağ taraftaki dikey aracı bölmesinde bulunur.

### <a name="options"></a>Seçenekler

> Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Çeşitli seçenekler alır salt okunur özelliğini Windows PowerShell ISE ayarlarını değiştirebilirsiniz.

### <a name="powershelltabs"></a>PowerShellTabs

> Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Windows PowerShell ISE açık PowerShell sekmeler koleksiyonunu alır salt okunur özellik. Varsayılan olarak, bu nesne bir PowerShell sekme içerir. Ancak, komut dosyalarını kullanarak veya Windows PowerShell ISE menüleri kullanarak bu nesne için daha fazla PowerShell sekmeler ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)