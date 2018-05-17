---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
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
