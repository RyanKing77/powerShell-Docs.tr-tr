---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="145af-102">Test-DscConfiguration cmdlet başvuru yapılandırmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="145af-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="145af-103">Test-DscConfiguration cmdlet'i karşılaştırma için bir başvuru yapılandırma belgesini belirterek bir veya daha fazla hedef düğümleri istenen yapılandırma durumunu sınama izin vermek için güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="145af-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="145af-104">Aşağıdaki yeni parametre kümeleri yalnızca test için belirtilen yol DSC yapılandırmalarını kullanabilir ve hiçbir zaman her yapılandırma üzerinde belirtilen hedef düğümde uygulamak.</span><span class="sxs-lookup"><span data-stu-id="145af-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="145af-105">Başlangıç DscConfiguration ve diğer DSC cmdlet'leri'te olduğu gibi her MOF adını hangi hedef düğüm üzerinde yapılandırmayı test belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="145af-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="145af-106">Aşağıdaki yeni parametre kümeleri yalnızca sınama ve hiçbir zaman yapılandırmayı belirtilen hedef düğümde uygulamak için tek bir DSC yapılandırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="145af-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
