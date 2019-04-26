---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: İşlem Cmdlet’leri ile İşlemleri Yönetme
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058718"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="8b814-103">İşlem Cmdlet’leri ile İşlemleri Yönetme</span><span class="sxs-lookup"><span data-stu-id="8b814-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="8b814-104">Yerel ve uzak Windows PowerShell işlemleri yönetmek için Windows PowerShell'de işlem cmdlet'leri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b814-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="8b814-105">İşlemlerini (Get-işlem) alma</span><span class="sxs-lookup"><span data-stu-id="8b814-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="8b814-106">Yerel bilgisayarda çalışan işlemlere almak için çalıştırın bir **Get-Process** parametre olmadan.</span><span class="sxs-lookup"><span data-stu-id="8b814-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="8b814-107">İşlem adları veya işlem kimliklerini belirterek belirli işlemleri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b814-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="8b814-108">Aşağıdaki komut, boşta işlemi alır:</span><span class="sxs-lookup"><span data-stu-id="8b814-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="8b814-109">Bir işlem tarafından ProcessId, belirttiğiniz zaman, bazı durumlarda, veri döndürmeyen cmdlet'leri için normal olsa **Get-Process** bilinen bir çalışan işleme almak için her zamanki hedefi olduğu için herhangi bir eşleşme bulduğunda bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b814-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="8b814-110">Bu kimliğe sahip bir işlem yok ise, büyük olasılıkla kimliği yanlış veya ilgi işlemden zaten çıkıldı:</span><span class="sxs-lookup"><span data-stu-id="8b814-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="8b814-111">Get-Process cmdlet'inin Name parametresine bir alt işlemlerin işlem adına göre belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b814-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="8b814-112">Name parametresi, virgülle ayrılmış bir listede birden çok ad alabilir ve adı desenlerinin girebilmeniz için joker karakterler kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="8b814-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="8b814-113">Örneğin, aşağıdaki komut, adları "ör." ile başlayan işlem alır</span><span class="sxs-lookup"><span data-stu-id="8b814-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="8b814-114">Windows PowerShell işlemleri için temel .NET System.Diagnostics.Process sınıfı olduğu için bazı System.Diagnostics.Process tarafından kullanılan kuralları izler.</span><span class="sxs-lookup"><span data-stu-id="8b814-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="8b814-115">Bu kuralları işlem adı bir yürütülebilir dosya için hiçbir zaman ".exe" içeren yürütülebilir adı sonunda biridir.</span><span class="sxs-lookup"><span data-stu-id="8b814-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="8b814-116">**Get-Process** da Name parametresi için birden çok değer kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8b814-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="8b814-117">Uzak bilgisayarlarda işlemleri almak için Get-Process ComputerName parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b814-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="8b814-118">Örneğin, aşağıdaki komutu ("localhost" gösterilir) yerel bilgisayarda PowerShell işlemleri alır ve iki uzak bilgisayarlarda.</span><span class="sxs-lookup"><span data-stu-id="8b814-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="8b814-119">Bilgisayar adları bu görünümde yetkisiz değiştirmeye karşı korumalı değildir, ancak bunlar döndüren Get-Process işlem nesneleri MachineName özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="8b814-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="8b814-120">Aşağıdaki komut, işlem kimliği, ProcessName ve MachineName (ComputerName) görüntülemek için Format-Table cmdlet kullanır. işlem nesnelerin özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="8b814-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="8b814-121">Daha karmaşık bu komut, standart Get-Process görüntülenecek MachineName özelliği ekler.</span><span class="sxs-lookup"><span data-stu-id="8b814-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="8b814-122">Durdurma işlemlerini (Stop-işlem)</span><span class="sxs-lookup"><span data-stu-id="8b814-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="8b814-123">Windows PowerShell işlemleri listeleme, ancak ne işlem durduruluyor. daha fazla esneklik sunar?</span><span class="sxs-lookup"><span data-stu-id="8b814-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="8b814-124">**Stop-Process** cmdlet adı veya kimliği durdurmak istediğiniz bir işlemi belirlemek için alır.</span><span class="sxs-lookup"><span data-stu-id="8b814-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="8b814-125">Yeteneğinizi işlemleri durdurun, izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b814-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="8b814-126">Bazı işlemler durdurulamıyor.</span><span class="sxs-lookup"><span data-stu-id="8b814-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="8b814-127">Örneğin, boşta işlemi durdurmak çalışırsanız hata alırsınız:</span><span class="sxs-lookup"><span data-stu-id="8b814-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="8b814-128">İle isteyen zorlayabilirsiniz **Onayla** parametresi.</span><span class="sxs-lookup"><span data-stu-id="8b814-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="8b814-129">Bu parametre, yanlışlıkla durdurmak istiyor musunuz bazı işlemler aynı olmayabilir çünkü bir joker karakter işlem adı belirtilirken kullanıyorsanız özellikle yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="8b814-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="8b814-130">Bazı cmdlet'ler filtreleme nesnesi kullanarak karmaşık bir işlem işleme mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8b814-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="8b814-131">Bir işlem nesnesi artık yanıt vermediğinde, doğru bir yanıt özelliği olmadığından, aşağıdaki komutla yanıt vermeyen tüm uygulamaları durdurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b814-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="8b814-132">Diğer durumlarda, aynı yaklaşımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b814-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="8b814-133">Örneğin, kullanıcıların başka bir uygulamayı başlattığınızda ikincil bildirim alan uygulamayı otomatik olarak çalıştırır varsayalım.</span><span class="sxs-lookup"><span data-stu-id="8b814-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="8b814-134">Bu doğru Terminal Hizmetleri oturumlarında çalışmaz, ancak yine de fiziksel bilgisayar konsol üzerinde çalıştır oturumlarında tutmak istiyor bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b814-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="8b814-135">Fiziksel bilgisayarın masaüstüne her zaman bağlı oturumlar sahip bir oturum kimliği 0 kullanarak diğer oturumlarda olan tüm işlemin örneği durdurabilirsiniz. Bu nedenle **Where-Object** ve işlem **SessionID** :</span><span class="sxs-lookup"><span data-stu-id="8b814-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="8b814-136">Stop-Process cmdlet, ComputerName parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="8b814-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="8b814-137">Bu nedenle, bir uzak bilgisayarda bir durdurma işlemi komutu çalıştırmak için Invoke-Command cmdlet'ini kullanmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b814-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="8b814-138">Örneğin, Server01 uzak bilgisayarda PowerShell işlemi durdurmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="8b814-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="8b814-139">Diğer Windows PowerShell oturumları durduruluyor</span><span class="sxs-lookup"><span data-stu-id="8b814-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="8b814-140">Bazen geçerli oturumu dışındaki tüm çalışan Windows PowerShell oturumları durdurmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b814-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="8b814-141">Oturum çok fazla kaynak kullanıyorsa veya erişilebilir değil (Bu çalışıyor olabilir uzaktan veya başka bir masaüstü oturumunda), doğrudan durdurmak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8b814-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="8b814-142">Ancak, tüm çalışan oturumları durdurmak denerseniz, geçerli oturumun yerine sonlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b814-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="8b814-143">Her Windows PowerShell oturumu bir ortam değişkenini Windows PowerShell işlem kimliğini içeren PID vardır.</span><span class="sxs-lookup"><span data-stu-id="8b814-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="8b814-144">Her oturum kimliği karşı $PID kontrol edin ve farklı bir kimliğe sahip Windows PowerShell oturumlarını sonlandırır Aşağıdaki işlem hattı komut bunu yapar ve sonlandırılan oturumların listesini döndürür (kullanımı nedeniyle **PassThru** parametresi):</span><span class="sxs-lookup"><span data-stu-id="8b814-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="8b814-145">Başlatılıyor, hata ayıklama ve işlemler için bekleniyor</span><span class="sxs-lookup"><span data-stu-id="8b814-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="8b814-146">Windows PowerShell cmdlet'leriyle başlatın (veya yeniden başlatmak için), hata ayıklama işlemi ve bir komut çalıştırmadan önce tamamlanması bir işlemin tamamlanmasını bekleyin da gelir.</span><span class="sxs-lookup"><span data-stu-id="8b814-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="8b814-147">Bu cmdlet'ler hakkında daha fazla bilgi için her cmdlet için cmdlet Yardım konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="8b814-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b814-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8b814-148">See Also</span></span>

- <span data-ttu-id="8b814-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="8b814-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="8b814-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="8b814-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="8b814-151">İşlemini Başlat</span><span class="sxs-lookup"><span data-stu-id="8b814-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="8b814-152">Bekleme işlemi</span><span class="sxs-lookup"><span data-stu-id="8b814-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="8b814-153">İşlem içi hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8b814-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="8b814-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8b814-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
