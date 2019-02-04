---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687422"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="28b08-102">Birleşmiş ve Tutarlı Durum ve Durum Gösterimi</span><span class="sxs-lookup"><span data-stu-id="28b08-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="28b08-103">Bir dizi, bu sürümde otomasyonları LCM durumu ve DSC durumu için yapılan.</span><span class="sxs-lookup"><span data-stu-id="28b08-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="28b08-104">Birleşmiş ve tutarlı durum ve duruma temsilleri yönetilebilir datetime özelliği tarafından döndürülen durum nesnelerin bunlar `Get-DscConfigurationStatus` cmdlet ve Gelişmiş LCM durumu ayrıntıları özelliği tarafından döndürülen `Get-DscLocalConfigurationManager` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="28b08-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="28b08-105">LCM durumu ve DSC işlem durumunu gösterimini revisited ve aşağıdaki kurallara göre birleşik:</span><span class="sxs-lookup"><span data-stu-id="28b08-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="28b08-106">LCM durumu ve DSC durumu Notprocessed kaynak etkilemez.</span><span class="sxs-lookup"><span data-stu-id="28b08-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="28b08-107">Yeniden başlatma isteği bir kaynak bulduğu sonra daha fazla işlem kaynaklarının LCM durdur.</span><span class="sxs-lookup"><span data-stu-id="28b08-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="28b08-108">Yeniden başlatma gerçekten oluşuncaya kadar yeniden başlatma isteği bir kaynak istenen durumda değil.</span><span class="sxs-lookup"><span data-stu-id="28b08-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="28b08-109">Başarısız bir bağımlı olmadıkları sürece başarısız olan bir kaynak karşılaştıktan sonra LCM daha fazla işleme kaynaklarına tutar.</span><span class="sxs-lookup"><span data-stu-id="28b08-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="28b08-110">Tarafından döndürülen genel durumunu `Get-DscConfigurationStatus` cmdlet'tir tüm kaynakların durum süper kümesi.</span><span class="sxs-lookup"><span data-stu-id="28b08-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="28b08-111">PendingReboot durumu PendingConfiguration durumu bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="28b08-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="28b08-112">Sonuç aşağıdaki tabloda gösterilmiştir durum ilgili bazı tipik senaryoları altındaki özellikler.</span><span class="sxs-lookup"><span data-stu-id="28b08-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="28b08-113">Senaryo</span><span class="sxs-lookup"><span data-stu-id="28b08-113">Scenario</span></span>                        | <span data-ttu-id="28b08-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="28b08-114">LCMState</span></span>             | <span data-ttu-id="28b08-115">Durum</span><span class="sxs-lookup"><span data-stu-id="28b08-115">Status</span></span>     | <span data-ttu-id="28b08-116">İstenen yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="28b08-116">Reboot Requested</span></span> | <span data-ttu-id="28b08-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="28b08-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="28b08-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="28b08-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="28b08-119">S<sub>ediyorum</sub></span><span class="sxs-lookup"><span data-stu-id="28b08-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="28b08-120">Boşta</span><span class="sxs-lookup"><span data-stu-id="28b08-120">Idle</span></span>                 | <span data-ttu-id="28b08-121">Başarılı</span><span class="sxs-lookup"><span data-stu-id="28b08-121">Success</span></span>    | <span data-ttu-id="28b08-122">$false</span><span class="sxs-lookup"><span data-stu-id="28b08-122">$false</span></span>        | <span data-ttu-id="28b08-123">S</span><span class="sxs-lookup"><span data-stu-id="28b08-123">S</span></span>                            | <span data-ttu-id="28b08-124">$null</span><span class="sxs-lookup"><span data-stu-id="28b08-124">$null</span></span>                          |
| <span data-ttu-id="28b08-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="28b08-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="28b08-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="28b08-126">PendingConfiguration</span></span> | <span data-ttu-id="28b08-127">Başarısız</span><span class="sxs-lookup"><span data-stu-id="28b08-127">Failure</span></span>    | <span data-ttu-id="28b08-128">$false</span><span class="sxs-lookup"><span data-stu-id="28b08-128">$false</span></span>        | <span data-ttu-id="28b08-129">$null</span><span class="sxs-lookup"><span data-stu-id="28b08-129">$null</span></span>                        | <span data-ttu-id="28b08-130">F</span><span class="sxs-lookup"><span data-stu-id="28b08-130">F</span></span>                              |
| <span data-ttu-id="28b08-131">S, F</span><span class="sxs-lookup"><span data-stu-id="28b08-131">S,F</span></span>                             | <span data-ttu-id="28b08-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="28b08-132">PendingConfiguration</span></span> | <span data-ttu-id="28b08-133">Başarısız</span><span class="sxs-lookup"><span data-stu-id="28b08-133">Failure</span></span>    | <span data-ttu-id="28b08-134">$false</span><span class="sxs-lookup"><span data-stu-id="28b08-134">$false</span></span>        | <span data-ttu-id="28b08-135">S</span><span class="sxs-lookup"><span data-stu-id="28b08-135">S</span></span>                            | <span data-ttu-id="28b08-136">F</span><span class="sxs-lookup"><span data-stu-id="28b08-136">F</span></span>                              |
| <span data-ttu-id="28b08-137">F,S</span><span class="sxs-lookup"><span data-stu-id="28b08-137">F,S</span></span>                             | <span data-ttu-id="28b08-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="28b08-138">PendingConfiguration</span></span> | <span data-ttu-id="28b08-139">Başarısız</span><span class="sxs-lookup"><span data-stu-id="28b08-139">Failure</span></span>    | <span data-ttu-id="28b08-140">$false</span><span class="sxs-lookup"><span data-stu-id="28b08-140">$false</span></span>        | <span data-ttu-id="28b08-141">S</span><span class="sxs-lookup"><span data-stu-id="28b08-141">S</span></span>                            | <span data-ttu-id="28b08-142">F</span><span class="sxs-lookup"><span data-stu-id="28b08-142">F</span></span>                              |
| <span data-ttu-id="28b08-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="28b08-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="28b08-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="28b08-144">PendingConfiguration</span></span> | <span data-ttu-id="28b08-145">Başarısız</span><span class="sxs-lookup"><span data-stu-id="28b08-145">Failure</span></span>    | <span data-ttu-id="28b08-146">$false</span><span class="sxs-lookup"><span data-stu-id="28b08-146">$false</span></span>        | <span data-ttu-id="28b08-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="28b08-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="28b08-148">F</span><span class="sxs-lookup"><span data-stu-id="28b08-148">F</span></span>                              |
| <span data-ttu-id="28b08-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="28b08-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="28b08-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="28b08-150">PendingConfiguration</span></span> | <span data-ttu-id="28b08-151">Başarısız</span><span class="sxs-lookup"><span data-stu-id="28b08-151">Failure</span></span>    | <span data-ttu-id="28b08-152">$false</span><span class="sxs-lookup"><span data-stu-id="28b08-152">$false</span></span>        | <span data-ttu-id="28b08-153">S</span><span class="sxs-lookup"><span data-stu-id="28b08-153">S</span></span>                            | <span data-ttu-id="28b08-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="28b08-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="28b08-155">S, r</span><span class="sxs-lookup"><span data-stu-id="28b08-155">S, r</span></span>                            | <span data-ttu-id="28b08-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="28b08-156">PendingReboot</span></span>        | <span data-ttu-id="28b08-157">Başarılı</span><span class="sxs-lookup"><span data-stu-id="28b08-157">Success</span></span>    | <span data-ttu-id="28b08-158">$true</span><span class="sxs-lookup"><span data-stu-id="28b08-158">$true</span></span>         | <span data-ttu-id="28b08-159">S</span><span class="sxs-lookup"><span data-stu-id="28b08-159">S</span></span>                            | <span data-ttu-id="28b08-160">r</span><span class="sxs-lookup"><span data-stu-id="28b08-160">r</span></span>                              |
| <span data-ttu-id="28b08-161">F, r</span><span class="sxs-lookup"><span data-stu-id="28b08-161">F, r</span></span>                            | <span data-ttu-id="28b08-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="28b08-162">PendingReboot</span></span>        | <span data-ttu-id="28b08-163">Başarısız</span><span class="sxs-lookup"><span data-stu-id="28b08-163">Failure</span></span>    | <span data-ttu-id="28b08-164">$true</span><span class="sxs-lookup"><span data-stu-id="28b08-164">$true</span></span>         | <span data-ttu-id="28b08-165">$null</span><span class="sxs-lookup"><span data-stu-id="28b08-165">$null</span></span>                        | <span data-ttu-id="28b08-166">F, r</span><span class="sxs-lookup"><span data-stu-id="28b08-166">F, r</span></span>                           |
| <span data-ttu-id="28b08-167">r, S</span><span class="sxs-lookup"><span data-stu-id="28b08-167">r, S</span></span>                            | <span data-ttu-id="28b08-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="28b08-168">PendingReboot</span></span>        | <span data-ttu-id="28b08-169">Başarılı</span><span class="sxs-lookup"><span data-stu-id="28b08-169">Success</span></span>    | <span data-ttu-id="28b08-170">$true</span><span class="sxs-lookup"><span data-stu-id="28b08-170">$true</span></span>         | <span data-ttu-id="28b08-171">$null</span><span class="sxs-lookup"><span data-stu-id="28b08-171">$null</span></span>                        | <span data-ttu-id="28b08-172">r</span><span class="sxs-lookup"><span data-stu-id="28b08-172">r</span></span>                              |
| <span data-ttu-id="28b08-173">r, F</span><span class="sxs-lookup"><span data-stu-id="28b08-173">r, F</span></span>                            | <span data-ttu-id="28b08-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="28b08-174">PendingReboot</span></span>        | <span data-ttu-id="28b08-175">Başarılı</span><span class="sxs-lookup"><span data-stu-id="28b08-175">Success</span></span>    | <span data-ttu-id="28b08-176">$true</span><span class="sxs-lookup"><span data-stu-id="28b08-176">$true</span></span>         | <span data-ttu-id="28b08-177">$null</span><span class="sxs-lookup"><span data-stu-id="28b08-177">$null</span></span>                        | <span data-ttu-id="28b08-178">r</span><span class="sxs-lookup"><span data-stu-id="28b08-178">r</span></span>                              |

