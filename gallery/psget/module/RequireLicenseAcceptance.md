---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptance
ms.openlocfilehash: d78f8cb7f84869880e9a88a0f0407d18dc5c64cb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="30616-103">Lisans Kabulü Gerektiren Modüller</span><span class="sxs-lookup"><span data-stu-id="30616-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="30616-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="30616-104">SYNOPSIS</span></span>
<span data-ttu-id="30616-105">Müşteriler açıkça lisans kendi modülü PowerShell Galerisi'nden yüklemeden önce kabul etmesi gereken bazı modülü yayımcıları için yasal Departmanlar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="30616-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="30616-106">Bir kullanıcı yükler, güncelleştirmeleri veya PowerShellGet, doğrudan ya da başka bir öğe için bağımlılık olarak kullanarak bir modülü kaydeder ve bu modül kullanıcıya bir lisans kabul gerektiriyorsa, kullanıcı lisansı kabul veya işlem başarısız belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30616-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="30616-107">Modülleri için gereksinimleri yayımlama</span><span class="sxs-lookup"><span data-stu-id="30616-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="30616-108">Kullanıcıların lisans kabul etmesini gerektir istediğiniz modülleri gereksinimleri karşılamanız:</span><span class="sxs-lookup"><span data-stu-id="30616-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="30616-109">Modül bildirimi PSData bölümünü RequireLicenseAcceptance içermelidir $True =.</span><span class="sxs-lookup"><span data-stu-id="30616-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="30616-110">Modül license.txt dosyası kök dizininde içermelidir.</span><span class="sxs-lookup"><span data-stu-id="30616-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="30616-111">Modül bildirimi lisans URI içermelidir.</span><span class="sxs-lookup"><span data-stu-id="30616-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="30616-112">Modül ve üstü PowerShellGet biçimi sürüm 2.0 ile yayımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="30616-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="30616-113">Yükleme/kaydetme/güncelleştirme-Module üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="30616-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="30616-114">Yükleme/kaydetme/güncelleştirme cmdlet'leri, yeni bir parametre destekleneceğini – kullanıcının lisans gördüğünüz olarak gibi davranacak AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="30616-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="30616-115">RequiredLicenseAcceptance True ise ve – AcceptLicense belirtilmezse, kullanıcı license.txt gösterilen ve ile istenir: &quot;lisans koşullarını (Evet/Hayır/YesToAll/NoToAll) kabul ediyor musunuz&quot;.</span><span class="sxs-lookup"><span data-stu-id="30616-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="30616-116">Lisans kabul edilirse</span><span class="sxs-lookup"><span data-stu-id="30616-116">If the license is accepted</span></span>
    - <span data-ttu-id="30616-117">**Kaydet-Module:** modülü kullanıcıya kopyalanacak&#39;s sistem</span><span class="sxs-lookup"><span data-stu-id="30616-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="30616-118">**Install-Module:** modülü kullanıcıya kopyalanacak&#39;(kapsamına göre) uygun klasöre s sistem</span><span class="sxs-lookup"><span data-stu-id="30616-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="30616-119">**Update-Module:** modülü güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="30616-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="30616-120">Lisans reddettiyseniz.</span><span class="sxs-lookup"><span data-stu-id="30616-120">If the license is declined.</span></span>
    - <span data-ttu-id="30616-121">İşlem iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="30616-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="30616-122">Tüm cmdlet'ler lisans kabulünü gereklidir bildiren için meta veriler (requireLicenseAcceptance ve biçim sürümünü) denetler</span><span class="sxs-lookup"><span data-stu-id="30616-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="30616-123">İstemci biçimindeki sürümü 2.0 eskiyse, işlem başarısız ve istemci güncelleştirmesini kullanıcıya isteyin.</span><span class="sxs-lookup"><span data-stu-id="30616-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="30616-124">Modül biçimi sürüm 2.0 eski yayımlandıysa requireLicenseAcceptance bayrağı yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="30616-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>


 ## <a name="module-dependencies"></a><span data-ttu-id="30616-125">Modül bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="30616-125">Module Dependencies</span></span>
