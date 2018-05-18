---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 272843efb68c42105af6eb88ad6a95b581da47ae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="468a6-102">Birleşmiş ve Tutarlı Durum ve Durum Gösterimi</span><span class="sxs-lookup"><span data-stu-id="468a6-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="468a6-103">Bir dizi, yerleşik LCM'yi durumu ve DSC durum otomasyonlara yönelik bu sürümde yapılan.</span><span class="sxs-lookup"><span data-stu-id="468a6-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="468a6-104">Birleştirilmiş ve tutarlı durumunu ve durum Beyanları bunlar, yönetilebilir datetime özelliği durum nesne Get-DscConfigurationStatus cmdlet tarafından döndürülen ve Get-DscLocalConfigurationManager tarafından döndürülen LCM'yi durumu ayrıntıları özelliği Gelişmiş cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="468a6-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by Get-DscConfigurationStatus cmdlet and enhanced LCM state details property returned by Get-DscLocalConfigurationManager cmdlet.</span></span>

<span data-ttu-id="468a6-105">LCM'yi durumu ve DSC işlem durumunu gösterimini tekrar ziyaret ve aşağıdaki kurallara göre birleşik:</span><span class="sxs-lookup"><span data-stu-id="468a6-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>
1.  <span data-ttu-id="468a6-106">Notprocessed kaynak LCM'yi durumu ve DSC durumunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="468a6-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2.  <span data-ttu-id="468a6-107">Yeniden başlatma istekleri kaynak bulduğu sonra daha fazla işleme kaynaklarına LCM'yi durdurun.</span><span class="sxs-lookup"><span data-stu-id="468a6-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3.  <span data-ttu-id="468a6-108">Yeniden başlatma gerçekte işlem yapılana kadar yeniden başlatma istekleri kaynak istenilen durumda değil.</span><span class="sxs-lookup"><span data-stu-id="468a6-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4.  <span data-ttu-id="468a6-109">Başarısız bir bağımlı olmadıkları sürece, başarısız bir kaynağa karşılaşmadan sonra LCM'yi kaynakları işlenmesi tutar.</span><span class="sxs-lookup"><span data-stu-id="468a6-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5.  <span data-ttu-id="468a6-110">Get-DscConfigurationStatus cmdlet tarafından döndürülen genel durumu tüm kaynakların durum Süper kümesidir.</span><span class="sxs-lookup"><span data-stu-id="468a6-110">The overall status returned by Get-DscConfigurationStatus cmdlet is the super set of all resources’ status.</span></span>
6.  <span data-ttu-id="468a6-111">PendingReboot durumu PendingConfiguration durumunun bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="468a6-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="468a6-112">Aşağıdaki tabloda sonuç gösterilmiştir durum ilgili birkaç tipik senaryolar altında özellikleri.</span><span class="sxs-lookup"><span data-stu-id="468a6-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="468a6-113">**Senaryo**</span><span class="sxs-lookup"><span data-stu-id="468a6-113">**Scenario**</span></span>                    | <span data-ttu-id="468a6-114">**LCMState\***</span><span class="sxs-lookup"><span data-stu-id="468a6-114">**LCMState\***</span></span>       | <span data-ttu-id="468a6-115">**Durumu**</span><span class="sxs-lookup"><span data-stu-id="468a6-115">**Status**</span></span> | <span data-ttu-id="468a6-116">**İstenen yeniden başlatma**</span><span class="sxs-lookup"><span data-stu-id="468a6-116">**Reboot Requested**</span></span>  | <span data-ttu-id="468a6-117">**ResourcesInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="468a6-117">**ResourcesInDesiredState**</span></span>  | <span data-ttu-id="468a6-118">**ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="468a6-118">**ResourcesNotInDesiredState**</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="468a6-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="468a6-119">S**^**</span></span>                          | <span data-ttu-id="468a6-120">Boşta</span><span class="sxs-lookup"><span data-stu-id="468a6-120">Idle</span></span>                 | <span data-ttu-id="468a6-121">Başarılı</span><span class="sxs-lookup"><span data-stu-id="468a6-121">Success</span></span>    | <span data-ttu-id="468a6-122">$false</span><span class="sxs-lookup"><span data-stu-id="468a6-122">$false</span></span>        | <span data-ttu-id="468a6-123">S</span><span class="sxs-lookup"><span data-stu-id="468a6-123">S</span></span>                            | <span data-ttu-id="468a6-124">$null</span><span class="sxs-lookup"><span data-stu-id="468a6-124">$null</span></span>                          |
| <span data-ttu-id="468a6-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="468a6-125">F**^**</span></span>                          | <span data-ttu-id="468a6-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="468a6-126">PendingConfiguration</span></span> | <span data-ttu-id="468a6-127">Başarısız</span><span class="sxs-lookup"><span data-stu-id="468a6-127">Failure</span></span>    | <span data-ttu-id="468a6-128">$false</span><span class="sxs-lookup"><span data-stu-id="468a6-128">$false</span></span>        | <span data-ttu-id="468a6-129">$null</span><span class="sxs-lookup"><span data-stu-id="468a6-129">$null</span></span>                        | <span data-ttu-id="468a6-130">F</span><span class="sxs-lookup"><span data-stu-id="468a6-130">F</span></span>                              |
| <span data-ttu-id="468a6-131">S, F</span><span class="sxs-lookup"><span data-stu-id="468a6-131">S,F</span></span>                             | <span data-ttu-id="468a6-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="468a6-132">PendingConfiguration</span></span> | <span data-ttu-id="468a6-133">Başarısız</span><span class="sxs-lookup"><span data-stu-id="468a6-133">Failure</span></span>    | <span data-ttu-id="468a6-134">$false</span><span class="sxs-lookup"><span data-stu-id="468a6-134">$false</span></span>        | <span data-ttu-id="468a6-135">S</span><span class="sxs-lookup"><span data-stu-id="468a6-135">S</span></span>                            | <span data-ttu-id="468a6-136">F</span><span class="sxs-lookup"><span data-stu-id="468a6-136">F</span></span>                              |
| <span data-ttu-id="468a6-137">F, S</span><span class="sxs-lookup"><span data-stu-id="468a6-137">F,S</span></span>                             | <span data-ttu-id="468a6-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="468a6-138">PendingConfiguration</span></span> | <span data-ttu-id="468a6-139">Başarısız</span><span class="sxs-lookup"><span data-stu-id="468a6-139">Failure</span></span>    | <span data-ttu-id="468a6-140">$false</span><span class="sxs-lookup"><span data-stu-id="468a6-140">$false</span></span>        | <span data-ttu-id="468a6-141">S</span><span class="sxs-lookup"><span data-stu-id="468a6-141">S</span></span>                            | <span data-ttu-id="468a6-142">F</span><span class="sxs-lookup"><span data-stu-id="468a6-142">F</span></span>                              |
| <span data-ttu-id="468a6-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="468a6-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="468a6-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="468a6-144">PendingConfiguration</span></span> | <span data-ttu-id="468a6-145">Başarısız</span><span class="sxs-lookup"><span data-stu-id="468a6-145">Failure</span></span>    | <span data-ttu-id="468a6-146">$false</span><span class="sxs-lookup"><span data-stu-id="468a6-146">$false</span></span>        | <span data-ttu-id="468a6-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="468a6-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="468a6-148">F</span><span class="sxs-lookup"><span data-stu-id="468a6-148">F</span></span>                              |
| <span data-ttu-id="468a6-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="468a6-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="468a6-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="468a6-150">PendingConfiguration</span></span> | <span data-ttu-id="468a6-151">Başarısız</span><span class="sxs-lookup"><span data-stu-id="468a6-151">Failure</span></span>    | <span data-ttu-id="468a6-152">$false</span><span class="sxs-lookup"><span data-stu-id="468a6-152">$false</span></span>        | <span data-ttu-id="468a6-153">S</span><span class="sxs-lookup"><span data-stu-id="468a6-153">S</span></span>                            | <span data-ttu-id="468a6-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="468a6-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="468a6-155">S, r</span><span class="sxs-lookup"><span data-stu-id="468a6-155">S, r</span></span>                            | <span data-ttu-id="468a6-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="468a6-156">PendingReboot</span></span>        | <span data-ttu-id="468a6-157">Başarılı</span><span class="sxs-lookup"><span data-stu-id="468a6-157">Success</span></span>    | <span data-ttu-id="468a6-158">$true</span><span class="sxs-lookup"><span data-stu-id="468a6-158">$true</span></span>         | <span data-ttu-id="468a6-159">S</span><span class="sxs-lookup"><span data-stu-id="468a6-159">S</span></span>                            | <span data-ttu-id="468a6-160">R</span><span class="sxs-lookup"><span data-stu-id="468a6-160">r</span></span>                              |
| <span data-ttu-id="468a6-161">F, r</span><span class="sxs-lookup"><span data-stu-id="468a6-161">F, r</span></span>                            | <span data-ttu-id="468a6-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="468a6-162">PendingReboot</span></span>        | <span data-ttu-id="468a6-163">Başarısız</span><span class="sxs-lookup"><span data-stu-id="468a6-163">Failure</span></span>    | <span data-ttu-id="468a6-164">$true</span><span class="sxs-lookup"><span data-stu-id="468a6-164">$true</span></span>         | <span data-ttu-id="468a6-165">$null</span><span class="sxs-lookup"><span data-stu-id="468a6-165">$null</span></span>                        | <span data-ttu-id="468a6-166">F, r</span><span class="sxs-lookup"><span data-stu-id="468a6-166">F, r</span></span>                           |
| <span data-ttu-id="468a6-167">r, S</span><span class="sxs-lookup"><span data-stu-id="468a6-167">r, S</span></span>                            | <span data-ttu-id="468a6-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="468a6-168">PendingReboot</span></span>        | <span data-ttu-id="468a6-169">Başarılı</span><span class="sxs-lookup"><span data-stu-id="468a6-169">Success</span></span>    | <span data-ttu-id="468a6-170">$true</span><span class="sxs-lookup"><span data-stu-id="468a6-170">$true</span></span>         | <span data-ttu-id="468a6-171">$null</span><span class="sxs-lookup"><span data-stu-id="468a6-171">$null</span></span>                        | <span data-ttu-id="468a6-172">R</span><span class="sxs-lookup"><span data-stu-id="468a6-172">r</span></span>                              |
| <span data-ttu-id="468a6-173">r, F</span><span class="sxs-lookup"><span data-stu-id="468a6-173">r, F</span></span>                            | <span data-ttu-id="468a6-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="468a6-174">PendingReboot</span></span>        | <span data-ttu-id="468a6-175">Başarılı</span><span class="sxs-lookup"><span data-stu-id="468a6-175">Success</span></span>    | <span data-ttu-id="468a6-176">$true</span><span class="sxs-lookup"><span data-stu-id="468a6-176">$true</span></span>         | <span data-ttu-id="468a6-177">$null</span><span class="sxs-lookup"><span data-stu-id="468a6-177">$null</span></span>                        | <span data-ttu-id="468a6-178">R</span><span class="sxs-lookup"><span data-stu-id="468a6-178">r</span></span>                              |

