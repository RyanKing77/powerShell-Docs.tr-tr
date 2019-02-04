---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688563"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="77450-102">Test-DscConfiguration cmdlet'i başvuru yapılandırmalarını destekler</span><span class="sxs-lookup"><span data-stu-id="77450-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="77450-103">Test-DscConfiguration cmdlet'i, karşılaştırma için bir başvuru yapılandırma belgesini belirterek bir veya daha fazla hedef düğümleri istenen yapılandırma durumunu sınama izin verecek şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="77450-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="77450-104">Aşağıdaki yeni parametre kümeleri yalnızca test için belirtilen yol DSC yapılandırmaları kullanın ve her yapılandırma belirtilen hedef düğüm üzerinde hiçbir zaman uygulamak.</span><span class="sxs-lookup"><span data-stu-id="77450-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="77450-105">Start-DscConfiguration ve diğer DSC cmdlet'leri gibi her MOF adını üzerinde test yapılandırması için hangi hedef düğümü belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77450-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="77450-106">Aşağıdaki yeni parametre kümeleri yalnızca test ve hiçbir zaman belirtilen hedef düğüm üzerinde yapılandırmayı uygulamak için tek bir DSC yapılandırması kullanın.</span><span class="sxs-lookup"><span data-stu-id="77450-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
