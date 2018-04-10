---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Bul komutu
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a>Bul komutu

PowerShell komutlarını modülleri bulur.

## <a name="description"></a>Açıklama
Cmdlet, diğer adlar, İşlevler ve iş akışları gibi PowerShell komutları Bul-Command cmdlet'i bulur. Bul komutu modülleri kayıtlı depoları içinde arar.
Bu cmdlet bulduğu her komut için bir PSGetCommandInfo nesnesi döndürür. Komutu içeren modülünü yüklemek için Yükle-modül cmdlet PSGetCommandInfo nesnesini geçirebilirsiniz.

- Bul komutu sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, RequiredVersion, AllVersions.
  - Bu parametreler karşılıklı olarak birbirini dışlar.
  - Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek modülü adıyla izin verilir.
  - RequiredVersion parametresi belirtilmezse, Bul komutu en az bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya modülünün en son sürümünü modülü en son sürümünü döndürür.
  - RequiredVersion parametresi belirtilirse, Bul komutu yalnızca tam olarak belirtilen sürümle eşleşen modülü sürümünü döndürür.
- Bul komutu modülü meta filtreleyebilir Tag parametresini ile
- Bul komutu deposu özgü arama dili filtreleyebilir - filtre parametresine sahip.
- Bul komutu tüm veya az kayıtlı depoları modüllerden filtre uygulayabilirsiniz.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Bul komutu](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>Örnek komutlar
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```