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
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="f9853-102">İsteğe bağlı ÇEKME DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="f9853-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="f9853-103">Yeni güncelleştirme DscConfiguration cmdlet meta yapılandırmada tanımlanan çekme sunucuları gelen çekme tetikler.</span><span class="sxs-lookup"><span data-stu-id="f9853-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="f9853-104">Davranış genellikle 'Pull şimdi ' adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f9853-104">The behavior is often referred to as 'Pull Now'.</span></span> 


<span data-ttu-id="f9853-105">Ne zaman yaptığınız gibi tetiklenen sonra çekme tam olarak aynı şekilde davranır normal sıklıığı tetiklenen:</span><span class="sxs-lookup"><span data-stu-id="f9853-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="f9853-106">Geçerli yapılandırma için sağlama toplamı çekme sunucusunda yapılandırması için sağlama toplamı karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="f9853-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span> 
2. <span data-ttu-id="f9853-107">Aynı olmaları durumunda yapılandırma uygulamadan başarıyla tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="f9853-107">If they are the same, it completes successfully without applying the configuration.</span></span> 
3. <span data-ttu-id="f9853-108">Bunlar farklıysa, yapılandırma istek sunucusundan çekilen ve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f9853-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="f9853-109">**Not:** varsa Meta yapılandırma RefreshMode 'Push' = hedef düğüm 'Push' modunda olduğunda bu cmdlet her zaman hiçbir şey yapmaz şekilde Bu cmdlet ile bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f9853-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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

