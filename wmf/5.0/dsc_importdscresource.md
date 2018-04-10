---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a3b176101bebf7081febd8629bddcfa0ae1e7540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="be65e-102">İçeri aktarma DscResource anahtar sözcüğü - ModuleVersion parametresini destekler</span><span class="sxs-lookup"><span data-stu-id="be65e-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="be65e-103">Yeni bir parametre ekledik `Import-DscResource` dynamic anahtar DSC yapılandırmaları yazarken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be65e-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="be65e-104">Yapılandırma yazarlar DSC kaynaklarından yüklemek için tam olarak hangi Modül sürümü artık belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be65e-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="be65e-105">Yeni anahtar sözcük sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="be65e-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="be65e-106">**Ad**: içeri aktarmak için bir veya daha fazla kaynakların adları.</span><span class="sxs-lookup"><span data-stu-id="be65e-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="be65e-107">**ModuleName**: modül adlarını veya ModuleSpecification nesneleri içeri aktarmak için bir veya daha fazla modülü.</span><span class="sxs-lookup"><span data-stu-id="be65e-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="be65e-108">**ModuleVersion**: modül ot içe sürümü.</span><span class="sxs-lookup"><span data-stu-id="be65e-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="be65e-109">Kullandıysanız, ModuleName adıyla yalnızca bir modülü temsil etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="be65e-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="be65e-110">Windows PowerShell ISE IntelliSense ile görüntülersiniz:</span><span class="sxs-lookup"><span data-stu-id="be65e-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="be65e-111">**Not**: `–ModuleVersion` parametresi yalnızca kullanılabilir birlikte `–ModuleName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="be65e-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="be65e-112">Yalnızca kaynak adlarıyla kullanılamaz `–Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="be65e-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="be65e-113">Önce DSC kaynakları yüklenirken Modül sürümü belirtmek için tek yolu örneğin modül belirtimi nesnesini kullanarak, bu: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="be65e-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>