---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Paket listeden kaldırma
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004175"
---
# <a name="unlisting-packages"></a>Unlisting paketleri

**Bir seçenek olarak gösterilmeyen PowerShell Galerisi'nden bir paketi kaldırma neden?**

PowerShell Galerisi paketlerini kalıcı olarak silme kullanıcılar desteklemez.
Bu, gelecekteki olası sonları hakkında endişelenmeden paketlerinizi üzerinde bağımlılıkları almak diğer sağlar.
Örneğin, Azure modülü, Pester modülü bağlıdır ve sonra da kullanıcı artık Azure modülünü Galeriden kaldırılır, Pester modülü kullanır.

Bir paketi kaldırma yerine ancak, bunu yerine listeden.

**PowerShell Galerisi paketin yapmak etkilenmeden yapar?**

Modül veya PowerShell Galerisi'nde betik gibi bir paket listeden kaldırılırken paketleri sekmesinden kaldırır. Ayrıca, listede bulunmayan paketleri arama çubuğunu kullanarak bulunabilirlik olmayacaktır.
Listede bulunmayan bir paketini indirmek için tek yolu paketin sürümü ve tam adını belirtmektir.
Bu nedenle, bir paketi listeden kaldırma bağımlı betikler veya diğer modüller keser değil.

Paketi listeden kaldırma için paket Ayrıntılar sayfasını ziyaret edin ve Sil'Module ' seçin. 'Listelendi' onay kutusunun işaretini kaldırın ve Kaydet'e tıklayın.

**Bir paketi nasıl kaldırabilir miyim?**

Paket silme gerekli olduğu bir senaryoda karşılaşırsanız, PowerShell Galerisi yöneticileri ile iletişime geçin.
Geçerli silme senaryolar şunlardır:
- Telif Hakkı ihlalini sorunları.
- Paket zararlı içeriğe sahip.
- Paket hassas verileri içerir.

Bir silme paket isteği PowerShell Galerisi yöneticilerine göndermek için paketinizin ayrıntı sayfasını ziyaret edin ve Destek'e başvur seçeneğini belirleyin.