<span data-ttu-id="468a6-179">^ S<sub>ı</sub>: F başarıyla uygulandı kaynakları bir dizi<sub>ı</sub>: bir dizi başarısız yeniden başlatma gerektiren r: A kaynak uygulanan kaynakları \*</span><span class="sxs-lookup"><span data-stu-id="468a6-179">^ S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="468a6-180">Get-DscConfigurationStatus cmdlet'i geliştirme</span><span class="sxs-lookup"><span data-stu-id="468a6-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="468a6-181">Get-DscConfigurationStatus cmdlet'i bu sürümde bazı geliştirmeler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="468a6-181">A few enhancements have been made to Get-DscConfigurationStatus cmdlet in this release.</span></span> <span data-ttu-id="468a6-182">Daha önce StartDate, cmdlet tarafından döndürülen nesnelerin dize türünde özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="468a6-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="468a6-183">Şimdi, seçerek ve daha kolay bir Datetime nesnesi iç özellikleri göre filtreleme karmaşık etkinleştirir Datetime türünde değil.</span><span class="sxs-lookup"><span data-stu-id="468a6-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="468a6-184">Aşağıdaki tüm DSC işlemi kayıtları bugün olarak haftanın aynı gün içinde gerçekleşen döndüren bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="468a6-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="468a6-185">Kayıtları (yani yalnızca işlemleri okuma) düğümün yapılandırma değişiklik yapmayın işlemlerinin ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="468a6-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="468a6-186">Bu nedenle, Test-DscConfiguration, Get-DscConfiguration işlemleri artık içinde adulterated Get-DscConfigurationStatus cmdlet'i nesne döndürmedi.</span><span class="sxs-lookup"><span data-stu-id="468a6-186">Therefore, Test-DscConfiguration, Get-DscConfiguration operations are no longer adulterated in returned objects from Get-DscConfigurationStatus cmdlet.</span></span>
<span data-ttu-id="468a6-187">Meta yapılandırmasını ayarlama işlemini kayıtlarının Get-DscConfigurationStatus cmdlet'i geri dönmek için eklenir.</span><span class="sxs-lookup"><span data-stu-id="468a6-187">Records of meta configuration setting operation is added to the return of Get-DscConfigurationStatus cmdlet.</span></span>

