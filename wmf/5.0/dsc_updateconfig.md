---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: f2ddde78f436e6f03f521a9a8246dbda93e7a57a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
---
# <a name="on-demand-pull-of-dsc-configurations"></a>İsteğe bağlı ÇEKME DSC yapılandırmaları

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

