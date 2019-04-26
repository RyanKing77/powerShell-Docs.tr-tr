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
# <a name="script-tracing-and-logging"></a>Betik İzleme ve Günlüğe Kaydetme

Windows PowerShell zaten varken **LogPipelineExecutionDetails** Grup İlkesi cmdlet'leri çağırmayı oturum ayarlama, PowerShell'in betik oluşturma dili, oturum ve/veya denetim isteyebilirsiniz özelliklerinin yeterince sahiptir. Yeni betik ayrıntılı izleme özelliği, ayrıntılı izleme ve çözümleme sisteminde Windows PowerShell komut dosyası kullanımı etkinleştirmenize olanak tanır. Ayrıntılı betik izlemeyi etkinleştirdikten sonra Windows PowerShell tüm betik bloklarını ETW olay günlüğüne kaydeder. **Microsoft-Windows-PowerShell/Operational**. Bir betik bloğu başka bir betik bloğu (örneğin, bir dizesine Invokeinline-Expression cmdlet'ini çağıran bir betik) oluşturuyorsa, ortaya çıkan bu betik bloğu de günlüğe kaydedilir.

Bu olayların günlüğe kaydedilmesi aracılığıyla etkinleştirilebilir **PowerShell komut dosyası bloğu günlük** Grup İlkesi ayarı (Yönetici Şablonları -> Windows bileşenleri Windows PowerShell ->).

Olaylar şunlardır:

| Kanal | İşletimsel                                 |
|---------|---------------------------------------------|
| Düzey   | Ayrıntılı                                     |
| Opcode  | Oluşturma                                      |
| Görev    | CommandStart                                |
| Anahtar sözcüğü | Çalışma alanı                                    |
| EventID | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| İleti | Scriptblock metin (%2'in %1) oluşturma: </br> %3 </br> ScriptBlock kimliği: %4 |


İletide katıştırılmış derlenmiş betik bloğu kapsamını metindir. Betik bloğundaki süresince korunur bir GUID kimliğidir.

Ayrıntılı günlüğe yazmayı etkinleştirdiğinizde, özellik yazma başlar ve işaretçileri bitiş:

| Kanal | İşletimsel                                            |
|---------|--------------------------------------------------------|
| Düzey   | Ayrıntılı                                                |
| Opcode  | Açık (/ Kapat)                                         |
| Görev    | CommandStart (/ CommandStop)                           |
| Anahtar sözcüğü | Çalışma alanı                                               |
| EventID | ScriptBlock\_çağırma\_Başlat\_ayrıntısı (0x1009 = 4105) / </br> ScriptBlock\_çağırma\_tam\_ayrıntısı (0x100A Sınır = 4106) |
| İleti | Kullanmaya başlama (/ tamamlanmış) çağırma ScriptBlock kimliği: %1 </br> Çalışma alanı kimliği: %2 |

Kimliği (yani 0x1008 olay kimliği ile ilişkili olabilir) komut dosyası bloğu temsil eden GUID'dir ve çalışma alanı kimliği bu betik bloğu çalıştırıldığı çalışma temsil eder.

Çağırma iletisinin yüzde işaretleri yapılandırılmış ETW özellikleri temsil eder. İleti metni gerçek değerleri yerine, bunlara erişmek için daha sağlam bir şekilde Get-WinEvent cmdlet'ini ileti alıp ardından açıkken **özellikleri** ileti dizisi.

Bu işlev şifrelemek ve bir betik karartmak için kötü amaçlı bir girişim sarmalamadan çıkarma nasıl yardımcı olabileceğini bir örnek aşağıda verilmiştir:

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

Bu çalışan aşağıdaki günlük girişlerini oluşturur:

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

ETW tutan tek bir olay yeteneğine nedir betik bloğu uzunluğu aşıyor, Windows PowerShell komut dosyası birden çok parçaya keser. Günlük iletilerini betikten yeniden birleştirmek için örnek kod aşağıda verilmiştir:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Sistemlerle sınırlı saklama arabellek (yani, ETW günlükleri) olan tüm günlük olarak, önceki kanıt gizlemek için sahte olayları günlükle doldurmak için bu altyapı karşı bir saldırı olduğunu. Bu saldırıya karşı korunmak için ayarlanmış olay günlüğü koleksiyon çeşit olduğundan emin olun (yani, Windows Olay iletme'yi [saldırganın Windows olay günlüğü izleme ile kapsamlı](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) olay günlükleri bilgisayarı olarak dışına taşımak için mümkün olduğunca çabuk.
