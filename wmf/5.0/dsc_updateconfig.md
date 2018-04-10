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
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="54cd9-102">DSC Yapılandırmalarının isteğe bağlı ÇEKME işlemi</span><span class="sxs-lookup"><span data-stu-id="54cd9-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="54cd9-103">Yeni güncelleştirme DscConfiguration cmdlet meta yapılandırmada tanımlanan çekme sunucuları gelen çekme tetikler.</span><span class="sxs-lookup"><span data-stu-id="54cd9-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="54cd9-104">Davranış genellikle 'Pull şimdi ' adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="54cd9-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="54cd9-105">Ne zaman yaptığınız gibi tetiklenen sonra çekme tam olarak aynı şekilde davranır normal sıklıığı tetiklenen:</span><span class="sxs-lookup"><span data-stu-id="54cd9-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="54cd9-106">Geçerli yapılandırma için sağlama toplamı çekme sunucusunda yapılandırması için sağlama toplamı karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="54cd9-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="54cd9-107">Aynı olmaları durumunda yapılandırma uygulamadan başarıyla tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="54cd9-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="54cd9-108">Bunlar farklıysa, yapılandırma istek sunucusundan çekilen ve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="54cd9-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="54cd9-109">**Not:** varsa Meta yapılandırma RefreshMode 'Push' = hedef düğüm 'Push' modunda olduğunda bu cmdlet her zaman hiçbir şey yapmaz şekilde Bu cmdlet ile bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="54cd9-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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