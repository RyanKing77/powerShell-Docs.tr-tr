---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: İşlem Cmdlet’leri ile İşlemleri Yönetme
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: 417b5a40cde51029de9ed8e005732978d92c9057
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46013150"
---
# <a name="managing-processes-with-process-cmdlets"></a>İşlem Cmdlet’leri ile İşlemleri Yönetme

Yerel ve uzak Windows PowerShell işlemleri yönetmek için Windows PowerShell'de işlem cmdlet'leri kullanın.

## <a name="getting-processes-get-process"></a>İşlemlerini (Get-işlem) alma

Yerel bilgisayarda çalışan işlemlere almak için çalıştırın bir **Get-Process** parametre olmadan.

İşlem adları veya işlem kimliklerini belirterek belirli işlemleri elde edebilirsiniz. Aşağıdaki komut, boşta işlemi alır:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Bir işlem tarafından ProcessId, belirttiğiniz zaman, bazı durumlarda, veri döndürmeyen cmdlet'leri için normal olsa **Get-Process** bilinen bir çalışan işleme almak için her zamanki hedefi olduğu için herhangi bir eşleşme bulduğunda bir hata oluşturur. Bu kimliğe sahip bir işlem yok ise, büyük olasılıkla kimliği yanlış veya ilgi işlemden zaten çıkıldı:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Get-Process cmdlet'inin Name parametresine bir alt işlemlerin işlem adına göre belirtmek için kullanabilirsiniz. Name parametresi, virgülle ayrılmış bir listede birden çok ad alabilir ve adı desenlerinin girebilmeniz için joker karakterler kullanımını destekler.

Örneğin, aşağıdaki komut, adları "ör." ile başlayan işlem alır

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Windows PowerShell işlemleri için temel .NET System.Diagnostics.Process sınıfı olduğu için bazı System.Diagnostics.Process tarafından kullanılan kuralları izler. Bu kuralları işlem adı bir yürütülebilir dosya için hiçbir zaman ".exe" içeren yürütülebilir adı sonunda biridir.

**Get-Process** da Name parametresi için birden çok değer kabul eder.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Uzak bilgisayarlarda işlemleri almak için Get-Process ComputerName parametresini kullanabilirsiniz. Örneğin, aşağıdaki komutu ("localhost" gösterilir) yerel bilgisayarda PowerShell işlemleri alır ve iki uzak bilgisayarlarda.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Bilgisayar adları bu görünümde yetkisiz değiştirmeye karşı korumalı değildir, ancak bunlar döndüren Get-Process işlem nesneleri MachineName özelliğinde depolanır. Aşağıdaki komut, işlem kimliği, ProcessName ve MachineName (ComputerName) görüntülemek için Format-Table cmdlet kullanır. işlem nesnelerin özelliklerini.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Daha karmaşık bu komut, standart Get-Process görüntülenecek MachineName özelliği ekler.

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

## <a name="stopping-processes-stop-process"></a>Durdurma işlemlerini (Stop-işlem)

Windows PowerShell işlemleri listeleme, ancak ne işlem durduruluyor. daha fazla esneklik sunar?

**Stop-Process** cmdlet adı veya kimliği durdurmak istediğiniz bir işlemi belirlemek için alır. Yeteneğinizi işlemleri durdurun, izinlerine bağlıdır. Bazı işlemler durdurulamıyor. Örneğin, boşta işlemi durdurmak çalışırsanız hata alırsınız:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

İle isteyen zorlayabilirsiniz **Onayla** parametresi. Bu parametre, yanlışlıkla durdurmak istiyor musunuz bazı işlemler aynı olmayabilir çünkü bir joker karakter işlem adı belirtilirken kullanıyorsanız özellikle yararlı olur:

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

Bazı cmdlet'ler filtreleme nesnesi kullanarak karmaşık bir işlem işleme mümkündür. Bir işlem nesnesi artık yanıt vermediğinde, doğru bir yanıt özelliği olmadığından, aşağıdaki komutla yanıt vermeyen tüm uygulamaları durdurabilirsiniz:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Diğer durumlarda, aynı yaklaşımı kullanabilirsiniz. Örneğin, kullanıcıların başka bir uygulamayı başlattığınızda ikincil bildirim alan uygulamayı otomatik olarak çalıştırır varsayalım. Bu doğru Terminal Hizmetleri oturumlarında çalışmaz, ancak yine de fiziksel bilgisayar konsol üzerinde çalıştır oturumlarında tutmak istiyor bulabilirsiniz. Fiziksel bilgisayarın masaüstüne her zaman bağlı oturumlar sahip bir oturum kimliği 0 kullanarak diğer oturumlarda olan tüm işlemin örneği durdurabilirsiniz. Bu nedenle **Where-Object** ve işlem **SessionID** :

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Stop-Process cmdlet, ComputerName parametresi yok. Bu nedenle, bir uzak bilgisayarda bir durdurma işlemi komutu çalıştırmak için Invoke-Command cmdlet'ini kullanmak gerekir. Örneğin, Server01 uzak bilgisayarda PowerShell işlemi durdurmak için şunu yazın:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Diğer Windows PowerShell oturumları durduruluyor

Bazen geçerli oturumu dışındaki tüm çalışan Windows PowerShell oturumları durdurmak yararlı olabilir. Oturum çok fazla kaynak kullanıyorsa veya erişilebilir değil (Bu çalışıyor olabilir uzaktan veya başka bir masaüstü oturumunda), doğrudan durdurmak mümkün olmayabilir. Ancak, tüm çalışan oturumları durdurmak denerseniz, geçerli oturumun yerine sonlandırılabilir.

Her Windows PowerShell oturumu bir ortam değişkenini Windows PowerShell işlem kimliğini içeren PID vardır. Her oturum kimliği karşı $PID kontrol edin ve farklı bir kimliğe sahip Windows PowerShell oturumlarını sonlandırır Aşağıdaki işlem hattı komut bunu yapar ve sonlandırılan oturumların listesini döndürür (kullanımı nedeniyle **PassThru** parametresi):

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

## <a name="starting-debugging-and-waiting-for-processes"></a>Başlatılıyor, hata ayıklama ve işlemler için bekleniyor

Windows PowerShell cmdlet'leriyle başlatın (veya yeniden başlatmak için), hata ayıklama işlemi ve bir komut çalıştırmadan önce tamamlanması bir işlemin tamamlanmasını bekleyin da gelir. Bu cmdlet'ler hakkında daha fazla bilgi için her cmdlet için cmdlet Yardım konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz:

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [İşlemini Başlat](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Bekleme işlemi](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [İşlem içi hata ayıklama](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
