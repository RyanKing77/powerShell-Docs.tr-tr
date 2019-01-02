---
ms.date: 11/13/2018
keywords: PowerShell cmdlet'i
title: PowerShell komutunun kodunu çalışan bir işlemden çözme
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405706"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="1b449-103">PowerShell komutunun kodunu çalışan bir işlemden çözme</span><span class="sxs-lookup"><span data-stu-id="1b449-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="1b449-104">Bazen, bir PowerShell kaynaklarının büyük bir miktarını, çalışan işlem sürüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b449-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="1b449-105">Bu işlem bağlamında çalışıyor olabilir bir [Görev Zamanlayıcı][] işi veya [SQL Server Agent][] işi.</span><span class="sxs-lookup"><span data-stu-id="1b449-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="1b449-106">Çalışan birden çok PowerShell işlemleri olduğu, hangi işlem sorunu temsil ettiği anlamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b449-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="1b449-107">Bu makalede, PowerShell işlem şu anda çalışan bir betik bloğu çözülecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b449-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="1b449-108">Uzun süre çalışan işlem oluştur</span><span class="sxs-lookup"><span data-stu-id="1b449-108">Create a long running process</span></span>

<span data-ttu-id="1b449-109">Bu senaryoyu göstermek için yeni bir PowerShell penceresi açın ve aşağıdaki kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1b449-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="1b449-110">Bu, birkaç dakikada 10 dakika çıkarır bir PowerShell komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="1b449-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="1b449-111">İşlem görünümü</span><span class="sxs-lookup"><span data-stu-id="1b449-111">View the process</span></span>

<span data-ttu-id="1b449-112">PowerShell yürütme komutu gövdesi içinde depolanan **CommandLine** özelliği [Win32_Process][] sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1b449-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="1b449-113">Komut ise bir [kodlanmış komut][], **CommandLine** özelliği "EncodedCommand" dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b449-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="1b449-114">Bu bilgileri kullanarak, kodlanmış komutu aşağıdaki işlem XML'deki karıştırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b449-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="1b449-115">PowerShell'i yönetici olarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="1b449-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="1b449-116">PowerShell'i yönetici olarak çalıştığından önemlidir, aksi takdirde sonuç çalışan işlemler sorgulanırken döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1b449-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="1b449-117">Tüm kodlanmış bir komut PowerShell işlemleri almak için aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="1b449-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="1b449-118">Aşağıdaki komut, işlem kimliği ve kodlanmış komut içeren özel bir PowerShell nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b449-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="1b449-119">Artık kodlanmış komut çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="1b449-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="1b449-120">Aşağıdaki kod parçacığı komut ayrıntıları nesnesi üzerinde yinelenir, kodlanmış komutu kodunu çözer ve kodu çözülmüş komut araştırılması için nesneye ekler.</span><span class="sxs-lookup"><span data-stu-id="1b449-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="1b449-121">Kodu çözülen komutu artık kodu çözülmüş komut özelliğini seçerek incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="1b449-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Görev Zamanlayıcı]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[kodlanmış komut]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
