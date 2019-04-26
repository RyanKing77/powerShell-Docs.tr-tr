---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057579"
---
# <a name="on-demand-pull-of-dsc-configurations"></a>DSC Yapılandırmalarının isteğe bağlı ÇEKME işlemi

Yeni güncelleştirme-DscConfiguration cmdlet'i bir çekme meta yapılandırmasında tanımlı çekme sunucuları işlemini tetikler. Davranış genellikle 'Pull şimdi ' adlandırılır.


Ne zaman yaptığınız gibi tetiklenen sonra çekme tam olarak aynı şekilde davranır normal sıklıığı tetikleyen:

1. Geçerli yapılandırma için sağlama toplamı çekme sunucusunda yapılandırma için sağlama toplamı karşılaştırılır.
2. Aynı olmaları durumunda yapılandırma uygulamadan başarıyla tamamlar.
3. Bunlar farklıysa, yapılandırma çekme sunucusundan aşağı çektiğiniz ve uygulanır.

**Not:** Yapılandırma Meta RefreshMode 'Push' = hedef düğüme 'Push' modunda olduğunda bu cmdlet her zaman nothing kadar bu cmdlet'i tarafından döndürülen bir hata oluştu.

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
