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
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="73c65-102">PowerShell modülü bulma, yükleme ve envanteri PowerShellGet ile</span><span class="sxs-lookup"><span data-stu-id="73c65-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="73c65-103">PowerShellGet WMF bu sürümünde yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="73c65-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="73c65-104">Find-Module modülü meta verilerine göre filtreleme yapabilirsiniz etiket parametresi</span><span class="sxs-lookup"><span data-stu-id="73c65-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="73c65-105">Find-Module depo özgü arama diline filtreleme yapabilirsiniz filtre parametresi</span><span class="sxs-lookup"><span data-stu-id="73c65-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="73c65-106">Find-Module olabilir modülünü göre filtreleme Command - DscResource, içeriği ve - parametreleri içerir</span><span class="sxs-lookup"><span data-stu-id="73c65-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="73c65-107">Bul-DscResource depolardaki DSC kaynakların bulunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="73c65-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="73c65-108">Yükleme ve dosya paylaşımlarına NuGet ile yayımlama desteği</span><span class="sxs-lookup"><span data-stu-id="73c65-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="73c65-109">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="73c65-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="73c65-110">PowerShellGet yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="73c65-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="73c65-111">Windows PowerShell 5.0 veya daha yeni yan yana sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="73c65-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="73c65-112">Modül bağımlılık yükleme desteği</span><span class="sxs-lookup"><span data-stu-id="73c65-112">Module dependency installation support</span></span>
-   <span data-ttu-id="73c65-113">Üç yeni cmdlet</span><span class="sxs-lookup"><span data-stu-id="73c65-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="73c65-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="73c65-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="73c65-115">Modül kaldırma</span><span class="sxs-lookup"><span data-stu-id="73c65-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="73c65-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="73c65-116">Save-Module</span></span>
