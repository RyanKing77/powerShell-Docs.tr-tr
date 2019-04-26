---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057477"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>PowerShell modülü bulma, yükleme ve envanteri PowerShellGet ile

PowerShellGet WMF bu sürümünde yer almaktadır:
-   Find-Module modülü meta verilerine göre filtreleme yapabilirsiniz etiket parametresi
-   Find-Module depo özgü arama diline filtreleme yapabilirsiniz filtre parametresi
-   Find-Module olabilir modülünü göre filtreleme Command - DscResource, içeriği ve - parametreleri içerir
-   Bul-DscResource depolardaki DSC kaynakların bulunmasını sağlar.
-   Yükleme ve dosya paylaşımlarına NuGet ile yayımlama desteği

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
-   Üç yeni cmdlet
    -   Get-InstalledModule
    -   Modül kaldırma
    -   Save-Module
