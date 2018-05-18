---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Öğe sahiplerini yönetme
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="managing-item-owners"></a><span data-ttu-id="9d1d2-103">Öğe sahiplerini yönetme</span><span class="sxs-lookup"><span data-stu-id="9d1d2-103">Managing item owners</span></span>

<span data-ttu-id="9d1d2-104">PowerShell galerisinde bir öğe sahipliğini kimin öğesi Galerisi'ne yayımlanan tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="9d1d2-105">Bazen bu meta veriler sahibi meta veri öğesi olmamasına karşın değişebilir olması gereken anlamına gelir başlangıç öğesi yayımlama ötesinde yönetilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="9d1d2-106">Tüm öğesi sahiplerinin eştir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-106">All item owners are peers.</span></span>
<span data-ttu-id="9d1d2-107">Başka bir deyişle, tüm öğesi sahibi öğeyi yeni bir sürümü yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="9d1d2-108">Ayrıca, tüm öğesi sahibi diğer öğesi sahibi kaldırabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="9d1d2-109">Sahibi diğer sahipleri'den daha fazla yetkilisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="9d1d2-110">Bir öğenin ilk sahibi ayarlama</span><span class="sxs-lookup"><span data-stu-id="9d1d2-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="9d1d2-111">Yeni bir öğe için PowerShell Galerisi yayımlandığında, ilk sahibi öğesi yayımlanan kullanıcı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="9d1d2-112">Bu, API tarafından Yayımla-Module cmdlet'te anahtar kullanılan belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="9d1d2-113">Sahipleri ekleme</span><span class="sxs-lookup"><span data-stu-id="9d1d2-113">Adding Owners</span></span>

