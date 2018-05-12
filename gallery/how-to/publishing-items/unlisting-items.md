---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Öğeleri listeden kaldırma
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a>Öğeleri listeden kaldırma

**PowerShell Galerisi'nden bir seçenek olarak gösterilmeyen bir öğe kaldırıldığında neden?**

PowerShell Galerisi, kullanıcıların kendilerine öğelerini kalıcı olarak silmesini desteklemez.
Bu, diğerleri gelecekteki olası kesmeleri hakkında endişelenmeden bulunan öğelerinizi bağımlılıkları yapılacak sağlar.
Örneğin, Azure modülünü Pester modül bağlıdır ve sonra da kullanıcı artık Azure modül Galerisi'nden kaldırılır Pester modülü kullanır.

Bir öğeyi kaldırmak yerine ancak, bunu yerine unlist.

**Ne unlisting PowerShell Galerisi bir öğede musunuz?**

Modül veya PowerShell Galerisi komut gibi bir öğe unlisting öğeleri sekmesinden kaldırır. Ayrıca, listede bulunmayan öğeleri arama çubuğunu kullanarak bulunabilirlik olmaz.
Listede bulunmayan bir öğe indirmek için yalnızca tam adı ve sürümü öğenin belirtmek için yoludur.
Bu nedenle, bir öğe unlisting bağımlı komut dosyaları veya diğer modüller kesintiye uğrar değil.

Öğenizi unlist için öğesi Ayrıntılar sayfasını ziyaret edin ve 'Öğeyi sil' seçin. 'Listelendi' onay kutusunun işaretini kaldırın ve Kaydet'i tıklatın.

**Bir öğe nasıl kaldırabilir miyim?**

Öğe silme gerekli olduğu bir senaryo karşılaşırsanız, PowerShell Galerisi yöneticileri ile iletişime geçin.
Geçerli silme senaryolar şunlardır:
- Telif hakkı ihlali sorunları.
- Öğe zararlı içerik içeriyor.
- Öğesi hassas verileri içerir.

Bir silme öğesi isteği PowerShell Galerisi yöneticilere göndermek için öğenizin ayrıntı sayfasını ziyaret edin ve Destek birimine başvurun seçin.