---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685756"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="dbab5-102">Sınıf tabanlı DSC Kaynakları</span><span class="sxs-lookup"><span data-stu-id="dbab5-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="dbab5-103">DSC kaynakları ile sınıfları tanımlama</span><span class="sxs-lookup"><span data-stu-id="dbab5-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="dbab5-104">Geri bildirimi doğrultusunda, DSC kaynaklarını daha basit ve daha kolay anlaşılır sınıf tabanlı geliştirme yaptık.</span><span class="sxs-lookup"><span data-stu-id="dbab5-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="dbab5-105">Cmdlet'i DSC kaynak sağlayıcısı ile bir sınıf tabanlı DSC kaynağı arasındaki temel farklılıklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dbab5-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="dbab5-106">Şema için bir MOF dosyası gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="dbab5-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="dbab5-107">A **DSCResource** modülü klasöründeki alt gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="dbab5-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="dbab5-108">Bir PowerShell modülü dosyası birden çok DSC kaynak sınıfları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="dbab5-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="dbab5-109">Daha fazla bilgi için [PowerShell sınıfları ile özel bir DSC kaynağı yazma](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="dbab5-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
