---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="1b452-103">Komut dosyaları için lisans kabulünü gerektirme</span><span class="sxs-lookup"><span data-stu-id="1b452-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="1b452-104">Lisans kabulünü komut dosyaları için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="1b452-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="1b452-105">Ancak, bir komut dosyası lisans kabulünü gerektiren bir modülünü yere bağlıdır senaryo desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1b452-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="1b452-106">Komut dosyası commands(Install-Script/Save-Script/Update-Script) destekleyen yeni bir parametre - kullanıcı lisansı gördüğünüz olarak gibi davranır AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="1b452-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="1b452-107">-AcceptLicense belirtilmezse; Kullanıcı license.txt bağımlı modülü için gösterilen ve lisans kabul etmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="1b452-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="1b452-108">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="1b452-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="1b452-109">Örnek 1: Lisans kabulünü gerektirme bağımlılıkları olan yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="1b452-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="1b452-110">Komut dosyası 'ScriptRequireLicenseAcceptance' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1b452-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1b452-111">Kullanıcı lisansı kabul istenir.</span><span class="sxs-lookup"><span data-stu-id="1b452-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="1b452-112">Örnek 2: Lisans kabulünü ve - AcceptLicense gerektiren bağımlılıkları olan yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="1b452-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="1b452-113">Komut dosyası 'ScriptRequireLicenseAcceptance' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1b452-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1b452-114">Kullanıcı - AcceptLicense belirtildiği şekilde lisans kabul etmek için istenmez.</span><span class="sxs-lookup"><span data-stu-id="1b452-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="1b452-115">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="1b452-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="1b452-116">Modüller için lisans kabulünü desteği gerektirir</span><span class="sxs-lookup"><span data-stu-id="1b452-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="1b452-117">Lisans kabulünü desteğini PowerShellGallery gerektirir</span><span class="sxs-lookup"><span data-stu-id="1b452-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="1b452-118">Lisans kabulünü gerektiren üzerinde Azure Automation'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="1b452-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
