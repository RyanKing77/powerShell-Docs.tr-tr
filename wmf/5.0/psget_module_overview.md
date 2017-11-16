---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
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
    
