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
# <a name="managing-processes-with-process-cmdlets"></a>İşlem Cmdlet’leri ile İşlemleri Yönetme

Windows PowerShell'de yerel ve uzak işlemlerin yönetmek için Windows PowerShell'de işlem cmdlet'lerini kullanabilirsiniz.

## <a name="getting-processes-get-process"></a>İşlemler (Get-Process) alma

Yerel bilgisayarda çalışan işlemler almak için şunu çalıştırın bir **Get-Process** hiçbir parametre.

İşlem adları veya işlem kimliklerini belirterek belirli işlemleri elde edebilirsiniz. Aşağıdaki komutu boşta işlemi alır:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Bir işlem tarafından kendi ProcessId belirttiğinizde, bazı durumlarda, hiçbir veri döndürmek cmdlet'leri için normal olsa **Get-Process** bilinen bir çalışan işlemi almak için her zamanki hedefi olduğu için herhangi bir eşleşme bulursa bir hata oluşturur. Bu kimliğe sahip hiçbir işlem ise olası kimliği hatalı veya ilgi işlemden zaten çıkıldı.:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Get-Process cmdlet'inin Name parametresi, bir alt işlem adına göre işlemlerin belirtmek için kullanabilirsiniz. Name parametresi birden çok ad virgülle ayrılmış bir liste alabilir ve adı desenleri girebilmeniz için joker karakterleri kullanımını destekler.

Örneğin, aşağıdaki komut, adları "ex" ile başlayan işlem alır

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

.NET System.Diagnostics.Process sınıfı Windows PowerShell işlemleri için temel olduğundan, bazı System.Diagnostics.Process tarafından kullanılan kurallara uyar. Bu kuralları işlem adını yürütülebilir bir dosya için hiçbir zaman ".exe" içeren yürütülebilir adının sonuna biridir.

**Get-Process** da Name parametresi için birden çok değer kabul eder.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Uzak bilgisayarlarda işlemler almak için Get-Process ComputerName parametresini kullanabilirsiniz. Örneğin, aşağıdaki komutu ("localhost" gösterilir) yerel bilgisayarda PowerShell işlemleri alır ve iki uzak bilgisayarlarda.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Bilgisayar adları bu görüntüde güvenli değildir, ancak Get-Process döndürür işlem nesneleri MachineName özelliğinde depolanır. Aşağıdaki komut, işlem kimliği, işlemadı ve MachineName (ComputerName) görüntülemek için Format-Table cmdlet kullanır. işlem nesnelerin özelliklerini.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Bu daha karmaşık komut standart Get-Process görüntü MachineName özelliği ekler.

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

## <a name="stopping-processes-stop-process"></a>İşlemler (Stop-Process) durduruluyor

Windows PowerShell işlemleri listeleme, ancak ne bir işlemi durdurmak için esneklik sağlar?

**Stop-Process** cmdlet adı veya kimliği durdurmak istediğiniz bir işlem belirtmek için alır. İşlemleri durdurmak yeteneğinizi izinlerinize bağlıdır. Bazı işlemler durdurulamıyor. Örneğin, boşta işlemi durdurmak çalışırsanız, bir hata alıyorsunuz:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

İle isteyen zorlayabilirsiniz **Onayla** parametresi. Bu parametre, yanlışlıkla durdurmak istiyor musunuz. bazı işlemleri eşleşmiyor olabilir çünkü bir joker karakter işlem adı belirtirken kullanırsanız özellikle yararlıdır:

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

Karmaşık bir işlem işleme cmdlet'leri filtreleme nesne bazıları kullanarak mümkündür. İşlem nesnesi artık yanıt vermiyor olduğunda true olan bir yanıt özelliği olduğundan, yanıt vermeyen tüm uygulamaları aşağıdaki komutla durdurabilirsiniz:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Diğer durumlarda aynı yaklaşımı kullanabilirsiniz. Örneğin, kullanıcıların başka bir uygulama başlattığınızda ikincil bildirim alanı uygulaması otomatik olarak çalışır varsayalım. Bu Terminal Hizmetleri oturumlarında düzgün çalışmaz, ancak yine de fiziksel bilgisayar konsolda çalıştırmak oturumlarda tutmak istiyor bulabilirsiniz. Fiziksel bilgisayarın masaüstüne her zaman bağlı oturumlar sahip 0, oturum kimliği kullanarak diğer oturumlarda olan tüm örneklerini işlemi durdurmak için **Where-Object** ve işlem **SessionID** :

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Stop-Process cmdlet, ComputerName parametresi yok. Bu nedenle, bir uzak bilgisayarda bir durdurma işlemi komutu çalıştırmak için Invoke-Command cmdlet'i kullanmanız gerekebilir. Örneğin, Server01 uzak bilgisayarda PowerShell işlemi durdurmak için şunu yazın:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Diğer Windows PowerShell oturumları durdurma

Bazen geçerli oturum dışındaki tüm çalışan Windows PowerShell oturumlarınızı durdurmak yararlı olabilir. Bir oturum çok fazla kaynak kullandığını veya erişilebilir değil (Bu çalıştırıyor olabilirsiniz uzaktan veya başka bir masaüstü oturumunda), doğrudan durdurmak mümkün olmayabilir. Tüm çalışan oturumları durdurmaya çalışırsanız, ancak, geçerli oturum yerine sonlandırılacak.

Her bir Windows PowerShell oturumu bir ortam değişkeni Windows PowerShell işlem kimliğini içeren PID sahiptir. Her oturum kimliği karşı $PID kontrol edin ve farklı bir kimliği olan Windows PowerShell oturumları sonlandırma Aşağıdaki ardışık düzen komut bunu yapar ve sonlandırılan oturumların listesini döndürür (kullanımı nedeniyle **PassThru** parametresi):

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

## <a name="starting-debugging-and-waiting-for-processes"></a>Başlangıç, hata ayıklama ve işlemler için bekleniyor

Windows PowerShell cmdlet'leriyle başlatın (veya yeniden başlatmak için), hata ayıklama işlemi ve bir komutu çalıştırmadan önce tamamlamak için bir işlem için bekleme de gelir. Bu cmdlet'ler hakkında daha fazla bilgi için her bir cmdlet için cmdlet Yardım konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz:

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [İşlem içi Başlat](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Bekleme işlemi](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Hata ayıklama işlemi](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)