---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Betikler için lisans kabulü gerektiren
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002591"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="ac2ed-103">Betikler için lisans kabulü gerektiren</span><span class="sxs-lookup"><span data-stu-id="ac2ed-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="ac2ed-104">Betikler için lisans kabulü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="ac2ed-105">Bununla birlikte, burada betik lisans kabulü gerektiren bir modülünü bağlıdır senaryo desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="ac2ed-106">Betik commands(Install-Script/Save-Script/Update-Script) destekleyen yeni bir parametre - kullanıcı lisansı saw olarak gibi davranır AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="ac2ed-107">-AcceptLicense belirtilmezse; Kullanıcı license.txt bağımlı modülü için gösterilen ve bu lisansı kabul istenir.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="ac2ed-108">ÖRNEKLERİ</span><span class="sxs-lookup"><span data-stu-id="ac2ed-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="ac2ed-109">Örnek 1: Lisans kabulü gerektiren bağımlılıkları olan yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="ac2ed-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="ac2ed-110">Betik 'ScriptRequireLicenseAcceptance' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ac2ed-111">Kullanıcı lisansı kabul istenir.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="ac2ed-112">Örnek 2: Lisans kabulü ve - AcceptLicense gerektiren bağımlılıkları olan yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="ac2ed-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="ac2ed-113">Betik 'ScriptRequireLicenseAcceptance' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ac2ed-114">-AcceptLicense olarak lisansını kabul etmek için kullanıcıya sorulmaz.</span><span class="sxs-lookup"><span data-stu-id="ac2ed-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="ac2ed-115">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="ac2ed-115">More details</span></span>

- [<span data-ttu-id="ac2ed-116">Modüller için lisans kabulü desteği gerektirir</span><span class="sxs-lookup"><span data-stu-id="ac2ed-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="ac2ed-117">PowerShellGallery desteğini lisans kabulü gerektir</span><span class="sxs-lookup"><span data-stu-id="ac2ed-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="ac2ed-118">Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="ac2ed-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
