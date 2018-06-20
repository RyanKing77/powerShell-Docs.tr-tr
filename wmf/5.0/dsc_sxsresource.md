---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218442"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="f7cb3-102">DSC kaynakları için yan yana modülü sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="f7cb3-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="f7cb3-103">Yan yana içeren DSC kaynakları olabileceği modüller yüklü ve DSC yapılandırmaları sistemde yüklü kaynak belirli bir sürümünü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7cb3-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="f7cb3-104">Daha fazla bilgi için bkz: [birden çok sürümü ile kaynakları kullanarak](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="f7cb3-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="f7cb3-105">Bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f7cb3-105">Known issues</span></span>

<span data-ttu-id="f7cb3-106">Bu sürümde, yan yana yükleme bilinen sorunlar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f7cb3-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="f7cb3-107">DSC kaynağı aynı yapılandırmayı içinde iki farklı sürümlerini kullanan desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="f7cb3-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
