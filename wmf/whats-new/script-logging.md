---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Betik İzleme ve Günlüğe Kaydetme
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856157"
---
# <a name="script-tracing-and-logging"></a>Betik İzleme ve Günlüğe Kaydetme

PowerShell zaten varken **LogPipelineExecutionDetails** Grup İlkesi cmdlet'leri çağırmayı günlük olarak ayarlanması, PowerShell'in betik oluşturma dili günlük ve denetim için isteyebileceğiniz birkaç özellik vardır. Yeni betik ayrıntılı izleme özelliği, bir sistemde ayrıntılı izleme ve PowerShell betik etkinliği analizini sağlar. Ayrıntılı betik izlemeyi etkinleştirdikten sonra PowerShell betik bloklarındaki tüm ETW olay günlüğüne kaydeder **Microsoft-Windows-PowerShell/Operational**. Çağırarak gibi bir betik bloğu başka bir betik bloğu oluşturması halinde `Invoke-Expression`, çağrılan betik bloğundaki da günlüğe kaydedilir.

Günlüğe kaydetme aracılığıyla etkinleştirildiğinde **PowerShell komut dosyası bloğu günlük** Grup İlkesi ayarının **Yönetim Şablonları** -> **Windows bileşenleri**  ->  **Windows PowerShell**.

Olaylar şunlardır:

| Kanal |                               İşletimsel                               |
| ------- | ----------------------------------------------------------------------- |
| Düzey   | Verbose                                                                 |
| Opcode  | Oluşturma                                                                  |
| Görev    | CommandStart                                                            |
| Anahtar sözcüğü | Çalışma alanı                                                                |
| EventID | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| İleti | Scriptblock metin (%2'in %1) oluşturma: </br> %3 </br> ScriptBlock kimliği: %4 |


İletide katıştırılmış derlenmiş betik bloğu kapsamını metindir. Betik bloğundaki süresince korunur bir GUID kimliğidir.

Ayrıntılı günlüğe yazmayı etkinleştirdiğinizde, özellik yazma başlar ve işaretçileri bitiş:

| Kanal |                                 İşletimsel                                |
| ------- | -------------------------------------------------------------------------- |
| Düzey   | Verbose                                                                    |
| Opcode  | Aç / Kapat                                                               |
| Görev    | CommandStart / CommandStop                                                 |
| Anahtar sözcüğü | Çalışma alanı                                                                   |
| EventID | ScriptBlock\_çağırma\_Başlat\_ayrıntısı (0x1009 = 4105) / </br> ScriptBlock\_çağırma\_tam\_ayrıntısı (0x100A Sınır = 4106) |
| İleti | Başlatılan / tamamlandı çağırma ScriptBlock kimliği: %1 </br> Çalışma alanı kimliği: %2 |

Kimliği (yani 0x1008 olay kimliği ile ilişkili olabilir) komut dosyası bloğu temsil eden GUID'dir ve çalışma alanı kimliği bu betik bloğu çalıştırıldığı çalışma temsil eder.

Çağırma iletisinin yüzde işaretleri yapılandırılmış ETW özellikleri temsil eder. İleti metni gerçek değerleri yerine, bunlara erişmek için daha sağlam bir şekilde Get-WinEvent cmdlet'ini ileti alıp ardından açıkken **özellikleri** ileti dizisi.

Bu işlev şifrelemek ve bir betik karartmak için kötü amaçlı bir girişim sarmalamadan çıkarma nasıl yardımcı olabileceğini bir örnek aşağıda verilmiştir:

```powershell
## Malware
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

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

Bu çalışan aşağıdaki günlük girişlerini oluşturur:

```Output
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

Betik bloğu tek bir olay kapasitesini aşıyor, PowerShell komut dosyası birden çok parçaya keser. Günlük iletilerini betikten yeniden birleştirmek için örnek kod aşağıda verilmiştir:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Sistemlerle sınırlı saklama arabellek sahip tüm günlük olarak, bu altyapısını saldırılara karşı bir önceki kanıt gizlemek için sahte olayları günlükle doldurmak için yoludur. Kendinizi bu saldırılardan korumak için Windows Olay iletme'yi kümesi olay günlüğü koleksiyon çeşit sahip olun. Daha fazla bilgi için [saldırganın Windows olay günlüğü izleme ile kapsamlı](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).