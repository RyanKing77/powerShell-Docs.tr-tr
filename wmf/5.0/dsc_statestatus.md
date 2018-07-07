---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0e8d0cb1e4afa7bc791d45bfb0b981654cb09ed5
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892578"
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Birleşmiş ve Tutarlı Durum ve Durum Gösterimi

Bir dizi, bu sürümde otomasyonları LCM durumu ve DSC durumu için yapılan. Birleşmiş ve tutarlı durum ve duruma temsilleri yönetilebilir datetime özelliği tarafından döndürülen durum nesnelerin bunlar `Get-DscConfigurationStatus` cmdlet ve Gelişmiş LCM durumu ayrıntıları özelliği tarafından döndürülen `Get-DscLocalConfigurationManager` cmdlet'i.

LCM durumu ve DSC işlem durumunu gösterimini revisited ve aşağıdaki kurallara göre birleşik:

1. LCM durumu ve DSC durumu Notprocessed kaynak etkilemez.
2. Yeniden başlatma isteği bir kaynak bulduğu sonra daha fazla işlem kaynaklarının LCM durdur.
3. Yeniden başlatma gerçekten oluşuncaya kadar yeniden başlatma isteği bir kaynak istenen durumda değil.
4. Başarısız bir bağımlı olmadıkları sürece başarısız olan bir kaynak karşılaştıktan sonra LCM daha fazla işleme kaynaklarına tutar.
5. Tarafından döndürülen genel durumunu `Get-DscConfigurationStatus` cmdlet'tir tüm kaynakların durum süper kümesi.
6. PendingReboot durumu PendingConfiguration durumu bir üst kümesidir.

   Sonuç aşağıdaki tabloda gösterilmiştir durum ilgili bazı tipik senaryoları altındaki özellikler.

   | Senaryo                    | LCMState       | Durum | İstenen yeniden başlatma  | ResourcesInDesiredState  | ResourcesNotInDesiredState |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | S**^**                          | Boşta                 | Başarılı    | $false        | S                            | $null                          |
   | F**^**                          | PendingConfiguration | Başarısız    | $false        | $null                        | F                              |
   | S, F                             | PendingConfiguration | Başarısız    | $false        | S                            | F                              |
   | F, S                             | PendingConfiguration | Başarısız    | $false        | S                            | F                              |
   | S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Başarısız    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
   | F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Başarısız    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
   | S, r                            | PendingReboot        | Başarılı    | $true         | S                            | r                              |
   | F, r                            | PendingReboot        | Başarısız    | $true         | $null                        | F, r                           |
   | r, S                            | PendingReboot        | Başarılı    | $true         | $null                        | r                              |
   | r, F                            | PendingReboot        | Başarılı    | $true         | $null                        | r                              |

   ^
   S<sub>miyim</sub>: F başarıyla uygulandı kaynakları bir dizi<sub>miyim</sub>: bir dizi başarısız yeniden başlatma gerektiren bir r: kaynak uygulanan kaynakları \*

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Get-DscConfigurationStatus cmdlet'inde geliştirme

Birkaç iyileştirme yapılmıştır `Get-DscConfigurationStatus` cmdlet'i bu sürümde. Önceden, StartDate özelliği cmdlet'i tarafından döndürülen nesnelerin dize türünde değil. Şimdi, sadece karmaşık seçme ve daha kolay bir Datetime nesnesini iç özelliklerde göre filtrelemeyi sağlayan Datetime türü değil.

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Tüm DSC işlem kaydı bugün olarak haftanın aynı günde gerçekleşen döndüren bir örneği verilmiştir.

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Geçersiz kayıt işlemlerinin (yani yalnızca işlem okuma) düğümün yapılandırmasını değişiklik yapmayın. Bu nedenle, `Test-DscConfiguration`, `Get-DscConfiguration` operations artık, döndürülen nesneleri adulterated `Get-DscConfigurationStatus` cmdlet'i.
Kayıtları meta yapılandırma ayarı işleminin dönüşü için eklenen `Get-DscConfigurationStatus` cmdlet'i.

Öğesinden döndürülen sonuç örneği aşağıdadır `Get-DscConfigurationStatus` – tüm cmdlet'i.

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Get-DscLocalConfigurationManager cmdlet'i geliştirmesi

Yönteminden döndürülen nesne LCMStateDetail yeni bir alan eklenir `Get-DscLocalConfigurationManager` cmdlet'i. LCMState "Meşgul" olduğunda bu alan doldurulur. Aşağıdaki cmdlet'i tarafından alınabilir:

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Bir sürekli uzak bir düğüm üzerinde iki yeniden başlatma gerektiren bir yapılandırma izleme bir örnek çıktı aşağıda verilmiştir.

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```