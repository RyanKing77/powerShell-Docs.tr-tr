---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Betik İzleme ve Günlüğe Kaydetme
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856157"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="4c4df-103">Betik İzleme ve Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="4c4df-103">Script Tracing and Logging</span></span>

<span data-ttu-id="4c4df-104">PowerShell zaten varken **LogPipelineExecutionDetails** Grup İlkesi cmdlet'leri çağırmayı günlük olarak ayarlanması, PowerShell'in betik oluşturma dili günlük ve denetim için isteyebileceğiniz birkaç özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="4c4df-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="4c4df-105">Yeni betik ayrıntılı izleme özelliği, bir sistemde ayrıntılı izleme ve PowerShell betik etkinliği analizini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c4df-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="4c4df-106">Ayrıntılı betik izlemeyi etkinleştirdikten sonra PowerShell betik bloklarındaki tüm ETW olay günlüğüne kaydeder **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="4c4df-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="4c4df-107">Çağırarak gibi bir betik bloğu başka bir betik bloğu oluşturması halinde `Invoke-Expression`, çağrılan betik bloğundaki da günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4c4df-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="4c4df-108">Günlüğe kaydetme aracılığıyla etkinleştirildiğinde **PowerShell komut dosyası bloğu günlük** Grup İlkesi ayarının **Yönetim Şablonları** -> **Windows bileşenleri**  ->  **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4c4df-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="4c4df-109">Olaylar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4c4df-109">The events are:</span></span>

| <span data-ttu-id="4c4df-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4c4df-110">Channel</span></span> |                               <span data-ttu-id="4c4df-111">İşletimsel</span><span class="sxs-lookup"><span data-stu-id="4c4df-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="4c4df-112">Düzey</span><span class="sxs-lookup"><span data-stu-id="4c4df-112">Level</span></span>   | <span data-ttu-id="4c4df-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="4c4df-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="4c4df-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="4c4df-114">Opcode</span></span>  | <span data-ttu-id="4c4df-115">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c4df-115">Create</span></span>                                                                  |
| <span data-ttu-id="4c4df-116">Görev</span><span class="sxs-lookup"><span data-stu-id="4c4df-116">Task</span></span>    | <span data-ttu-id="4c4df-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="4c4df-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="4c4df-118">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="4c4df-118">Keyword</span></span> | <span data-ttu-id="4c4df-119">Çalışma alanı</span><span class="sxs-lookup"><span data-stu-id="4c4df-119">Runspace</span></span>                                                                |
| <span data-ttu-id="4c4df-120">EventID</span><span class="sxs-lookup"><span data-stu-id="4c4df-120">EventId</span></span> | <span data-ttu-id="4c4df-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="4c4df-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="4c4df-122">İleti</span><span class="sxs-lookup"><span data-stu-id="4c4df-122">Message</span></span> | <span data-ttu-id="4c4df-123">Scriptblock metin (%2'in %1) oluşturma:</span><span class="sxs-lookup"><span data-stu-id="4c4df-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="4c4df-124">%3</span><span class="sxs-lookup"><span data-stu-id="4c4df-124">%3</span></span> </br> <span data-ttu-id="4c4df-125">ScriptBlock kimliği: %4</span><span class="sxs-lookup"><span data-stu-id="4c4df-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="4c4df-126">İletide katıştırılmış derlenmiş betik bloğu kapsamını metindir.</span><span class="sxs-lookup"><span data-stu-id="4c4df-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="4c4df-127">Betik bloğundaki süresince korunur bir GUID kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="4c4df-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="4c4df-128">Ayrıntılı günlüğe yazmayı etkinleştirdiğinizde, özellik yazma başlar ve işaretçileri bitiş:</span><span class="sxs-lookup"><span data-stu-id="4c4df-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="4c4df-129">Kanal</span><span class="sxs-lookup"><span data-stu-id="4c4df-129">Channel</span></span> |                                 <span data-ttu-id="4c4df-130">İşletimsel</span><span class="sxs-lookup"><span data-stu-id="4c4df-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="4c4df-131">Düzey</span><span class="sxs-lookup"><span data-stu-id="4c4df-131">Level</span></span>   | <span data-ttu-id="4c4df-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="4c4df-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="4c4df-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="4c4df-133">Opcode</span></span>  | <span data-ttu-id="4c4df-134">Aç / Kapat</span><span class="sxs-lookup"><span data-stu-id="4c4df-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="4c4df-135">Görev</span><span class="sxs-lookup"><span data-stu-id="4c4df-135">Task</span></span>    | <span data-ttu-id="4c4df-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="4c4df-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="4c4df-137">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="4c4df-137">Keyword</span></span> | <span data-ttu-id="4c4df-138">Çalışma alanı</span><span class="sxs-lookup"><span data-stu-id="4c4df-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="4c4df-139">EventID</span><span class="sxs-lookup"><span data-stu-id="4c4df-139">EventId</span></span> | <span data-ttu-id="4c4df-140">ScriptBlock\_çağırma\_Başlat\_ayrıntısı (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="4c4df-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="4c4df-141">ScriptBlock\_çağırma\_tam\_ayrıntısı (0x100A Sınır = 4106)</span><span class="sxs-lookup"><span data-stu-id="4c4df-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="4c4df-142">İleti</span><span class="sxs-lookup"><span data-stu-id="4c4df-142">Message</span></span> | <span data-ttu-id="4c4df-143">Başlatılan / tamamlandı çağırma ScriptBlock kimliği: %1</span><span class="sxs-lookup"><span data-stu-id="4c4df-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="4c4df-144">Çalışma alanı kimliği: %2</span><span class="sxs-lookup"><span data-stu-id="4c4df-144">Runspace ID: %2</span></span> |

<span data-ttu-id="4c4df-145">Kimliği (yani 0x1008 olay kimliği ile ilişkili olabilir) komut dosyası bloğu temsil eden GUID'dir ve çalışma alanı kimliği bu betik bloğu çalıştırıldığı çalışma temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c4df-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="4c4df-146">Çağırma iletisinin yüzde işaretleri yapılandırılmış ETW özellikleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c4df-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="4c4df-147">İleti metni gerçek değerleri yerine, bunlara erişmek için daha sağlam bir şekilde Get-WinEvent cmdlet'ini ileti alıp ardından açıkken **özellikleri** ileti dizisi.</span><span class="sxs-lookup"><span data-stu-id="4c4df-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="4c4df-148">Bu işlev şifrelemek ve bir betik karartmak için kötü amaçlı bir girişim sarmalamadan çıkarma nasıl yardımcı olabileceğini bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4c4df-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="4c4df-149">Bu çalışan aşağıdaki günlük girişlerini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="4c4df-149">Running this generates the following log entries:</span></span>

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Betik bloğu tek bir olay kapasitesini aşıyor, PowerShell komut dosyası birden çok parçaya keser. <span data-ttu-id="4c4df-151">Günlük iletilerini betikten yeniden birleştirmek için örnek kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4c4df-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="4c4df-152">Sistemlerle sınırlı saklama arabellek sahip tüm günlük olarak, bu altyapısını saldırılara karşı bir önceki kanıt gizlemek için sahte olayları günlükle doldurmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="4c4df-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="4c4df-153">Kendinizi bu saldırılardan korumak için Windows Olay iletme'yi kümesi olay günlüğü koleksiyon çeşit sahip olun.</span><span class="sxs-lookup"><span data-stu-id="4c4df-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="4c4df-154">Daha fazla bilgi için [saldırganın Windows olay günlüğü izleme ile kapsamlı](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="4c4df-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>