---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Lisans Kabulü Gerektiren Modüller
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075231"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="de49f-103">Lisans Kabulü Gerektiren Modüller</span><span class="sxs-lookup"><span data-stu-id="de49f-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="de49f-104">ÖZETİ</span><span class="sxs-lookup"><span data-stu-id="de49f-104">SYNOPSIS</span></span>

<span data-ttu-id="de49f-105">Müşteriler açıkça lisans kendi modülü PowerShell Galerisi'nden yüklemeden önce kabul etmesi gereken bazı modülü yayımcılar için yasal Departmanlar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="de49f-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="de49f-106">Bir kullanıcı yükler, güncelleştirmeleri veya PowerShellGet, doğrudan ya da başka bir paket için bir bağımlılık olarak kullanarak bir modülü kaydeder ve bu modül lisansı kabul etmesi gerekir, kullanıcı lisansı kabul veya işlem başarısız belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de49f-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="de49f-107">Modüller için gereksinimleri yayımlama</span><span class="sxs-lookup"><span data-stu-id="de49f-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="de49f-108">Kullanıcıların lisans kabul etmesini gerektirmek için istediğiniz modülleri gereksinimleri yerine getirmek:</span><span class="sxs-lookup"><span data-stu-id="de49f-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="de49f-109">Modül bildirimini PSData bölümünü RequireLicenseAcceptance içermelidir $True =.</span><span class="sxs-lookup"><span data-stu-id="de49f-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="de49f-110">Modül kök dizininde license.txt dosyasına içermelidir.</span><span class="sxs-lookup"><span data-stu-id="de49f-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="de49f-111">Modül bildirimini lisans URI içermelidir.</span><span class="sxs-lookup"><span data-stu-id="de49f-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="de49f-112">PowerShellGet biçimi sürüm 2.0 ve üstüyle modülü yayımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="de49f-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="de49f-113">Yükleme/kaydetme/Update-Module etkisi</span><span class="sxs-lookup"><span data-stu-id="de49f-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="de49f-114">Yükleme/kaydetme/güncelleştirme cmdlet'leri yeni bir parametre destekleyeceği – kullanıcı lisansı saw olarak gibi davranır AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="de49f-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="de49f-115">RequiredLicenseAcceptance true'dur ve – AcceptLicense belirtilmezse, kullanıcı license.txt gösterilen ve ile istenir: &quot;Bu lisans koşullarını (Evet/Hayır/YesToAll/NoToAll) kabul etmezseniz&quot;.</span><span class="sxs-lookup"><span data-stu-id="de49f-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="de49f-116">Lisans kabul edilirse</span><span class="sxs-lookup"><span data-stu-id="de49f-116">If the license is accepted</span></span>
    - <span data-ttu-id="de49f-117">**Save-Module:** modülü kullanıcıya kopyalanacak&#39;s sistem</span><span class="sxs-lookup"><span data-stu-id="de49f-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="de49f-118">**Install-Module:** modülü kullanıcıya kopyalanacak&#39;s sistem uygun klasöre (kapsamınıza bağlı olarak)</span><span class="sxs-lookup"><span data-stu-id="de49f-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="de49f-119">**Update-Module:** modülü güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="de49f-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="de49f-120">Lisansı'nı reddetmeniz durumunda.</span><span class="sxs-lookup"><span data-stu-id="de49f-120">If the license is declined.</span></span>
    - <span data-ttu-id="de49f-121">İşlem iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="de49f-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="de49f-122">Tüm cmdlet'ler lisans kabulü gerekli olduğuna ilişkin meta verileri (requireLicenseAcceptance ve biçim sürümünü) denetler.</span><span class="sxs-lookup"><span data-stu-id="de49f-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="de49f-123">İstemci biçimindeki sürümü 2.0 eskiyse, işlem başarısız ve istemci güncelleştirmesi için kullanıcıya sor.</span><span class="sxs-lookup"><span data-stu-id="de49f-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="de49f-124">Modül biçimi sürüm 2.0 eski yayımlandıysa requireLicenseAcceptance bayrağı yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="de49f-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="de49f-125">Modül bağımlılıklarının</span><span class="sxs-lookup"><span data-stu-id="de49f-125">Module Dependencies</span></span>