- <span data-ttu-id="28b08-179">S<sub>miyim</sub>: Bir dizi başarıyla uygulandı kaynakları</span><span class="sxs-lookup"><span data-stu-id="28b08-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="28b08-180">F<sub>miyim</sub>: Bir dizi başarısız uygulanan kaynakları</span><span class="sxs-lookup"><span data-stu-id="28b08-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="28b08-181">r: Yeniden başlatma gerektiren bir kaynak</span><span class="sxs-lookup"><span data-stu-id="28b08-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="28b08-182">Get-DscConfigurationStatus cmdlet'inde geliştirme</span><span class="sxs-lookup"><span data-stu-id="28b08-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="28b08-183">Birkaç iyileştirme yapılmıştır `Get-DscConfigurationStatus` cmdlet'i bu sürümde.</span><span class="sxs-lookup"><span data-stu-id="28b08-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="28b08-184">Önceden, StartDate özelliği cmdlet'i tarafından döndürülen nesnelerin dize türünde değil.</span><span class="sxs-lookup"><span data-stu-id="28b08-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="28b08-185">Şimdi, sadece karmaşık seçme ve daha kolay bir Datetime nesnesini iç özelliklerde göre filtrelemeyi sağlayan Datetime türü değil.</span><span class="sxs-lookup"><span data-stu-id="28b08-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="28b08-186">Aşağıdaki örnek, aynı gün haftanın geçerli günü olarak gerçekleşen tüm DSC işlemi kayıtları döndürür.</span><span class="sxs-lookup"><span data-stu-id="28b08-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="28b08-187">Geçersiz kayıt işlemlerinin (yani yalnızca işlem okuma) düğümün yapılandırmasını değişiklik yapmayın.</span><span class="sxs-lookup"><span data-stu-id="28b08-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="28b08-188">Bu nedenle, `Test-DscConfiguration`, `Get-DscConfiguration` operations artık, döndürülen nesneleri adulterated `Get-DscConfigurationStatus` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="28b08-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="28b08-189">Kayıtları meta yapılandırma ayarı işleminin dönüşü için eklenen `Get-DscConfigurationStatus` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="28b08-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="28b08-190">Öğesinden döndürülen sonuç örneği aşağıdadır `Get-DscConfigurationStatus –All` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="28b08-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="28b08-191">Get-DscLocalConfigurationManager cmdlet'i geliştirmesi</span><span class="sxs-lookup"><span data-stu-id="28b08-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="28b08-192">Yönteminden döndürülen nesne LCMStateDetail yeni bir alan eklenir `Get-DscLocalConfigurationManager` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="28b08-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="28b08-193">LCMState "Meşgul" olduğunda bu alan doldurulur.</span><span class="sxs-lookup"><span data-stu-id="28b08-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="28b08-194">Aşağıdaki cmdlet'i tarafından alınabilir:</span><span class="sxs-lookup"><span data-stu-id="28b08-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="28b08-195">Bir sürekli uzak bir düğüm üzerinde iki yeniden başlatma gerektiren bir yapılandırma izleme bir örnek çıktı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="28b08-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
