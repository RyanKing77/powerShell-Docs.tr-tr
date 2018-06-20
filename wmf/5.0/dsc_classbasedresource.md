---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221859"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="a00a3-102">Sınıf tabanlı DSC Kaynakları</span><span class="sxs-lookup"><span data-stu-id="a00a3-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="a00a3-103">DSC kaynakları ile sınıfları tanımlama</span><span class="sxs-lookup"><span data-stu-id="a00a3-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="a00a3-104">Geri bildirimi doğrultusunda, sınıf tabanlı DSC kaynakları daha basit ve anlaşılması daha kolay geliştirme yaptık.</span><span class="sxs-lookup"><span data-stu-id="a00a3-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="a00a3-105">Bir sınıf tabanlı DSC kaynağı bir cmdlet DSC kaynak sağlayıcısı arasındaki temel farklılıklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a00a3-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="a00a3-106">MOF dosyası şeması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a00a3-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="a00a3-107">A **DSCResource** modül klasöründe alt gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a00a3-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="a00a3-108">PowerShell modülü dosyası birden çok DSC kaynağı sınıfları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a00a3-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="a00a3-109">Daha fazla bilgi için bkz: [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="a00a3-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