<span data-ttu-id="9d1d2-114">Bir öğe için PowerShell Galerisi yayımlandıktan sonra öğeyi sahipleri olmaya ek kullanıcıları davet kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="9d1d2-115">[Oturum](https://powershellgallery.com/users/account/LogOn) bir öğenin geçerli sahibi olan hesapla PowerShell Galerisi.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="9d1d2-116">'Öğeler' sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir öğe sayfasına gidin ve ardından [ **Yönet My öğeleri**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="9d1d2-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="9d1d2-117">Bir öğenin sahibi olarak oturum açtığında tıklatın sol taraftaki 'Sahiplerini Yönetme' bağlantısı yoktur.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="9d1d2-118">Kullanıcı bir sahibi olarak ekleyin ve 'Ekle'yi tıklatın kişinin adını girin.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="9d1d2-119">Bir e-posta, bir öğenin bir sahibi olmak için bir davet yeni ikincil sahip seçeneğine sonra gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="9d1d2-120">Kullanıcı bağlantıyı tıklattığında, bunlar bir tam ortak sahibi diğer kullanıcıların sahipleri kaldırma özelliği de dahil olmak üzere bir öğe üzerinde tam denetime sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="9d1d2-121">**Not**: yeni sahibi sahipliği onaylayıncaya kadar bunlar *almayacak* öğeyi sahibi olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="9d1d2-122">Görüntülerken **sahiplerini yönetme** sayfasında, geçerli sahipleri bir "onay" bekleyen giriş görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="9d1d2-123">Bu davet Kaldırılabilir; yalnızca diğer sahipleri olarak kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="9d1d2-124">Davet bu işlem, kullanıcıların diğer kullanıcıların kendi öğeleri sahipleri olarak yanlışlıkla eklemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="9d1d2-125">"Yazar" meta veri tamamen serbest biçimli metin olduğunu unutmayın; yalnızca "sahipleri" denetlenir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="9d1d2-126">Sahipleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="9d1d2-126">Removing Owners</span></span>

<span data-ttu-id="9d1d2-127">Birden çok sahipleri bir öğe içeriyor ve bir kaldırılacak gerektiğinde basit bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="9d1d2-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="9d1d2-128">[Oturum](https://powershellgallery.com/users/account/LogOn) bir öğenin; geçerli sahibi olan hesapla PowerShell Galerisi</span><span class="sxs-lookup"><span data-stu-id="9d1d2-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="9d1d2-129">Öğeler sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir öğe sayfasına gidin ve ardından [ **Yönet My öğeleri**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="9d1d2-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="9d1d2-130">Bir öğenin sahibi olarak oturum açmış olduğunda 'Sahiplerini Yönetme' bağlantısını tıklatın sol taraftaki;</span><span class="sxs-lookup"><span data-stu-id="9d1d2-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="9d1d2-131">Kaldırılacak sahibi yanındaki 'Kaldır' bağlantısını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="9d1d2-132">Öğe sahipliğini aktarma</span><span class="sxs-lookup"><span data-stu-id="9d1d2-132">Transferring Item Ownership</span></span>

<span data-ttu-id="9d1d2-133">Biz bazen öğesi sahipliği bir kullanıcıdan başka bir bilgisayara aktarmak için destek isteklerini alır ancak bunu kendiniz neredeyse her zaman gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="9d1d2-134">Bir kullanıcıdan sahipliğini aktarma Yukarıdaki iki özelliği yalnızca bir birleşiminden oluşur.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="9d1d2-135">İkincil sahip olmak için yeni kullanıcı geçerli sahibi başvurulmasını ve yeni kullanıcı daveti kabul eder;</span><span class="sxs-lookup"><span data-stu-id="9d1d2-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="9d1d2-136">Yeni kullanıcı eski kullanıcı sahipler listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="9d1d2-137">Bu istek altında birkaç forms geldi, ancak işlem aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="9d1d2-138">Öğe sahipliği bir geliştiriciden diğerine değiştiriyor.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-138">The item ownership is changing from one developer to another</span></span>
- <span data-ttu-id="9d1d2-139">Öğe, yanlışlıkla yanlış hesap kullanılarak yayımlandı</span><span class="sxs-lookup"><span data-stu-id="9d1d2-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="9d1d2-140">Yalnız bırakılmış öğeleri</span><span class="sxs-lookup"><span data-stu-id="9d1d2-140">Orphaned Items</span></span>

<span data-ttu-id="9d1d2-141">Bir son senaryo, değil birçok kez oluştu.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="9d1d2-142">Öğeleri artık duruma gelmiş ve yalnızca öğesi sahip hesabı yeni sahipleri eklemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="9d1d2-143">Bu senaryonun bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d1d2-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="9d1d2-144">Sahibin hesabını artık mevcut bir e-posta adresiyle ilişkili ve kullanıcı parolalarını unutan</span><span class="sxs-lookup"><span data-stu-id="9d1d2-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="9d1d2-145">Kayıtlı sahip öğeyi üreten ve madde sahipliği güncelleştirmek için ulaşılamıyor şirket ayrıldı</span><span class="sxs-lookup"><span data-stu-id="9d1d2-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
- <span data-ttu-id="9d1d2-146">Yalnızca öğeleri sayıda etkilediğini bir hata nedeniyle, şekilde galeride ownerless öğedir</span><span class="sxs-lookup"><span data-stu-id="9d1d2-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="9d1d2-147">PowerShell Galerisi Yöneticiler herhangi bir öğeyi 'Sahiplerini Yönetme' bağlantısını erişebilir.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="9d1d2-148">Öğesinin gerçek sahibiyseniz ve sahipliği izinleri kazanmak için geçerli sahibi ulaşamıyor, 'Rapor kötüye' bağlantısını PowerShell Galerisi Yöneticiler ulaşması galeride kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="9d1d2-149">Biz, ardından öğenin, sahipliği doğrulamak için bir sürecini takip eder.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="9d1d2-150">Öğenin bir sahibi olması gereken karar verirseniz, biz 'Sahiplerini Yönetme' bağlantıyı öğe için kendisini kullanın ve sahibi olmak için davet gönderin.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="9d1d2-151">Biz yalnızca bu bir sahip olması gerekir ve bu işlem tarafından durumlar değişir doğruladıktan sonra yapın.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="9d1d2-152">Çoğu zaman, biz öğesi'nin proje URL'sini bir proje sahibine başvurun şekilde bulmak için kullanır, ancak proje sahibi ile iletişim için Twitter, e-posta ya da başka araçlar da kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="9d1d2-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>