---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Lisans Kabulü Gerektiren Modüller
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="8ac7d-103">Lisans Kabulü Gerektiren Modüller</span><span class="sxs-lookup"><span data-stu-id="8ac7d-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="8ac7d-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="8ac7d-104">SYNOPSIS</span></span>

<span data-ttu-id="8ac7d-105">Müşteriler açıkça lisans kendi modülü PowerShell Galerisi'nden yüklemeden önce kabul etmesi gereken bazı modülü yayımcıları için yasal Departmanlar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="8ac7d-106">Bir kullanıcı yükler, güncelleştirmeleri veya PowerShellGet, doğrudan ya da başka bir öğe için bağımlılık olarak kullanarak bir modülü kaydeder ve bu modül kullanıcıya bir lisans kabul gerektiriyorsa, kullanıcı lisansı kabul veya işlem başarısız belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="8ac7d-107">Modülleri için gereksinimleri yayımlama</span><span class="sxs-lookup"><span data-stu-id="8ac7d-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="8ac7d-108">Kullanıcıların lisans kabul etmesini gerektir istediğiniz modülleri gereksinimleri karşılamanız:</span><span class="sxs-lookup"><span data-stu-id="8ac7d-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="8ac7d-109">Modül bildirimi PSData bölümünü RequireLicenseAcceptance içermelidir $True =.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="8ac7d-110">Modül license.txt dosyası kök dizininde içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="8ac7d-111">Modül bildirimi lisans URI içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="8ac7d-112">Modül ve üstü PowerShellGet biçimi sürüm 2.0 ile yayımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="8ac7d-113">Yükleme/kaydetme/güncelleştirme-Module üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="8ac7d-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="8ac7d-114">Yükleme/kaydetme/güncelleştirme cmdlet'leri, yeni bir parametre destekleneceğini – kullanıcının lisans gördüğünüz olarak gibi davranacak AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="8ac7d-115">RequiredLicenseAcceptance True ise ve – AcceptLicense belirtilmezse, kullanıcı license.txt gösterilen ve ile istenir: &quot;lisans koşullarını (Evet/Hayır/YesToAll/NoToAll) kabul ediyor musunuz&quot;.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="8ac7d-116">Lisans kabul edilirse</span><span class="sxs-lookup"><span data-stu-id="8ac7d-116">If the license is accepted</span></span>
    - <span data-ttu-id="8ac7d-117">**Kaydet-Module:** modülü kullanıcıya kopyalanacak&#39;s sistem</span><span class="sxs-lookup"><span data-stu-id="8ac7d-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="8ac7d-118">**Install-Module:** modülü kullanıcıya kopyalanacak&#39;(kapsamına göre) uygun klasöre s sistem</span><span class="sxs-lookup"><span data-stu-id="8ac7d-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="8ac7d-119">**Update-Module:** modülü güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="8ac7d-120">Lisans reddettiyseniz.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-120">If the license is declined.</span></span>
    - <span data-ttu-id="8ac7d-121">İşlem iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="8ac7d-122">Tüm cmdlet'ler lisans kabulünü gereklidir bildiren için meta veriler (requireLicenseAcceptance ve biçim sürümünü) denetler</span><span class="sxs-lookup"><span data-stu-id="8ac7d-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="8ac7d-123">İstemci biçimindeki sürümü 2.0 eskiyse, işlem başarısız ve istemci güncelleştirmesini kullanıcıya isteyin.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="8ac7d-124">Modül biçimi sürüm 2.0 eski yayımlandıysa requireLicenseAcceptance bayrağı yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>


 ## <a name="module-dependencies"></a><span data-ttu-id="8ac7d-125">Modül bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="8ac7d-125">Module Dependencies</span></span>
- <span data-ttu-id="8ac7d-126">(Başka bir modülde bağlıdır) bağımlı bir modül lisans kabulünü sonra lisans kabulü davranış (yukarıda) gerektiriyorsa işlemi kaydetme/yükleme/güncelleştirme sırasında gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="8ac7d-127">Modül sürümü zaten sistemde yüklü olarak yerel kataloğunda listeleniyorsa, biz lisans denetimi atlar.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="8ac7d-128">Yükleme/kaydetme/güncelleştirme işlemi sırasında bir bağımlı modül lisans gerektiriyorsa ve lisans kabulünü oluşmaz, işlemi başarısız olacak ve kaydetme/yükleme/güncelleştirme işlemi başarısız oldu öğesi için normal işlemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="8ac7d-129">Etkisini - Force</span><span class="sxs-lookup"><span data-stu-id="8ac7d-129">Impact on -Force</span></span>

