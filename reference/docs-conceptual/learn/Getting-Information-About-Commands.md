---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Komutlar hakkında bilgi alma
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030949"
---
# <a name="getting-information-about-commands"></a>Komutlar hakkında bilgi alma

PowerShell `Get-Command` Geçerli oturumunuzda kullanılabilir komutları görüntüler.
Çalıştırdığınızda `Get-Command` cmdlet'ini aşağıdaki çıktıya benzer bir şey görürsünüz:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Bu görünümler gibi Yardım çıktısını çok çıktı **cmd.exe**: iç komutları tablosal bir özeti. Alıntı içinde `Get-Command` komut gösterilen her komut, yukarıda gösterilen çıkış, bir CommandType cmdlet'i vardır. Bir cmdlet, PowerShell'in iç komut türüdür. Bu tür komutlar gibi kabaca karşılık `dir` ve `cd` içinde **cmd.exe** veya bash gibi UNIX Kabukları'nın yerleşik komutlar.

`Get-Command` Cmdlet'i sahip bir **söz dizimi** her cmdlet'in söz dizimi döndüren parametresi. Aşağıdaki örnek söz dizimini alınacağı gösterilmektedir `Get-Help` cmdlet:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Kullanılabilir komut türüne göre görüntüleme

`Get-Command` Komut geçerli oturumda yalnızca cmdlet öğelerini listeler. PowerShell komutları diğer birçok türde gerçekten destekler:

- Diğer adlar
- İşlevler
- Betikler

Ayrıca Dış yürütülebilir dosyalar veya kayıtlı dosya türü işleyicisi dosyalar komut olarak sınıflandırılır.

Tüm komutlar oturumda almak için şunu yazın:

```powershell
Get-Command *
```

Bu liste, binlerce öğenin bulunabilir, arama yolunda dış komutları içerir.
Sınırlı bir komut kümesini aramak daha yararlı olacaktır.

> [!NOTE]
> Yıldız işareti (\*) joker karakter eşleme PowerShell komut satırı bağımsız değişkenlerini için kullanılır. \* Eşleşme anlamına gelir"bir veya daha fazla herhangi bir karakter". Yazabilirsiniz `Get-Command a*` harfi ile başlayan tüm komutları bulmak için "a". İçinde joker karakterlerle eşleşen aksine **cmd.exe**, PowerShell'in joker karakter, bir süre de eşleşir.

Kullanım **CommandType** parametresinin `Get-Command` diğer tür yerel komutları almak için.
cmdlet'i.

Komutların atanan takma adları olan komut diğer adları almak için aşağıdakileri yazın:

```powershell
Get-Command -CommandType Alias
```

Geçerli oturumda işlevleri almak için şunu yazın:

```powershell
Get-Command -CommandType Function
```

PowerShell'in arama yolunda komut dosyaları görüntülemek için şunu yazın:

```powershell
Get-Command -CommandType Script
```
