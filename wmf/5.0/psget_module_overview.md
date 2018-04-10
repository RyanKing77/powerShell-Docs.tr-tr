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
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="3860e-102">PowerShell modülü bulma, yükleme ve PowerShellGet ile stok</span><span class="sxs-lookup"><span data-stu-id="3860e-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="3860e-103">PowerShellGet WMF bu sürümde eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="3860e-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="3860e-104">Bulma modülü modülü meta filtreleyebilir Tag parametresini ile</span><span class="sxs-lookup"><span data-stu-id="3860e-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="3860e-105">Bulma modülü deposu özgü arama dili filtreleyebilir filtre parametresi ile</span><span class="sxs-lookup"><span data-stu-id="3860e-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="3860e-106">Bulma modülü için modüle bağlı filtre Command - DscResource, içeriği ve - parametreleri içerir</span><span class="sxs-lookup"><span data-stu-id="3860e-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="3860e-107">Depoları tek tek DSC kaynakları bulma bulma DscResource sağlar</span><span class="sxs-lookup"><span data-stu-id="3860e-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="3860e-108">Yükleme ve dosya paylaşımları NuGet ile yayımlamak için destek</span><span class="sxs-lookup"><span data-stu-id="3860e-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="3860e-109">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="3860e-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="3860e-110">PowerShellGet yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="3860e-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="3860e-111">Windows PowerShell 5.0 veya daha yeni yan yana sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="3860e-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="3860e-112">Modül bağımlılık yükleme desteği</span><span class="sxs-lookup"><span data-stu-id="3860e-112">Module dependency installation support</span></span>
-   <span data-ttu-id="3860e-113">Üç yeni cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="3860e-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="3860e-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="3860e-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="3860e-115">Kaldırma Modülü</span><span class="sxs-lookup"><span data-stu-id="3860e-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="3860e-116">Kaydet-Modülü</span><span class="sxs-lookup"><span data-stu-id="3860e-116">Save-Module</span></span>