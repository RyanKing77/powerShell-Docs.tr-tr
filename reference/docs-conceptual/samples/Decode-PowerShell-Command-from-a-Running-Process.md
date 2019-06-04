---
ms.date: 11/13/2018
keywords: PowerShell cmdlet'i
title: PowerShell komutunun kodunu çalışan bir işlemden çözme
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470973"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>PowerShell komutunun kodunu çalışan bir işlemden çözme

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

PowerShell yürütme komutu gövdesi içinde depolanan **CommandLine** özelliği [Win32_Process][] sınıfı. Kodlanmış bir komut komutsa **CommandLine** özelliği "EncodedCommand" dizesini içerir. Bu bilgileri kullanarak, kodlanmış komutu aşağıdaki işlem XML'deki karıştırılmış olabilir.

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
