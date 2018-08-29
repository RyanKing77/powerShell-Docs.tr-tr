---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Komutlar hakkında bilgi alma
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: f4238927f10b4204cd3e23f0b0453011f54cb04a
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134019"
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

Bu görünümler Cmd.exe Yardım çıktısını gibi çok çıkış: iç komutları tablosal bir özeti. Alıntı içinde `Get-Command` komut gösterilen her komut, yukarıda gösterilen çıkış, bir CommandType cmdlet'i vardır. Bir cmdlet, PowerShell'in iç komut türüdür. Bu tür komutlar gibi kabaca karşılık `dir` ve `cd` bash Kabuk Cmd.exe veya UNIX yerleşik komutlarını ister.

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
> Yıldız işareti (\*) joker karakter eşleme PowerShell komut satırı bağımsız değişkenlerini için kullanılır. \* Eşleşme anlamına gelir"bir veya daha fazla herhangi bir karakter". Yazabilirsiniz `Get-Command a*` harfi ile başlayan tüm komutları bulmak için "a". Joker karakter eşleme cmd.exe içinde, PowerShell'in joker ayrıca bir süre eşleşir.

Kullanım **CommandType** parametresinin `Get-Command` diğer tür yerel komutları almak için.
cmdlet'ini çalıştırdığınızda döndürülen çekirdek kaynakları bilgilerini gözden geçirebilirsiniz.

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