---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: İşlem Cmdlet’leri ile İşlemleri Yönetme
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: d6d7daa810dce2d476566e4d30f03cc95bf730e6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952503"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="6ad51-103">İşlem Cmdlet’leri ile İşlemleri Yönetme</span><span class="sxs-lookup"><span data-stu-id="6ad51-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="6ad51-104">Windows PowerShell'de yerel ve uzak işlemlerin yönetmek için Windows PowerShell'de işlem cmdlet'lerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ad51-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="6ad51-105">İşlemler (Get-Process) alma</span><span class="sxs-lookup"><span data-stu-id="6ad51-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="6ad51-106">Yerel bilgisayarda çalışan işlemler almak için şunu çalıştırın bir **Get-Process** hiçbir parametre.</span><span class="sxs-lookup"><span data-stu-id="6ad51-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="6ad51-107">İşlem adları veya işlem kimliklerini belirterek belirli işlemleri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ad51-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="6ad51-108">Aşağıdaki komutu boşta işlemi alır:</span><span class="sxs-lookup"><span data-stu-id="6ad51-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="6ad51-109">Bir işlem tarafından kendi ProcessId belirttiğinizde, bazı durumlarda, hiçbir veri döndürmek cmdlet'leri için normal olsa **Get-Process** bilinen bir çalışan işlemi almak için her zamanki hedefi olduğu için herhangi bir eşleşme bulursa bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ad51-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="6ad51-110">Bu kimliğe sahip hiçbir işlem ise olası kimliği hatalı veya ilgi işlemden zaten çıkıldı.:</span><span class="sxs-lookup"><span data-stu-id="6ad51-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="6ad51-111">Get-Process cmdlet'inin Name parametresi, bir alt işlem adına göre işlemlerin belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ad51-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="6ad51-112">Name parametresi birden çok ad virgülle ayrılmış bir liste alabilir ve adı desenleri girebilmeniz için joker karakterleri kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="6ad51-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="6ad51-113">Örneğin, aşağıdaki komut, adları "ex" ile başlayan işlem alır</span><span class="sxs-lookup"><span data-stu-id="6ad51-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="6ad51-114">.NET System.Diagnostics.Process sınıfı Windows PowerShell işlemleri için temel olduğundan, bazı System.Diagnostics.Process tarafından kullanılan kurallara uyar.</span><span class="sxs-lookup"><span data-stu-id="6ad51-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="6ad51-115">Bu kuralları işlem adını yürütülebilir bir dosya için hiçbir zaman ".exe" içeren yürütülebilir adının sonuna biridir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="6ad51-116">**Get-Process** da Name parametresi için birden çok değer kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6ad51-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="6ad51-117">Uzak bilgisayarlarda işlemler almak için Get-Process ComputerName parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ad51-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="6ad51-118">Örneğin, aşağıdaki komutu ("localhost" gösterilir) yerel bilgisayarda PowerShell işlemleri alır ve iki uzak bilgisayarlarda.</span><span class="sxs-lookup"><span data-stu-id="6ad51-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="6ad51-119">Bilgisayar adları bu görüntüde güvenli değildir, ancak Get-Process döndürür işlem nesneleri MachineName özelliğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="6ad51-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="6ad51-120">Aşağıdaki komut, işlem kimliği, işlemadı ve MachineName (ComputerName) görüntülemek için Format-Table cmdlet kullanır. işlem nesnelerin özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="6ad51-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="6ad51-121">Bu daha karmaşık komut standart Get-Process görüntü MachineName özelliği ekler.</span><span class="sxs-lookup"><span data-stu-id="6ad51-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $() {$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="6ad51-122">İşlemler (Stop-Process) durduruluyor</span><span class="sxs-lookup"><span data-stu-id="6ad51-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="6ad51-123">Windows PowerShell işlemleri listeleme, ancak ne bir işlemi durdurmak için esneklik sağlar?</span><span class="sxs-lookup"><span data-stu-id="6ad51-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="6ad51-124">**Stop-Process** cmdlet adı veya kimliği durdurmak istediğiniz bir işlem belirtmek için alır.</span><span class="sxs-lookup"><span data-stu-id="6ad51-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="6ad51-125">İşlemleri durdurmak yeteneğinizi izinlerinize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ad51-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="6ad51-126">Bazı işlemler durdurulamıyor.</span><span class="sxs-lookup"><span data-stu-id="6ad51-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="6ad51-127">Örneğin, boşta işlemi durdurmak çalışırsanız, bir hata alıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="6ad51-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="6ad51-128">İle isteyen zorlayabilirsiniz **Onayla** parametresi.</span><span class="sxs-lookup"><span data-stu-id="6ad51-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="6ad51-129">Bu parametre, yanlışlıkla durdurmak istiyor musunuz. bazı işlemleri eşleşmiyor olabilir çünkü bir joker karakter işlem adı belirtirken kullanırsanız özellikle yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="6ad51-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

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

<span data-ttu-id="6ad51-130">Karmaşık bir işlem işleme cmdlet'leri filtreleme nesne bazıları kullanarak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6ad51-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="6ad51-131">İşlem nesnesi artık yanıt vermiyor olduğunda true olan bir yanıt özelliği olduğundan, yanıt vermeyen tüm uygulamaları aşağıdaki komutla durdurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ad51-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="6ad51-132">Diğer durumlarda aynı yaklaşımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ad51-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="6ad51-133">Örneğin, kullanıcıların başka bir uygulama başlattığınızda ikincil bildirim alanı uygulaması otomatik olarak çalışır varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6ad51-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="6ad51-134">Bu Terminal Hizmetleri oturumlarında düzgün çalışmaz, ancak yine de fiziksel bilgisayar konsolda çalıştırmak oturumlarda tutmak istiyor bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ad51-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="6ad51-135">Fiziksel bilgisayarın masaüstüne her zaman bağlı oturumlar sahip 0, oturum kimliği kullanarak diğer oturumlarda olan tüm örneklerini işlemi durdurmak için **Where-Object** ve işlem **SessionID** :</span><span class="sxs-lookup"><span data-stu-id="6ad51-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="6ad51-136">Stop-Process cmdlet, ComputerName parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="6ad51-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="6ad51-137">Bu nedenle, bir uzak bilgisayarda bir durdurma işlemi komutu çalıştırmak için Invoke-Command cmdlet'i kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="6ad51-138">Örneğin, Server01 uzak bilgisayarda PowerShell işlemi durdurmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ad51-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="6ad51-139">Diğer Windows PowerShell oturumları durdurma</span><span class="sxs-lookup"><span data-stu-id="6ad51-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="6ad51-140">Bazen geçerli oturum dışındaki tüm çalışan Windows PowerShell oturumlarınızı durdurmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="6ad51-141">Bir oturum çok fazla kaynak kullandığını veya erişilebilir değil (Bu çalıştırıyor olabilirsiniz uzaktan veya başka bir masaüstü oturumunda), doğrudan durdurmak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="6ad51-142">Tüm çalışan oturumları durdurmaya çalışırsanız, ancak, geçerli oturum yerine sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="6ad51-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="6ad51-143">Her bir Windows PowerShell oturumu bir ortam değişkeni Windows PowerShell işlem kimliğini içeren PID sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="6ad51-144">Her oturum kimliği karşı $PID kontrol edin ve farklı bir kimliği olan Windows PowerShell oturumları sonlandırma Aşağıdaki ardışık düzen komut bunu yapar ve sonlandırılan oturumların listesini döndürür (kullanımı nedeniyle **PassThru** parametresi):</span><span class="sxs-lookup"><span data-stu-id="6ad51-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

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

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="6ad51-145">Başlangıç, hata ayıklama ve işlemler için bekleniyor</span><span class="sxs-lookup"><span data-stu-id="6ad51-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="6ad51-146">Windows PowerShell cmdlet'leriyle başlatın (veya yeniden başlatmak için), hata ayıklama işlemi ve bir komutu çalıştırmadan önce tamamlamak için bir işlem için bekleme de gelir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="6ad51-147">Bu cmdlet'ler hakkında daha fazla bilgi için her bir cmdlet için cmdlet Yardım konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="6ad51-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ad51-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6ad51-148">See Also</span></span>

- <span data-ttu-id="6ad51-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="6ad51-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="6ad51-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="6ad51-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="6ad51-151">İşlem içi Başlat</span><span class="sxs-lookup"><span data-stu-id="6ad51-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="6ad51-152">Bekleme işlemi</span><span class="sxs-lookup"><span data-stu-id="6ad51-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="6ad51-153">Hata ayıklama işlemi</span><span class="sxs-lookup"><span data-stu-id="6ad51-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="6ad51-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="6ad51-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)