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
# <a name="find-command"></a><span data-ttu-id="fae12-103">Bul komutu</span><span class="sxs-lookup"><span data-stu-id="fae12-103">Find-Command</span></span>

<span data-ttu-id="fae12-104">PowerShell komutlarını modülleri bulur.</span><span class="sxs-lookup"><span data-stu-id="fae12-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="fae12-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fae12-105">Description</span></span>
<span data-ttu-id="fae12-106">Cmdlet, diğer adlar, İşlevler ve iş akışları gibi PowerShell komutları Bul-Command cmdlet'i bulur.</span><span class="sxs-lookup"><span data-stu-id="fae12-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="fae12-107">Bul komutu modülleri kayıtlı depoları içinde arar.</span><span class="sxs-lookup"><span data-stu-id="fae12-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="fae12-108">Bu cmdlet bulduğu her komut için bir PSGetCommandInfo nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fae12-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="fae12-109">Komutu içeren modülünü yüklemek için Yükle-modül cmdlet PSGetCommandInfo nesnesini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae12-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="fae12-110">Bul komutu sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="fae12-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="fae12-111">Bu parametreler karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="fae12-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="fae12-112">Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek modülü adıyla izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fae12-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="fae12-113">RequiredVersion parametresi belirtilmezse, Bul komutu en az bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya modülünün en son sürümünü modülü en son sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="fae12-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="fae12-114">RequiredVersion parametresi belirtilirse, Bul komutu yalnızca tam olarak belirtilen sürümle eşleşen modülü sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="fae12-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="fae12-115">Bul komutu modülü meta filtreleyebilir Tag parametresini ile</span><span class="sxs-lookup"><span data-stu-id="fae12-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="fae12-116">Bul komutu deposu özgü arama dili filtreleyebilir - filtre parametresine sahip.</span><span class="sxs-lookup"><span data-stu-id="fae12-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="fae12-117">Bul komutu tüm veya az kayıtlı depoları modüllerden filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae12-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="fae12-118">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fae12-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="fae12-119">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="fae12-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="fae12-120">Bul komutu</span><span class="sxs-lookup"><span data-stu-id="fae12-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="fae12-121">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="fae12-121">Example commands</span></span>
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