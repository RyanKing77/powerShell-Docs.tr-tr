---
ms.date: 2017-08-25
keywords: PowerShell cmdlet'i
title: ObjectModelRoot nesnesi
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot nesnesi

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

- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)
