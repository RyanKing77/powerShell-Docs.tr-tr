---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Paket listeden kaldırma
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004175"
---
# <a name="unlisting-packages"></a><span data-ttu-id="1c2da-103">Unlisting paketleri</span><span class="sxs-lookup"><span data-stu-id="1c2da-103">Unlisting Packages</span></span>

<span data-ttu-id="1c2da-104">**Bir seçenek olarak gösterilmeyen PowerShell Galerisi'nden bir paketi kaldırma neden?**</span><span class="sxs-lookup"><span data-stu-id="1c2da-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="1c2da-105">PowerShell Galerisi paketlerini kalıcı olarak silme kullanıcılar desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1c2da-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="1c2da-106">Bu, gelecekteki olası sonları hakkında endişelenmeden paketlerinizi üzerinde bağımlılıkları almak diğer sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c2da-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="1c2da-107">Örneğin, Azure modülü, Pester modülü bağlıdır ve sonra da kullanıcı artık Azure modülünü Galeriden kaldırılır, Pester modülü kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c2da-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="1c2da-108">Bir paketi kaldırma yerine ancak, bunu yerine listeden.</span><span class="sxs-lookup"><span data-stu-id="1c2da-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="1c2da-109">**PowerShell Galerisi paketin yapmak etkilenmeden yapar?**</span><span class="sxs-lookup"><span data-stu-id="1c2da-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="1c2da-110">Modül veya PowerShell Galerisi'nde betik gibi bir paket listeden kaldırılırken paketleri sekmesinden kaldırır. Ayrıca, listede bulunmayan paketleri arama çubuğunu kullanarak bulunabilirlik olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="1c2da-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="1c2da-111">Listede bulunmayan bir paketini indirmek için tek yolu paketin sürümü ve tam adını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="1c2da-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="1c2da-112">Bu nedenle, bir paketi listeden kaldırma bağımlı betikler veya diğer modüller keser değil.</span><span class="sxs-lookup"><span data-stu-id="1c2da-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="1c2da-113">Paketi listeden kaldırma için paket Ayrıntılar sayfasını ziyaret edin ve Sil'Module ' seçin.</span><span class="sxs-lookup"><span data-stu-id="1c2da-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="1c2da-114">'Listelendi' onay kutusunun işaretini kaldırın ve Kaydet'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1c2da-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="1c2da-115">**Bir paketi nasıl kaldırabilir miyim?**</span><span class="sxs-lookup"><span data-stu-id="1c2da-115">**How can I remove an package?**</span></span>

<span data-ttu-id="1c2da-116">Paket silme gerekli olduğu bir senaryoda karşılaşırsanız, PowerShell Galerisi yöneticileri ile iletişime geçin.</span><span class="sxs-lookup"><span data-stu-id="1c2da-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="1c2da-117">Geçerli silme senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1c2da-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="1c2da-118">Telif Hakkı ihlalini sorunları.</span><span class="sxs-lookup"><span data-stu-id="1c2da-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="1c2da-119">Paket zararlı içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c2da-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="1c2da-120">Paket hassas verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1c2da-120">Package contains sensitive data.</span></span>

<span data-ttu-id="1c2da-121">Bir silme paket isteği PowerShell Galerisi yöneticilerine göndermek için paketinizin ayrıntı sayfasını ziyaret edin ve Destek'e başvur seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="1c2da-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
