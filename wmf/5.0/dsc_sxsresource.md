---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685637"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="c2812-102">DSC kaynakları için yan yana modülü sürüm oluşturma desteği</span><span class="sxs-lookup"><span data-stu-id="c2812-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="c2812-103">DSC kaynakları içeren olabileceği modüller yan yana yüklü ve DSC yapılandırmaları sistemde yüklü kaynak belirli bir sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2812-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="c2812-104">Daha fazla bilgi için [birden çok sürümü olan kaynakları kullanma](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="c2812-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="c2812-105">Bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="c2812-105">Known issues</span></span>

<span data-ttu-id="c2812-106">Bu sürümde aşağıdaki yan yana yükleme sorunlar bilinmektedir:</span><span class="sxs-lookup"><span data-stu-id="c2812-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="c2812-107">DSC kaynak aynı yapılandırması içindeki iki farklı sürümlerini kullanan desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c2812-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
