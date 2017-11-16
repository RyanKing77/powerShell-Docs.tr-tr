---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="8808d-102">Düğüm ve yapılandırma kimlikleri ayrımı</span><span class="sxs-lookup"><span data-stu-id="8808d-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="8808d-103">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="8808d-103">Overview</span></span>

<span data-ttu-id="8808d-104">DSC çekme modunda kullanılırken daha esnek ve kolaylaştırılmış bir deneyim sunmak için çok sayıda özelliği bu sürümde ekledik.</span><span class="sxs-lookup"><span data-stu-id="8808d-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="8808d-105">Bu özellikler kolayca Kurulum yapılandırmalarını ve birden çok düğüm arasında hala durumu izleme ve raporlama bilgileri her düğüm için ayrı ayrı sırasında dağıtın esnekliğine sahip olanak tanımak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8808d-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span> <span data-ttu-id="8808d-106">Bu özellikler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8808d-106">These features are as follows:</span></span>

* <span data-ttu-id="8808d-107">Bir bilgisayar yapılandırmasını tanımlayan bir yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="8808d-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="8808d-108">Bu adı birden çok hedef düğümleri tarafından paylaşılabilir</span><span class="sxs-lookup"><span data-stu-id="8808d-108">This name can be shared by multiple target nodes</span></span> 
* <span data-ttu-id="8808d-109">Tek bir düğüm benzersiz olarak tanımlayan bir aracı kimliği</span><span class="sxs-lookup"><span data-stu-id="8808d-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="8808d-110">Bir çekme sunucusuna yalnızca bir hedef düğümü ilk kez oluşan bir kayıt adımından bağlanır</span><span class="sxs-lookup"><span data-stu-id="8808d-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="8808d-111">**Not:** bu özellikler ve işlevsellik eklenmiştir ve varolan çekme özelliklerinin ve kavramlarının değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="8808d-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="8808d-112">Bu yeni özellikleri veya eskiler bu sürümde sevkiyat yeni çekme sunucusuyla kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8808d-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="8808d-113">Daha fazla bilgi için bkz: [yapılandırma adları kullanarak bir çekme istemci ayarlama](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="8808d-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>

