---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7b4e4dbeaf9c3c48e7b2dfc74435dfa2cd9c7ea7
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Birleşmiş ve Tutarlı Durum ve Durum Gösterimi

Bir dizi, yerleşik LCM'yi durumu ve DSC durum otomasyonlara yönelik bu sürümde yapılan. Birleştirilmiş ve tutarlı durumunu ve durum Beyanları bunlar, yönetilebilir datetime özelliği durum nesne Get-DscConfigurationStatus cmdlet tarafından döndürülen ve Get-DscLocalConfigurationManager tarafından döndürülen LCM'yi durumu ayrıntıları özelliği Gelişmiş cmdlet'ini kullanın.

LCM'yi durumu ve DSC işlem durumunu gösterimini tekrar ziyaret ve aşağıdaki kurallara göre birleşik:
1.  Notprocessed kaynak LCM'yi durumu ve DSC durumunu etkilemez.
2.  Yeniden başlatma istekleri kaynak bulduğu sonra daha fazla işleme kaynaklarına LCM'yi durdurun.
3.  Yeniden başlatma gerçekte işlem yapılana kadar yeniden başlatma istekleri kaynak istenilen durumda değil.
4.  Başarısız bir bağımlı olmadıkları sürece, başarısız bir kaynağa karşılaşmadan sonra LCM'yi kaynakları işlenmesi tutar.
5.  Get-DscConfigurationStatus cmdlet tarafından döndürülen genel durumu tüm kaynakların durum Süper kümesidir.
6.  PendingReboot durumu PendingConfiguration durumunun bir üst kümesidir.

Aşağıdaki tabloda sonuç gösterilmiştir durum ilgili birkaç tipik senaryolar altında özellikleri.

| Senaryo                    | LCMState       | Durum | İstenen yeniden başlatma  | ResourcesInDesiredState  | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | Boşta                 | Başarılı    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Başarısız    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Başarısız    | $false        | S                            | F                              |
| F, S                             | PendingConfiguration | Başarısız    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Başarısız    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Başarısız    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Başarılı    | $true         | S                            | R                              |
| F, r                            | PendingReboot        | Başarısız    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Başarılı    | $true         | $null                        | R                              |
| r, F                            | PendingReboot        | Başarılı    | $true         | $null                        | R                              |

^ S<sub>ı</sub>: F başarıyla uygulandı kaynakları bir dizi<sub>ı</sub>: bir dizi başarısız yeniden başlatma gerektiren r: A kaynak uygulanan kaynakları \*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Get-DscConfigurationStatus cmdlet'i geliştirme

Get-DscConfigurationStatus cmdlet'i bu sürümde bazı geliştirmeler yapılmıştır. Daha önce StartDate, cmdlet tarafından döndürülen nesnelerin dize türünde özelliğidir. Şimdi, seçerek ve daha kolay bir Datetime nesnesi iç özellikleri göre filtreleme karmaşık etkinleştirir Datetime türünde değil.

```powershell
(Get-DscConfigurationStatus).StartDate | fl *
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

Aşağıdaki tüm DSC işlemi kayıtları bugün olarak haftanın aynı gün içinde gerçekleşen döndüren bir örnektir.

```powershell
(Get-DscConfigurationStatus –All) | where { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Kayıtları (yani yalnızca işlemleri okuma) düğümün yapılandırma değişiklik yapmayın işlemlerinin ortadan kalkar. Bu nedenle, Test-DscConfiguration, Get-DscConfiguration işlemleri artık içinde adulterated Get-DscConfigurationStatus cmdlet'i nesne döndürmedi.
Meta yapılandırmasını ayarlama işlemini kayıtlarının Get-DscConfigurationStatus cmdlet'i geri dönmek için eklenir.

Get-DscConfigurationStatus döndürülen sonuç örneği aşağıdadır – tüm cmdlet'i.

```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Get-DscLocalConfigurationManager cmdlet'i geliştirme

Yeni bir alan LCMStateDetail, Get-DscLocalConfigurationManager cmdlet'i döndürülen nesne eklenir. Bu alan, LCMState "Meşgul" olduğunda doldurulur. Aşağıdaki cmdlet'i tarafından alınabilir:

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Aşağıda, bir sürekli uzak bir düğüm üzerindeki iki yeniden başlatma gerektiren bir yapılandırma izleme bir örnek çıktı verilmiştir.

```powershell
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