- <span data-ttu-id="30616-126">(Başka bir modülde bağlıdır) bağımlı bir modül lisans kabulünü sonra lisans kabulü davranış (yukarıda) gerektiriyorsa işlemi kaydetme/yükleme/güncelleştirme sırasında gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="30616-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="30616-127">Modül sürümü zaten sistemde yüklü olarak yerel kataloğunda listeleniyorsa, biz lisans denetimi atlar.</span><span class="sxs-lookup"><span data-stu-id="30616-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="30616-128">Yükleme/kaydetme/güncelleştirme işlemi sırasında bir bağımlı modül lisans gerektiriyorsa ve lisans kabulünü oluşmaz, işlemi başarısız olacak ve kaydetme/yükleme/güncelleştirme işlemi başarısız oldu öğesi için normal işlemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="30616-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="30616-129">Etkisini - Force</span><span class="sxs-lookup"><span data-stu-id="30616-129">Impact on -Force</span></span>

<span data-ttu-id="30616-130">Belirtmek için – Force değil bir lisans kabul etmek yeterli.</span><span class="sxs-lookup"><span data-stu-id="30616-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="30616-131">– AcceptLicense iznin yüklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30616-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="30616-132">Zorla belirtilmişse, – RequiredLicenseAcceptance true'dur ve – AcceptLicense belirtilmedi, işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="30616-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="30616-133">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="30616-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="30616-134">Örnek 1: Lisans kabulünü gerektirecek şekilde modülü güncelleştirme bildirimi</span><span class="sxs-lookup"><span data-stu-id="30616-134">Example 1: Update Module Manifest to require license acceptance</span></span>
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```
<span data-ttu-id="30616-135">Bu komut, bildirim dosyasını güncelleştirir ve RequireLicenseAcceptance bayrağı true olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="30616-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>
### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="30616-136">Örnek 2: Yükleme modül gerektiren lisans kabulü</span><span class="sxs-lookup"><span data-stu-id="30616-136">Example 2: Install Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

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
<span data-ttu-id="30616-137">Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="30616-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="30616-138">Örnek 3: Yükleme modül gerektiren lisans kabulünü - AcceptLicense ile</span><span class="sxs-lookup"><span data-stu-id="30616-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="30616-139">Modül lisans kabul etmek için hiçbir istemi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="30616-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="30616-140">Örnek 4: Yükleme modül gerektiren lisans kabulünü ile - Force</span><span class="sxs-lookup"><span data-stu-id="30616-140">Example 4: Install Module requiring license acceptance with -Force</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="30616-141">Örnek 5: Yükleme modül lisans kabulünü gerektirme bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="30616-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>
<span data-ttu-id="30616-142">Modül 'ModuleWithDependency' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="30616-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="30616-143">Kullanıcı lisansı kabul istenir.</span><span class="sxs-lookup"><span data-stu-id="30616-143">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="30616-144">Örnek 6: Yükleme modül lisans kabulünü ve - AcceptLicense gerektiren bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="30616-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="30616-145">Modül 'ModuleWithDependency' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="30616-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="30616-146">Kullanıcı - AcceptLicense belirtildiği şekilde lisans kabul etmek için istenmez.</span><span class="sxs-lookup"><span data-stu-id="30616-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="30616-147">7. örnek: PSGetFormatVersion 2.0 eski bir istemcide lisans kabulünü gerektirme modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="30616-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="30616-148">Örnek 8: Lisans kabulünü gerektirme modülü Kaydet</span><span class="sxs-lookup"><span data-stu-id="30616-148">Example 8: Save Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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
<span data-ttu-id="30616-149">Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="30616-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="30616-150">9. örnek: - AcceptLicense ile lisans kabulünü gerektirme modülü kaydedin</span><span class="sxs-lookup"><span data-stu-id="30616-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
<span data-ttu-id="30616-151">Modül lisans kabul etmek için tüm sorulmadan kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="30616-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="30616-152">Örnek 10: Güncelleştirme modülü gerektiren lisans kabulü</span><span class="sxs-lookup"><span data-stu-id="30616-152">Example 10: Update Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

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
<span data-ttu-id="30616-153">Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="30616-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="30616-154">Örnek 11: Güncelleştirme modülü gerektiren lisans kabulünü - AcceptLicense ile</span><span class="sxs-lookup"><span data-stu-id="30616-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="30616-155">Modül lisans kabul etmek için tüm sorulmadan güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="30616-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="30616-156">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="30616-156">More details</span></span>
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[<span data-ttu-id="30616-157">Betikler için Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="30616-157">Require License Acceptance for Scripts</span></span>](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="30616-158">Lisans kabulünü desteğini PowerShellGallery gerektirir</span><span class="sxs-lookup"><span data-stu-id="30616-158">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="30616-159">Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="30616-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)