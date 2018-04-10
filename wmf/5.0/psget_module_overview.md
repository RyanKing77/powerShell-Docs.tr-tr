---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 82b8046d5cbb47300f090ce2ffbf3c279ed19458
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>PowerShell modülü bulma, yükleme ve PowerShellGet ile stok

PowerShellGet WMF bu sürümde eklenmiştir:
-   Bulma modülü modülü meta filtreleyebilir Tag parametresini ile
-   Bulma modülü deposu özgü arama dili filtreleyebilir filtre parametresi ile
-   Bulma modülü için modüle bağlı filtre Command - DscResource, içeriği ve - parametreleri içerir
-   Depoları tek tek DSC kaynakları bulma bulma DscResource sağlar
-   Yükleme ve dosya paylaşımları NuGet ile yayımlamak için destek

## <a name="example-commands"></a>Örnek komutlar
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>PowerShellGet yeni özellikler
-   Windows PowerShell 5.0 veya daha yeni yan yana sürüm desteği
-   Modül bağımlılık yükleme desteği
-   Üç yeni cmdlet'leri
    -   Get-InstalledModule
    -   Kaldırma Modülü
    -   Kaydet-Modülü