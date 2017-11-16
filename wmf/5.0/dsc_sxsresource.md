---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="ce018-102">DSC kaynakları için yan yana modülü sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="ce018-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="ce018-103">Yan yana içeren DSC kaynakları olabileceği modüller yüklü ve DSC yapılandırmaları sistemde yüklü kaynak belirli bir sürümünü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ce018-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="ce018-104">Daha fazla bilgi için bkz: [birden çok sürümü ile kaynakları kullanarak](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="ce018-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="ce018-105">Bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="ce018-105">Known issues</span></span>

<span data-ttu-id="ce018-106">Bu sürümde, yan yana yükleme bilinen sorunlar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ce018-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="ce018-107">DSC kaynağı aynı yapılandırmayı içinde iki farklı sürümlerini kullanan desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ce018-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>

