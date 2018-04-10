---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a><span data-ttu-id="86892-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="86892-103">Find-DscResource</span></span>

<span data-ttu-id="86892-104">Modüllerdeki DSC kaynakları bulur.</span><span class="sxs-lookup"><span data-stu-id="86892-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="86892-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86892-105">Description</span></span>

<span data-ttu-id="86892-106">Bul DscResource cmdlet bulur [istenen durum Yapılandırması'nı (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) kayıtlı depoları öğesinden belirtilen ölçütlerle eşleşen modüllerde bulunan kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="86892-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="86892-107">Modüllerin her zaman bu cmdlet bulur Bul DscResource yükleme-Bu cmdlet döndürür ve kaynakları içeren modüllerini yüklemek için modülüne iletebildiğiniz bir PSGetDscResourceInfo nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="86892-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="86892-108">DSC, Windows PowerShell'de, dağıtma ve yazılım hizmetleri için yapılandırma verilerini yönetmek ve bu hizmetleri çalıştırdığınız ortamının yönetilmesi sağlayan yeni bir yönetim platformudur.</span><span class="sxs-lookup"><span data-stu-id="86892-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="86892-109">İstenen durum Yapılandırması'nı (DSC) kaynaklar, DSC yapılandırması için yapı taşlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="86892-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="86892-110">Bir kaynak yapılandırılmış (şema) olabilir ve "Bunu yapmak için" yerel Configuration Manager (LCM'yi) çağıran PowerShell Betiği işlevleri içeren özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="86892-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="86892-111">Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucu ayarı olarak belirli bir şey model oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86892-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="86892-112">Grupları, kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve nasıl kullanılmaya kaynaklara yönelik tanımlamak için meta verileri içeren bir yapı düzenler bir DSC modülü, birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="86892-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="86892-113">Bul DscResource sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="86892-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="86892-114">Bu parametreler karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="86892-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="86892-115">Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek modülü adıyla izin verilir.</span><span class="sxs-lookup"><span data-stu-id="86892-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="86892-116">RequiredVersion parametresi belirtilmezse, Bul DscResource en düşük bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya modülünün en son sürümünü modülü en son sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="86892-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="86892-117">RequiredVersion parametresi belirtilirse, Bul DscResource yalnızca tam olarak belirtilen sürümle eşleşen modülü sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="86892-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="86892-118">Bul DscResource modülü meta filtreleyebilir Tag parametresini ile</span><span class="sxs-lookup"><span data-stu-id="86892-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="86892-119">Bul DscResource depo özgü arama dili filtreleyebilir - filtre parametresine sahip.</span><span class="sxs-lookup"><span data-stu-id="86892-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="86892-120">Bul DscResource tüm veya az kayıtlı depoları modüllerden filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86892-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="86892-121">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86892-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="86892-122">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="86892-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="86892-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="86892-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="86892-124">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="86892-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```