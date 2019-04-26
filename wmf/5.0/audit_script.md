---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058089"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="ac85b-102">Betik İzleme ve Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="ac85b-102">Script Tracing and Logging</span></span>

<span data-ttu-id="ac85b-103">Windows PowerShell zaten varken **LogPipelineExecutionDetails** Grup İlkesi cmdlet'leri çağırmayı oturum ayarlama, PowerShell'in betik oluşturma dili, oturum ve/veya denetim isteyebilirsiniz özelliklerinin yeterince sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ac85b-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="ac85b-104">Yeni betik ayrıntılı izleme özelliği, ayrıntılı izleme ve çözümleme sisteminde Windows PowerShell komut dosyası kullanımı etkinleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ac85b-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="ac85b-105">Ayrıntılı betik izlemeyi etkinleştirdikten sonra Windows PowerShell tüm betik bloklarını ETW olay günlüğüne kaydeder. **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="ac85b-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="ac85b-106">Bir betik bloğu başka bir betik bloğu (örneğin, bir dizesine Invokeinline-Expression cmdlet'ini çağıran bir betik) oluşturuyorsa, ortaya çıkan bu betik bloğu de günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ac85b-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="ac85b-107">Bu olayların günlüğe kaydedilmesi aracılığıyla etkinleştirilebilir **PowerShell komut dosyası bloğu günlük** Grup İlkesi ayarı (Yönetici Şablonları -> Windows bileşenleri Windows PowerShell ->).</span><span class="sxs-lookup"><span data-stu-id="ac85b-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="ac85b-108">Olaylar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ac85b-108">The events are:</span></span>

