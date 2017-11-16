---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
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

