---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Öğeleri listeden kaldırma
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="77dc1-103">Öğeleri listeden kaldırma</span><span class="sxs-lookup"><span data-stu-id="77dc1-103">Unlisting items</span></span>

<span data-ttu-id="77dc1-104">**PowerShell Galerisi'nden bir seçenek olarak gösterilmeyen bir öğe kaldırıldığında neden?**</span><span class="sxs-lookup"><span data-stu-id="77dc1-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="77dc1-105">PowerShell Galerisi, kullanıcıların kendilerine öğelerini kalıcı olarak silmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="77dc1-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="77dc1-106">Bu, diğerleri gelecekteki olası kesmeleri hakkında endişelenmeden bulunan öğelerinizi bağımlılıkları yapılacak sağlar.</span><span class="sxs-lookup"><span data-stu-id="77dc1-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="77dc1-107">Örneğin, Azure modülünü Pester modül bağlıdır ve sonra da kullanıcı artık Azure modül Galerisi'nden kaldırılır Pester modülü kullanır.</span><span class="sxs-lookup"><span data-stu-id="77dc1-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="77dc1-108">Bir öğeyi kaldırmak yerine ancak, bunu yerine unlist.</span><span class="sxs-lookup"><span data-stu-id="77dc1-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="77dc1-109">**Ne unlisting PowerShell Galerisi bir öğede musunuz?**</span><span class="sxs-lookup"><span data-stu-id="77dc1-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="77dc1-110">Modül veya PowerShell Galerisi komut gibi bir öğe unlisting öğeleri sekmesinden kaldırır. Ayrıca, listede bulunmayan öğeleri arama çubuğunu kullanarak bulunabilirlik olmaz.</span><span class="sxs-lookup"><span data-stu-id="77dc1-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="77dc1-111">Listede bulunmayan bir öğe indirmek için yalnızca tam adı ve sürümü öğenin belirtmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="77dc1-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="77dc1-112">Bu nedenle, bir öğe unlisting bağımlı komut dosyaları veya diğer modüller kesintiye uğrar değil.</span><span class="sxs-lookup"><span data-stu-id="77dc1-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="77dc1-113">Öğenizi unlist için öğesi Ayrıntılar sayfasını ziyaret edin ve 'Öğeyi sil' seçin.</span><span class="sxs-lookup"><span data-stu-id="77dc1-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="77dc1-114">'Listelendi' onay kutusunun işaretini kaldırın ve Kaydet'i tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77dc1-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="77dc1-115">**Bir öğe nasıl kaldırabilir miyim?**</span><span class="sxs-lookup"><span data-stu-id="77dc1-115">**How can I remove an item?**</span></span>

<span data-ttu-id="77dc1-116">Öğe silme gerekli olduğu bir senaryo karşılaşırsanız, PowerShell Galerisi yöneticileri ile iletişime geçin.</span><span class="sxs-lookup"><span data-stu-id="77dc1-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="77dc1-117">Geçerli silme senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="77dc1-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="77dc1-118">Telif hakkı ihlali sorunları.</span><span class="sxs-lookup"><span data-stu-id="77dc1-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="77dc1-119">Öğe zararlı içerik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="77dc1-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="77dc1-120">Öğesi hassas verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="77dc1-120">Item contains sensitive data.</span></span>

<span data-ttu-id="77dc1-121">Bir silme öğesi isteği PowerShell Galerisi yöneticilere göndermek için öğenizin ayrıntı sayfasını ziyaret edin ve Destek birimine başvurun seçin.</span><span class="sxs-lookup"><span data-stu-id="77dc1-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>