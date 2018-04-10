---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="85873-102">DSC kaynakları için yan yana modülü sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="85873-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="85873-103">Yan yana içeren DSC kaynakları olabileceği modüller yüklü ve DSC yapılandırmaları sistemde yüklü kaynak belirli bir sürümünü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="85873-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="85873-104">Daha fazla bilgi için bkz: [birden çok sürümü ile kaynakları kullanarak](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="85873-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="85873-105">Bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="85873-105">Known issues</span></span>

<span data-ttu-id="85873-106">Bu sürümde, yan yana yükleme bilinen sorunlar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="85873-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="85873-107">DSC kaynağı aynı yapılandırmayı içinde iki farklı sürümlerini kullanan desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="85873-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>