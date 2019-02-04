---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684657"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="5272a-102">Import-DscResource anahtar sözcüğü - ModuleVersion parametresini destekler</span><span class="sxs-lookup"><span data-stu-id="5272a-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="5272a-103">Yeni bir parametre ekledik `Import-DscResource` dynamic anahtar sözcüğü DSC yapılandırmaları yazarken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5272a-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="5272a-104">Yapılandırma yazarları artık DSC kaynaklarından yüklemek için tam olarak hangi modül sürümünün belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5272a-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="5272a-105">Anahtar sözcüğünün yeni sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5272a-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="5272a-106">**Ad**: İçeri aktarmak için bir veya daha fazla kaynak adları.</span><span class="sxs-lookup"><span data-stu-id="5272a-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="5272a-107">**ModuleName**: Modül adlarını veya içeri aktarmak için bir veya daha fazla modül ModuleSpecification nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5272a-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="5272a-108">**Moduleversıon**: Modülü içeri aktarmak için sürümü.</span><span class="sxs-lookup"><span data-stu-id="5272a-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="5272a-109">ModuleName kullandıysanız, yalnızca bir modül adına göre temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="5272a-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="5272a-110">Windows PowerShell ISE'de, IntelliSense ile gösterilir:</span><span class="sxs-lookup"><span data-stu-id="5272a-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="5272a-111">**Not**: `–ModuleVersion` parametresi yalnızca kullanılabilir birlikte `–ModuleName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5272a-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="5272a-112">Yalnızca kaynak adları ile kullanılamaz `–Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5272a-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="5272a-113">Örneğin modülü belirtimi nesnesini kullanarak daha önce DSC kaynakları yüklenirken Modül sürümü belirtmek için tek yolu şöyleydi: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="5272a-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
