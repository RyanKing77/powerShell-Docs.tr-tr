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
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="28613-102">PowerShell modülü bulma, yükleme ve PowerShellGet ile stok</span><span class="sxs-lookup"><span data-stu-id="28613-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>
 
<span data-ttu-id="28613-103">PowerShellGet WMF bu sürümde eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="28613-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="28613-104">Bulma modülü modülü meta filtreleyebilir Tag parametresini ile</span><span class="sxs-lookup"><span data-stu-id="28613-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="28613-105">Bulma modülü deposu özgü arama dili filtreleyebilir filtre parametresi ile</span><span class="sxs-lookup"><span data-stu-id="28613-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="28613-106">Bulma modülü için modüle bağlı filtre Command - DscResource, içeriği ve - parametreleri içerir</span><span class="sxs-lookup"><span data-stu-id="28613-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="28613-107">Depoları tek tek DSC kaynakları bulma bulma DscResource sağlar</span><span class="sxs-lookup"><span data-stu-id="28613-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="28613-108">Yükleme ve dosya paylaşımları NuGet ile yayımlamak için destek</span><span class="sxs-lookup"><span data-stu-id="28613-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="28613-109">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="28613-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="28613-110">PowerShellGet yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="28613-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="28613-111">Windows PowerShell 5.0 veya daha yeni yan yana sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="28613-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="28613-112">Modül bağımlılık yükleme desteği</span><span class="sxs-lookup"><span data-stu-id="28613-112">Module dependency installation support</span></span>
-   <span data-ttu-id="28613-113">Üç yeni cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="28613-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="28613-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="28613-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="28613-115">Kaldırma Modülü</span><span class="sxs-lookup"><span data-stu-id="28613-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="28613-116">Kaydet-Modülü</span><span class="sxs-lookup"><span data-stu-id="28613-116">Save-Module</span></span>
    
