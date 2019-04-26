---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058208"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="ce73f-102">Düğüm ve Yapılandırma kimliklerinin ayrımı</span><span class="sxs-lookup"><span data-stu-id="ce73f-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="ce73f-103">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="ce73f-103">Overview</span></span>

<span data-ttu-id="ce73f-104">DSC çekme modunda kullanılırken daha esnek ve kolaylaştırılmış bir deneyim sağlamak amacıyla bir dizi özelliği bu sürümde ekledik.</span><span class="sxs-lookup"><span data-stu-id="ce73f-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="ce73f-105">Bu özellikler, kolay kurulum ve yine de durum izleme ve raporlama bilgileri her düğüm için ayrı ayrı sırasında birden fazla düğümde yapılandırmaları dağıtma esnekliğine sahip olmasını sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce73f-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="ce73f-106">Bu özellikler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ce73f-106">These features are as follows:</span></span>

* <span data-ttu-id="ce73f-107">Bir bilgisayar yapılandırmasını tanımlayan bir yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="ce73f-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="ce73f-108">Bu ad, birden çok hedef düğümler tarafından paylaşılabilir</span><span class="sxs-lookup"><span data-stu-id="ce73f-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="ce73f-109">Tek bir düğüme benzersiz olarak tanımlayan bir Aracısı kimliği</span><span class="sxs-lookup"><span data-stu-id="ce73f-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="ce73f-110">Kayıt adımı yalnızca bir hedef düğümü ilk kez oluşan bir çekme sunucusuna bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ce73f-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="ce73f-111">**Not:** Bu özellikler ve İşlevler eklendi ve mevcut çekme özellikler ve kavramlar değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="ce73f-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="ce73f-112">Bu yeni özelliklerin veya eskiler bu sürümünde yeni çekme sunucusu ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce73f-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="ce73f-113">Daha fazla bilgi için [yapılandırma adlarını kullanarak çekme istemcisi ayarlama](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="ce73f-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
