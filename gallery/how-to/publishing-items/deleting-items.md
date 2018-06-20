---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Öğeleri silme
ms.openlocfilehash: 3f67f78d63e5cf797d00ce43f95fb3b4f62d6f7c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218238"
---
# <a name="deleting-items"></a><span data-ttu-id="0b6a2-103">Öğeleri silme</span><span class="sxs-lookup"><span data-stu-id="0b6a2-103">Deleting items</span></span>

<span data-ttu-id="0b6a2-104">Kullanılabilir kalan ona bağlı olarak herkes bölün çünkü PowerShell Galerisi öğeleri kalıcı silinmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0b6a2-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="0b6a2-105">Bunun yerine, PowerShell Galerisi 'öğesi Yönetim sayfasında web sitesinde yapılabilir bir öğe unlist' yolu destekler.</span><span class="sxs-lookup"><span data-stu-id="0b6a2-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="0b6a2-106">Bir öğe listede bulunmayan olduğunda, artık arama ve listeleme, hem de PowerShell Galerisi ve PowerShellGet komutları kullanarak herhangi bir öğeyi görüntülersiniz.</span><span class="sxs-lookup"><span data-stu-id="0b6a2-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="0b6a2-107">Ancak, ne çalışmaya devam etmek otomatik betikler sağlayan olan, tam sürümünü belirterek indirilebilir kalır.</span><span class="sxs-lookup"><span data-stu-id="0b6a2-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="0b6a2-108">Burada öğelerinizi birini silinmelidir düşündüğünüz olağanüstü bir durumla karşılaşırsanız, bu el ile PowerShell Galerisi ekibi tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0b6a2-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="0b6a2-109">Örneğin, bir telif hakkı ihlali sorunu veya zararlı içerik ise, onu silmek için geçerli bir nedeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b6a2-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="0b6a2-110">[PowerShell Galerisi] aracılığıyla bir destek isteği göndermek (http://www.PowerShellGallery.com) bu durumda.</span><span class="sxs-lookup"><span data-stu-id="0b6a2-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>