<span data-ttu-id="8ac7d-130">Belirtmek için – Force değil bir lisans kabul etmek yeterli.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="8ac7d-131">– AcceptLicense iznin yüklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="8ac7d-132">Zorla belirtilmişse, – RequiredLicenseAcceptance true'dur ve – AcceptLicense belirtilmedi, işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="8ac7d-133">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="8ac7d-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="8ac7d-134">Örnek 1: Lisans kabulünü gerektirecek şekilde modülü güncelleştirme bildirimi</span><span class="sxs-lookup"><span data-stu-id="8ac7d-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="8ac7d-135">Bu komut, bildirim dosyasını güncelleştirir ve RequireLicenseAcceptance bayrağı true olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="8ac7d-136">Örnek 2: Yükleme modül gerektiren lisans kabulü</span><span class="sxs-lookup"><span data-stu-id="8ac7d-136">Example 2: Install Module requiring license acceptance</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

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

<span data-ttu-id="8ac7d-137">Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="8ac7d-138">Örnek 3: Yükleme modül gerektiren lisans kabulünü - AcceptLicense ile</span><span class="sxs-lookup"><span data-stu-id="8ac7d-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="8ac7d-139">Modül lisans kabul etmek için hiçbir istemi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="8ac7d-140">Örnek 4: Yükleme modül gerektiren lisans kabulünü ile - Force</span><span class="sxs-lookup"><span data-stu-id="8ac7d-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="8ac7d-141">Örnek 5: Yükleme modül lisans kabulünü gerektirme bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="8ac7d-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="8ac7d-142">Modül 'ModuleWithDependency' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="8ac7d-143">Kullanıcı lisansı kabul istenir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-143">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="8ac7d-144">Örnek 6: Yükleme modül lisans kabulünü ve - AcceptLicense gerektiren bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="8ac7d-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="8ac7d-145">Modül 'ModuleWithDependency' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="8ac7d-146">Kullanıcı - AcceptLicense belirtildiği şekilde lisans kabul etmek için istenmez.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="8ac7d-147">7. örnek: PSGetFormatVersion 2.0 eski bir istemcide lisans kabulünü gerektirme modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="8ac7d-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="8ac7d-148">Örnek 8: Lisans kabulünü gerektirme modülü Kaydet</span><span class="sxs-lookup"><span data-stu-id="8ac7d-148">Example 8: Save Module requiring license acceptance</span></span>

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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

<span data-ttu-id="8ac7d-149">Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="8ac7d-150">9. örnek: - AcceptLicense ile lisans kabulünü gerektirme modülü kaydedin</span><span class="sxs-lookup"><span data-stu-id="8ac7d-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="8ac7d-151">Modül lisans kabul etmek için tüm sorulmadan kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="8ac7d-152">Örnek 10: Güncelleştirme modülü gerektiren lisans kabulü</span><span class="sxs-lookup"><span data-stu-id="8ac7d-152">Example 10: Update Module requiring license acceptance</span></span>

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

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

<span data-ttu-id="8ac7d-153">Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="8ac7d-154">Örnek 11: Güncelleştirme modülü gerektiren lisans kabulünü - AcceptLicense ile</span><span class="sxs-lookup"><span data-stu-id="8ac7d-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="8ac7d-155">Modül lisans kabul etmek için tüm sorulmadan güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8ac7d-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="8ac7d-156">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="8ac7d-156">More details</span></span>

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[<span data-ttu-id="8ac7d-157">Betikler için Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="8ac7d-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[<span data-ttu-id="8ac7d-158">Lisans kabulünü desteğini PowerShellGallery gerektirir</span><span class="sxs-lookup"><span data-stu-id="8ac7d-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[<span data-ttu-id="8ac7d-159">Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="8ac7d-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)