---
ms.date: 09/09/2019
keywords: PowerShell, cmdlet
title: Ek 1 Uyumluluk Takma Adları
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848171"
---
# <a name="appendix-1---compatibility-aliases"></a>Ek 1-uyumluluk diğer adları

PowerShell, **UNIX** ve **cmd. exe** kullanıcılarının tanıdık komutları kullanmasına izin veren birkaç diğer ad içerir.
Komutlar ve ilgili PowerShell cmdlet 'i ve PowerShell diğer adı aşağıdaki tabloda gösterilmiştir:

|cmd. exe komutu|UNIX komutu|PowerShell cmdlet 'i|PowerShell diğer adı|
|---------------|----------------|--------------|------------|
|**CLS**|**lediğiniz**|`Clear-Host`çalışmayacaktır|`cls`|
|**kopya**|**'s**|`Copy-Item`|`cpi`|
|**öğesini**|**çıkar**|`Get-ChildItem`|`gci`|
|**type**|**kedi**|`Get-Content`|`gc`|
|**geçiş**|**k**|`Move-Item`|`mi`|
|**MD**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**, **Erase**, **RD**, **RMI**|**'yi**|`Remove-Item`|`ri`|
|**Ren**|**k**|`Rename-Item`|`rni`|
|**CD**, **chdir**|**CD**|`Set-Location`|`sl`|

PowerShell diğer adlarını bulmak için [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet 'ini kullanın. Bir cmdlet 'in diğer adlarını göstermek için, **tanım** parametresini kullanın ve cmdlet adını belirtin.
Ya da diğer adın cmdlet adını bulmak için **ad** parametresini kullanın ve diğer adı belirtin.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
