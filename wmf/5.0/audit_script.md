---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2627b9d02788bd31a5384587406df533faf2cfaf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="script-tracing-and-logging"></a>Betik İzleme ve Günlüğe Kaydetme

Windows PowerShell zaten varken **LogPipelineExecutionDetails** Grup İlkesi cmdlet'leri çağırma oturum ayarlama, PowerShell'in komut dosyası dili oturum ve/veya denetim isteyebilirsiniz özellikleri Eskinin sahiptir. Yeni betik ayrıntılı izleme özelliği, ayrıntılı izleme ve çözümleme sisteminde Windows PowerShell komut dosyası kullanımı olanak tanır. Ayrıntılı betik izleme etkinleştirdikten sonra Windows PowerShell tüm komut dosyası blokları ETW olay günlüğüne kaydeder. **Microsoft-Windows-PowerShell/Operational**. Bir betik bloğu başka bir betik bloğu (örneğin, bir dizesine Invoke-Expression cmdlet'ini çağıran bir betik) oluşturursa, sonuçta elde edilen bu betik bloğu da günlüğe kaydedilir.

Bu olayların günlüğe kaydedilmesi, aracılığıyla etkinleştirilebilir **PowerShell betik bloğu günlük özelliğini açın** Grup İlkesi ayarı (Yönetim Şablonları -> Windows bileşenlerini Windows PowerShell ->).

Olaylar şunlardır:

| Kanal | İşletimsel                                 |
|---------|---------------------------------------------|
| Düzey   | Verbose                                     |
| İşlem kodu  | Oluşturma                                      |
| Görev    | CommandStart                                |
| Anahtar sözcüğü | Çalışma alanı                                    |
| Olay Kimliği | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| İleti | Scriptblock metin (%1% 2) oluşturma: </br> %3 </br> ScriptBlock kimliği: %4 |


İletiye ekli derlenmiş betik bloğu kapsamını metindir. Betik bloğu yaşam süreleri boyunca tutulur bir GUID kimliğidir.

Ayrıntılı günlük kaydını etkinleştirdiğinizde, özellik yazma başlamak ve işaretçileri bitiş:

| Kanal | İşletimsel                                            |
|---------|--------------------------------------------------------|
| Düzey   | Verbose                                                |
| İşlem kodu  | Açın (/ Kapat)                                         |
| Görev    | CommandStart (/ CommandStop)                           |
| Anahtar sözcüğü | Çalışma alanı                                               |
| Olay Kimliği | ScriptBlock\_çağırma\_Başlat\_ayrıntı (0x1009 = 4105) / </br> ScriptBlock\_çağırma\_tam\_ayrıntı (0x100A Sınır = 4106) |
| İleti | Başlarken (/ tamamlanmış) çağırma ScriptBlock kimliği: %1 </br> Çalışma alanı kimliği: %2 |

Kimliği (olay kimliği 0x1008 ile ilişkili olabilir) betik bloğu temsil eden GUID'dir ve çalışma alanı kimliği bu betik bloğu çalıştırıldı çalışma alanı temsil eder.

Çağırma iletisinin yüzde işaretleri yapılandırılmış ETW özelliklerini temsil eder. İleti metni gerçek değerler ile değiştirilir, bunlara erişmek için daha sağlam bir şekilde Get-WinEvent cmdlet'ini iletisiyle almak ve daha sonra kullanmak için açıkken **özellikleri** ileti dizisi.

Bu işlev bir komut dosyası belirsizleştirirseniz ve şifrelemek için bir kötü amaçlı girişimi kaydırma nasıl yardımcı olabileceğini örneği şöyledir:

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

Bu çalıştığını aşağıdaki günlük girişlerini oluşturur:

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

Betik bloğu uzunluğu ETW tek bir olay tutan yeteneğine nedir aşarsa, Windows PowerShell komut dosyası birden çok bölüme ayırır. Kendi günlük iletilerini betikten rahatça için örnek kod aşağıda verilmiştir:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Sistemleriyle sınırlı bekletme arabellek (yani ETW günlükleri) sahip tüm günlük olarak, önceki kanıt gizlemek için alacaklardır olaylarla günlük bölgesini doldurmak için bu altyapı karşı bir saldırı olduğunu. Bu saldırıya karşı korunmak için ayarlanan olay günlüğü koleksiyonunu çeşit olduğundan emin olun (yani, Windows Olay iletme'yi [Windows olay günlüğünü izleme ile birlikte etkilemeyi belirleme](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) olay günlükleri bilgisayarı olarak dışına taşımak için mümkün olduğunca çabuk.
