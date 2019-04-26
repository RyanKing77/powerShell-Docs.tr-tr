---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058752"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Test-DscConfiguration cmdlet'i başvuru yapılandırmalarını destekler

Test-DscConfiguration cmdlet'i, karşılaştırma için bir başvuru yapılandırma belgesini belirterek bir veya daha fazla hedef düğümleri istenen yapılandırma durumunu sınama izin verecek şekilde güncelleştirildi.

Aşağıdaki yeni parametre kümeleri yalnızca test için belirtilen yol DSC yapılandırmaları kullanın ve her yapılandırma belirtilen hedef düğüm üzerinde hiçbir zaman uygulamak. Start-DscConfiguration ve diğer DSC cmdlet'leri gibi her MOF adını üzerinde test yapılandırması için hangi hedef düğümü belirlemek için kullanılır.

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

Aşağıdaki yeni parametre kümeleri yalnızca test ve hiçbir zaman belirtilen hedef düğüm üzerinde yapılandırmayı uygulamak için tek bir DSC yapılandırması kullanın.

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