| <span data-ttu-id="ac85b-109">Kanal</span><span class="sxs-lookup"><span data-stu-id="ac85b-109">Channel</span></span> | <span data-ttu-id="ac85b-110">İşletimsel</span><span class="sxs-lookup"><span data-stu-id="ac85b-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="ac85b-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="ac85b-111">Level</span></span>   | <span data-ttu-id="ac85b-112">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ac85b-112">Verbose</span></span>                                     |
| <span data-ttu-id="ac85b-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="ac85b-113">Opcode</span></span>  | <span data-ttu-id="ac85b-114">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac85b-114">Create</span></span>                                      |
| <span data-ttu-id="ac85b-115">Görev</span><span class="sxs-lookup"><span data-stu-id="ac85b-115">Task</span></span>    | <span data-ttu-id="ac85b-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="ac85b-116">CommandStart</span></span>                                |
| <span data-ttu-id="ac85b-117">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="ac85b-117">Keyword</span></span> | <span data-ttu-id="ac85b-118">Çalışma alanı</span><span class="sxs-lookup"><span data-stu-id="ac85b-118">Runspace</span></span>                                    |
| <span data-ttu-id="ac85b-119">EventID</span><span class="sxs-lookup"><span data-stu-id="ac85b-119">EventId</span></span> | <span data-ttu-id="ac85b-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="ac85b-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="ac85b-121">İleti</span><span class="sxs-lookup"><span data-stu-id="ac85b-121">Message</span></span> | <span data-ttu-id="ac85b-122">Scriptblock metin (%2'in %1) oluşturma:</span><span class="sxs-lookup"><span data-stu-id="ac85b-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="ac85b-123">%3</span><span class="sxs-lookup"><span data-stu-id="ac85b-123">%3</span></span> </br> <span data-ttu-id="ac85b-124">ScriptBlock kimliği: %4</span><span class="sxs-lookup"><span data-stu-id="ac85b-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="ac85b-125">İletide katıştırılmış derlenmiş betik bloğu kapsamını metindir.</span><span class="sxs-lookup"><span data-stu-id="ac85b-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="ac85b-126">Betik bloğundaki süresince korunur bir GUID kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="ac85b-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="ac85b-127">Ayrıntılı günlüğe yazmayı etkinleştirdiğinizde, özellik yazma başlar ve işaretçileri bitiş:</span><span class="sxs-lookup"><span data-stu-id="ac85b-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="ac85b-128">Kanal</span><span class="sxs-lookup"><span data-stu-id="ac85b-128">Channel</span></span> | <span data-ttu-id="ac85b-129">İşletimsel</span><span class="sxs-lookup"><span data-stu-id="ac85b-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="ac85b-130">Düzey</span><span class="sxs-lookup"><span data-stu-id="ac85b-130">Level</span></span>   | <span data-ttu-id="ac85b-131">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ac85b-131">Verbose</span></span>                                                |
| <span data-ttu-id="ac85b-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="ac85b-132">Opcode</span></span>  | <span data-ttu-id="ac85b-133">Açık (/ Kapat)</span><span class="sxs-lookup"><span data-stu-id="ac85b-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="ac85b-134">Görev</span><span class="sxs-lookup"><span data-stu-id="ac85b-134">Task</span></span>    | <span data-ttu-id="ac85b-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="ac85b-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="ac85b-136">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="ac85b-136">Keyword</span></span> | <span data-ttu-id="ac85b-137">Çalışma alanı</span><span class="sxs-lookup"><span data-stu-id="ac85b-137">Runspace</span></span>                                               |
| <span data-ttu-id="ac85b-138">EventID</span><span class="sxs-lookup"><span data-stu-id="ac85b-138">EventId</span></span> | <span data-ttu-id="ac85b-139">ScriptBlock\_çağırma\_Başlat\_ayrıntısı (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="ac85b-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="ac85b-140">ScriptBlock\_çağırma\_tam\_ayrıntısı (0x100A Sınır = 4106)</span><span class="sxs-lookup"><span data-stu-id="ac85b-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="ac85b-141">İleti</span><span class="sxs-lookup"><span data-stu-id="ac85b-141">Message</span></span> | <span data-ttu-id="ac85b-142">Kullanmaya başlama (/ tamamlanmış) çağırma ScriptBlock kimliği: %1</span><span class="sxs-lookup"><span data-stu-id="ac85b-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="ac85b-143">Çalışma alanı kimliği: %2</span><span class="sxs-lookup"><span data-stu-id="ac85b-143">Runspace ID: %2</span></span> |

<span data-ttu-id="ac85b-144">Kimliği (yani 0x1008 olay kimliği ile ilişkili olabilir) komut dosyası bloğu temsil eden GUID'dir ve çalışma alanı kimliği bu betik bloğu çalıştırıldığı çalışma temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ac85b-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="ac85b-145">Çağırma iletisinin yüzde işaretleri yapılandırılmış ETW özellikleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ac85b-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="ac85b-146">İleti metni gerçek değerleri yerine, bunlara erişmek için daha sağlam bir şekilde Get-WinEvent cmdlet'ini ileti alıp ardından açıkken **özellikleri** ileti dizisi.</span><span class="sxs-lookup"><span data-stu-id="ac85b-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="ac85b-147">Bu işlev şifrelemek ve bir betik karartmak için kötü amaçlı bir girişim sarmalamadan çıkarma nasıl yardımcı olabileceğini bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ac85b-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
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

<span data-ttu-id="ac85b-148">Bu çalışan aşağıdaki günlük girişlerini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ac85b-148">Running this generates the following log entries:</span></span>

```
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

ETW tutan tek bir olay yeteneğine nedir betik bloğu uzunluğu aşıyor, Windows PowerShell komut dosyası birden çok parçaya keser. <span data-ttu-id="ac85b-150">Günlük iletilerini betikten yeniden birleştirmek için örnek kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ac85b-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="ac85b-151">Sistemlerle sınırlı saklama arabellek (yani, ETW günlükleri) olan tüm günlük olarak, önceki kanıt gizlemek için sahte olayları günlükle doldurmak için bu altyapı karşı bir saldırı olduğunu.</span><span class="sxs-lookup"><span data-stu-id="ac85b-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="ac85b-152">Bu saldırıya karşı korunmak için ayarlanmış olay günlüğü koleksiyon çeşit olduğundan emin olun (yani, Windows Olay iletme'yi [saldırganın Windows olay günlüğü izleme ile kapsamlı](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) olay günlükleri bilgisayarı olarak dışına taşımak için mümkün olduğunca çabuk.</span><span class="sxs-lookup"><span data-stu-id="ac85b-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