<span data-ttu-id="468a6-188">Get-DscConfigurationStatus döndürülen sonuç örneği aşağıdadır – tüm cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="468a6-188">Following is an example of result returned from Get-DscConfigurationStatus –All cmdlet.</span></span>
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="468a6-189">Get-DscLocalConfigurationManager cmdlet'i geliştirme</span><span class="sxs-lookup"><span data-stu-id="468a6-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>
<span data-ttu-id="468a6-190">Yeni bir alan LCMStateDetail, Get-DscLocalConfigurationManager cmdlet'i döndürülen nesne eklenir.</span><span class="sxs-lookup"><span data-stu-id="468a6-190">A new field of LCMStateDetail is added to the object returned from Get-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="468a6-191">Bu alan, LCMState "Meşgul" olduğunda doldurulur.</span><span class="sxs-lookup"><span data-stu-id="468a6-191">This field is populated when LCMState is “Busy”.</span></span> <span data-ttu-id="468a6-192">Aşağıdaki cmdlet'i tarafından alınabilir:</span><span class="sxs-lookup"><span data-stu-id="468a6-192">It can be retrieved by following cmdlet:</span></span>
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="468a6-193">Aşağıda, bir sürekli uzak bir düğüm üzerindeki iki yeniden başlatma gerektiren bir yapılandırma izleme bir örnek çıktı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="468a6-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>
```powershell
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
