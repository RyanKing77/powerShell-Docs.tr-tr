---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Betik Bölmesi ve Konsol Bölmesinde Sekme Tamamlamayı Kullanma
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Betik Bölmesi ve Konsol Bölmesinde Sekme Tamamlamayı Kullanma

Betik bölmesine ya da komut bölmesinde yazarken sekme tamamlama otomatik Yardım sağlar. Bu özelliğin avantajlarından yararlanmak için aşağıdaki adımları kullanın:

## <a name="to-automatically-complete-a-command-entry"></a>Bir komut girişi otomatik olarak tamamlamak için

Komut bölmesinde veya komut dosyası bölmesi, birkaç karakterini bir komut yazın ve istenen tamamlama metni seçmek için SEKME tuşuna basın. Birden çok öğe başlangıçta yazdığınız metni ile başlarsa, ardından istediğiniz öğeyi görünene kadar SEKME tuşuna basarak devam edin. Sekme tamamlama, bir cmdlet adı, parametre adı, değişken adı, nesne özellik adı veya bir dosya yolu yazarak ile yardımcı olabilir.

> [!NOTE]
> Yalnızca .ps1, .psd1 veya .psm1 dosyaları düzenlerken betik bölmesinde SEKME tuşuna basarak otomatik olarak bir komut işlemini tamamlar. Sekme tamamlama zaman komut bölmesinde yazarak dilediğiniz zaman çalışır.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Bir cmdlet parametresi girişi otomatik olarak tamamlamak için

Komut bölmesi veya betik bölmesinde kısa çizgi ve ardından cmdlet'i yazın ve sonra SEKME tuşuna basın.

Örneğin, `Get-Process -` sekme her cmdlet parametrelerinin sırayla görüntülemek için birden çok kez basın.

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE Tanıtımı](Introducing-the-Windows-PowerShell-ISE.md)
- [Bir PowerShell sekme oluşturma](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)