---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 18c1dab7412b8e9d31960507b612dd6cc56d31d5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Test-DscConfiguration cmdlet başvuru yapılandırmayı destekler.

Test-DscConfiguration cmdlet'i karşılaştırma için bir başvuru yapılandırma belgesini belirterek bir veya daha fazla hedef düğümleri istenen yapılandırma durumunu sınama izin vermek için güncelleştirilmiştir.

Aşağıdaki yeni parametre kümeleri yalnızca test için belirtilen yol DSC yapılandırmalarını kullanabilir ve hiçbir zaman her yapılandırma üzerinde belirtilen hedef düğümde uygulamak. Başlangıç DscConfiguration ve diğer DSC cmdlet'leri'te olduğu gibi her MOF adını hangi hedef düğüm üzerinde yapılandırmayı test belirlemek için kullanılır.

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

Aşağıdaki yeni parametre kümeleri yalnızca sınama ve hiçbir zaman yapılandırmayı belirtilen hedef düğümde uygulamak için tek bir DSC yapılandırması kullanın.

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```