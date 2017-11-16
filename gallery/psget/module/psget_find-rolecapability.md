---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Bul RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a><span data-ttu-id="a3e0b-103">Bul RoleCapability</span><span class="sxs-lookup"><span data-stu-id="a3e0b-103">Find-RoleCapability</span></span>

<span data-ttu-id="a3e0b-104">Rol özellikleri modülleri bulur.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="a3e0b-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3e0b-105">Description</span></span>
<span data-ttu-id="a3e0b-106">Bul RoleCapability cmdlet'i modüllerdeki PowerShell rol özellikleri bulur.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="a3e0b-107">Bul RoleCapability modülleri kayıtlı depoları içinde arar.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-107">Find-RoleCapability searches modules in registered repositories.</span></span> <span data-ttu-id="a3e0b-108">Bu cmdlet bulduğu her rol özelliği için bir PSGetRoleCapabilityInfo nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="a3e0b-109">Rol özelliği içeren modülünü yüklemek için Yükle-modül cmdlet PSGetRoleCapabilityInfo nesnesini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="a3e0b-110">PowerShell rol özellikleri, komutları tanımlamak, uygulamaları ve benzeri, bir kullanıcı yalnızca yetecek kadar Yönetim (JEA) uç noktada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="a3e0b-111">Rol özellikleri .psrc uzantılı dosyaları tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="a3e0b-112">Bul RoleCapability sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="a3e0b-113">Bu parametreler karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="a3e0b-114">Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek modülü adıyla izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="a3e0b-115">RequiredVersion parametresi belirtilmezse, Bul RoleCapability en düşük bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya modülünün en son sürümünü modülü en son sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="a3e0b-116">RequiredVersion parametresi belirtilirse, Bul RoleCapability yalnızca tam olarak belirtilen sürümle eşleşen modülü sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="a3e0b-117">Bul RoleCapability modülü meta filtreleyebilir Tag parametresini ile</span><span class="sxs-lookup"><span data-stu-id="a3e0b-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="a3e0b-118">Bul RoleCapability depo özgü arama dili filtreleyebilir - filtre parametresine sahip.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="a3e0b-119">Bul RoleCapability tüm veya az kayıtlı depoları modüllerden filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3e0b-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a3e0b-120">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3e0b-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a3e0b-121">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="a3e0b-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="a3e0b-122">Bul RoleCapability</span><span class="sxs-lookup"><span data-stu-id="a3e0b-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="a3e0b-123">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="a3e0b-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

