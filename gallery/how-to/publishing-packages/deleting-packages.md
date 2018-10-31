---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Paketleri silme
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004211"
---
# <a name="deleting-packages"></a><span data-ttu-id="47842-103">Paketleri silme</span><span class="sxs-lookup"><span data-stu-id="47842-103">Deleting Packages</span></span>

<span data-ttu-id="47842-104">Kullanılabilir kalan ona bağlı olarak herkesin sonu çünkü PowerShell Galerisi paketleri kalıcı olarak silinmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="47842-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="47842-105">Bunun yerine, PowerShell Galerisi 'paket Yönetim sayfasında web sitesinde yapılabilir bir paket listeden ' yolu destekler.</span><span class="sxs-lookup"><span data-stu-id="47842-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="47842-106">Bir paket listelenmemiş olduğunda, artık arama ve listelemek, hem de PowerShell Galerisi ve PowerShellGet komutlarını kullanarak herhangi bir paket gösterilir.</span><span class="sxs-lookup"><span data-stu-id="47842-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="47842-107">Ancak, bunu ne çalışmaya devam etmek otomatik betikler sağlar, tam sürümü belirterek indirilebilir kalır.</span><span class="sxs-lookup"><span data-stu-id="47842-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="47842-108">Burada paketlerinizi birini silinmelidir düşündüğünüz bir olağanüstü durumla çalıştırırsanız, bu el ile PowerShell Galerisi ekibi tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="47842-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="47842-109">Örneğin, bir telif hakkı ihlali sorunu veya zararlı içerik yoksa, silmek için geçerli bir sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="47842-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="47842-110">Üzerinden bir destek isteği gönderdiğiniz [PowerShell Galerisi](http://www.PowerShellGallery.com) durumda.</span><span class="sxs-lookup"><span data-stu-id="47842-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>
