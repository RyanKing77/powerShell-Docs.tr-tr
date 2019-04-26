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
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="fe88b-102">DSC Yapılandırmalarının isteğe bağlı ÇEKME işlemi</span><span class="sxs-lookup"><span data-stu-id="fe88b-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="fe88b-103">Yeni güncelleştirme-DscConfiguration cmdlet'i bir çekme meta yapılandırmasında tanımlı çekme sunucuları işlemini tetikler.</span><span class="sxs-lookup"><span data-stu-id="fe88b-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="fe88b-104">Davranış genellikle 'Pull şimdi ' adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fe88b-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="fe88b-105">Ne zaman yaptığınız gibi tetiklenen sonra çekme tam olarak aynı şekilde davranır normal sıklıığı tetikleyen:</span><span class="sxs-lookup"><span data-stu-id="fe88b-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="fe88b-106">Geçerli yapılandırma için sağlama toplamı çekme sunucusunda yapılandırma için sağlama toplamı karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="fe88b-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="fe88b-107">Aynı olmaları durumunda yapılandırma uygulamadan başarıyla tamamlar.</span><span class="sxs-lookup"><span data-stu-id="fe88b-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="fe88b-108">Bunlar farklıysa, yapılandırma çekme sunucusundan aşağı çektiğiniz ve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe88b-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="fe88b-109">**Not:** Yapılandırma Meta RefreshMode 'Push' = hedef düğüme 'Push' modunda olduğunda bu cmdlet her zaman nothing kadar bu cmdlet'i tarafından döndürülen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fe88b-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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
