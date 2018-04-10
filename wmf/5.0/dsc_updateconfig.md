---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 27f8fab6a72e7f3a3f510f5a9e503bbfb8a8f618
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a>DSC Yapılandırmalarının isteğe bağlı ÇEKME işlemi

Yeni güncelleştirme DscConfiguration cmdlet meta yapılandırmada tanımlanan çekme sunucuları gelen çekme tetikler. Davranış genellikle 'Pull şimdi ' adlandırılır.


Ne zaman yaptığınız gibi tetiklenen sonra çekme tam olarak aynı şekilde davranır normal sıklıığı tetiklenen:

1. Geçerli yapılandırma için sağlama toplamı çekme sunucusunda yapılandırması için sağlama toplamı karşılaştırılır.
2. Aynı olmaları durumunda yapılandırma uygulamadan başarıyla tamamlanır.
3. Bunlar farklıysa, yapılandırma istek sunucusundan çekilen ve uygulanır.

**Not:** varsa Meta yapılandırma RefreshMode 'Push' = hedef düğüm 'Push' modunda olduğunda bu cmdlet her zaman hiçbir şey yapmaz şekilde Bu cmdlet ile bir hata döndürülür.

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