- <span data-ttu-id="de49f-126">Yükleme/kaydetme/güncelleştirme sırasında işlemi (başka bir modüldeki bağlıdır) bağımlı bir modül lisans kabulü sonra lisans kabulü davranışı (yukarıda) gerektiriyorsa, gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="de49f-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="de49f-127">Modül sürümü sistemde yüklü olarak yerel kataloğunda zaten listedeyse, biz lisansı denetleniyor atlar.</span><span class="sxs-lookup"><span data-stu-id="de49f-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="de49f-128">Yükleme/kaydetme/güncelleştirme işlemi sırasında lisansı bağımlı bir modül gerektirir ve lisans kabulü oluşmaz, işlemi başarısız ve kaydetme/yükleme/güncelleştirme işlemi başarısız oldu paketi için normal işlemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="de49f-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="de49f-129">-Force üzerindeki etki</span><span class="sxs-lookup"><span data-stu-id="de49f-129">Impact on -Force</span></span>

<span data-ttu-id="de49f-130">Belirtme `–Force` değil bir lisansı kabul etmek yeterli.</span><span class="sxs-lookup"><span data-stu-id="de49f-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="de49f-131">`–AcceptLicense` yüklemek için izin gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="de49f-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="de49f-132">Varsa `–Force` , RequiredLicenseAcceptance True, yeterli belirtilir ve `–AcceptLicense` belirtilmezse, işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="de49f-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="de49f-133">ÖRNEKLERİ</span><span class="sxs-lookup"><span data-stu-id="de49f-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="de49f-134">Örnek 1: Güncelleştirme modül lisans kabulü gerektir için bildirim.</span><span class="sxs-lookup"><span data-stu-id="de49f-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="de49f-135">Bu komut, bildirim dosyasını güncelleştirir ve RequireLicenseAcceptance bayrağı true olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="de49f-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="de49f-136">Örnek 2: Lisans kabulü gerektiren bir modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="de49f-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="de49f-137">Bu komut, lisans license.txt dosyasından gösterir ve bu lisansı kabul etmesi ister.</span><span class="sxs-lookup"><span data-stu-id="de49f-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="de49f-138">Örnek 3: -AcceptLicense ile lisans kabulü gerektiren bir modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="de49f-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="de49f-139">Modül lisansını kabul etmek için herhangi bir istem olmadan yüklenir.</span><span class="sxs-lookup"><span data-stu-id="de49f-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="de49f-140">Örnek 4: -Force ile lisans kabulü gerektiren bir modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="de49f-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="de49f-141">Örnek 5: Lisans kabulü gerektiren bağımlılıklarla modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="de49f-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="de49f-142">Modül 'ModuleWithDependency' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="de49f-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="de49f-143">Kullanıcı lisansı kabul istenir.</span><span class="sxs-lookup"><span data-stu-id="de49f-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="de49f-144">Örnek 6: Lisans kabulü ve - AcceptLicense gerektiren bağımlılıklarla modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="de49f-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="de49f-145">Modül 'ModuleWithDependency' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="de49f-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="de49f-146">-AcceptLicense olarak lisansını kabul etmek için kullanıcıya sorulmaz.</span><span class="sxs-lookup"><span data-stu-id="de49f-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="de49f-147">Örnek 7: PSGetFormatVersion 2.0 eski bir istemcide lisans kabulü gerektiren bir modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="de49f-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="de49f-148">8. örnek: Modül lisans kabulü gerektiren Kaydet</span><span class="sxs-lookup"><span data-stu-id="de49f-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="de49f-149">Bu komut, lisans license.txt dosyasından gösterir ve bu lisansı kabul etmesi ister.</span><span class="sxs-lookup"><span data-stu-id="de49f-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="de49f-150">9. örnek: -AcceptLicense ile lisans kabulü gerektiren modülü Kaydet</span><span class="sxs-lookup"><span data-stu-id="de49f-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="de49f-151">Modül lisansını kabul etmek için herhangi bir istem olmadan kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="de49f-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="de49f-152">10. örnek: Lisans kabulü gerektiren modülü güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="de49f-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="de49f-153">Bu komut, lisans license.txt dosyasından gösterir ve bu lisansı kabul etmesi ister.</span><span class="sxs-lookup"><span data-stu-id="de49f-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="de49f-154">11. örnek: -AcceptLicense ile lisans kabulü gerektiren modülü güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="de49f-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="de49f-155">Modül lisansını kabul etmek için herhangi bir istem olmadan güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="de49f-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="de49f-156">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="de49f-156">More details</span></span>

[<span data-ttu-id="de49f-157">Betikler için Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="de49f-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="de49f-158">PowerShellGallery desteğini lisans kabulü gerektir</span><span class="sxs-lookup"><span data-stu-id="de49f-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="de49f-159">Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="de49f-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
