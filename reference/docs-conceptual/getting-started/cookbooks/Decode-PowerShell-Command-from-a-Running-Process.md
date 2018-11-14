---
ms.date: 11/13/2018
keywords: PowerShell cmdlet'i
title: Bir PowerShell komutu çalışan bir işlemden kodunu çözme
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619265"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Bir PowerShell komutu çalışan bir işlemden kodunu çözme

Bazen, bir PowerShell kaynaklarının büyük bir miktarını, çalışan işlem sürüyor olabilir.
Bu işlem bağlamında çalışıyor olabilir bir [Görev Zamanlayıcısı][] işi veya [SQL Server Aracısı][] işi. Çalışan birden çok PowerShell işlemleri olduğu, hangi işlem sorunu temsil ettiği anlamak zor olabilir. Bu makalede, PowerShell işlem şu anda çalışan bir betik bloğu çözülecek gösterilmektedir.

## <a name="create-a-long-running-process"></a>Uzun süre çalışan işlem oluştur

Bu senaryoyu göstermek için yeni bir PowerShell penceresi açın ve aşağıdaki kodu çalıştırın. Bu, birkaç dakikada 10 dakika çıkarır bir PowerShell komutu yürütür.

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

## <a name="view-the-process"></a>İşlem görünümü

PowerShell yürütme komutu gövdesi içinde depolanan **CommandLine** özelliği [Win32_Process][] sınıfı. Komut ise bir [Kodlanmış komutu][], **CommandLine** özelliği "EncodedCommand" dizesini içerir. Bu bilgileri kullanarak, kodlanmış komutu aşağıdaki işlem XML'deki karıştırılmış olabilir.

PowerShell'i yönetici olarak başlatın. PowerShell'i yönetici olarak çalıştığından önemlidir, aksi takdirde sonuç çalışan işlemler sorgulanırken döndürülür.

Tüm kodlanmış bir komut PowerShell işlemleri almak için aşağıdaki komutu yürütün:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

Aşağıdaki komut, işlem kimliği ve kodlanmış komut içeren özel bir PowerShell nesnesi oluşturur.

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

Artık kodlanmış komut çözülebilir. Aşağıdaki kod parçacığı komut ayrıntıları nesnesi üzerinde yinelenir, kodlanmış komutu kodunu çözer ve kodu çözülmüş komut araştırılması için nesneye ekler.

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

Kodu çözülen komutu artık kodu çözülmüş komut özelliğini seçerek incelenebilir.

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

[Görev Zamanlayıcısı]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Aracısı]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[Kodlanmış komutu]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
