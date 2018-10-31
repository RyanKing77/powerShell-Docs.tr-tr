---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Paket sahiplerini yönetme
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004217"
---
# <a name="managing-package-owners"></a><span data-ttu-id="781e6-103">Paket sahiplerini yönetme</span><span class="sxs-lookup"><span data-stu-id="781e6-103">Managing package owners</span></span>

<span data-ttu-id="781e6-104">PowerShell Galerisi paketinde sahipliğini kimin paket galeride yayımlanmış tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="781e6-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="781e6-105">Bazen bu meta veriler sahip meta veriler paket durumdayken değişebilir olması gerekir yani ilk paket yayımlama ötesinde yönetiliyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="781e6-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="781e6-106">Tüm paket sahipleri eştir.</span><span class="sxs-lookup"><span data-stu-id="781e6-106">All package owners are peers.</span></span>
<span data-ttu-id="781e6-107">Bu, paket sahibinden herhangi bir paketin yeni bir sürümü yayımlayabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="781e6-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="781e6-108">Ayrıca, herhangi bir paket sahibinden tüm paket sahibi tarafından kaldırılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="781e6-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="781e6-109">Diğer sahipleri değerinden daha fazla yetkilisi sahibi yok.</span><span class="sxs-lookup"><span data-stu-id="781e6-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="781e6-110">Bir paketin ilk sahip ayarlama</span><span class="sxs-lookup"><span data-stu-id="781e6-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="781e6-111">PowerShell Galerisi'nde yeni paketi yayımlandığında, ilk sahip paket yayımlanan kullanıcı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="781e6-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="781e6-112">Bu, API tarafından Publish-Module cmdlet'inde anahtar kullanılan belirlenir.</span><span class="sxs-lookup"><span data-stu-id="781e6-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="781e6-113">Sahipleri ekleme</span><span class="sxs-lookup"><span data-stu-id="781e6-113">Adding Owners</span></span>

<span data-ttu-id="781e6-114">Bir paket için PowerShell Galerisi yayımlandıktan sonra ek kullanıcılar sahipleri bir paketin olmaya davet etmek kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="781e6-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="781e6-115">[Oturum](https://powershellgallery.com/users/account/LogOn) bir paketin geçerli sahibi olan hesabının PowerShell Galeriye.</span><span class="sxs-lookup"><span data-stu-id="781e6-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="781e6-116">'Items' sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir paket sayfasına gidin ve ardından [ **My paketlerini Yönet**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="781e6-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="781e6-117">Bir paketin sahibi olarak oturum açtığınızda, sol tarafta tıklayın Yönet'sahipleri ' bağlantısı bulunur.</span><span class="sxs-lookup"><span data-stu-id="781e6-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="781e6-118">Sahip olarak ekleyebilir ve 'Ekle' seçeneğine tıklayın kişinin kullanıcı adı girin.</span><span class="sxs-lookup"><span data-stu-id="781e6-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="781e6-119">E-posta, daha sonra yeni ikincil sahip için bir paket sahibi olmaya davetiye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="781e6-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="781e6-120">Kullanıcı bağlantıyı tıklattığında, sahipleri olarak diğer kullanıcıları kaldırma olanağı dahil olmak üzere, bir paketi üzerinde tam denetimle tam bir ortak sahip değildirler.</span><span class="sxs-lookup"><span data-stu-id="781e6-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="781e6-121">**Not**: yeni sahip, sahiplik doğrulayana kadar bunlar *yapmamayı* paketinin sahibi listelenir.</span><span class="sxs-lookup"><span data-stu-id="781e6-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="781e6-122">Görüntülerken **sahiplerini yönetme** sayfasında, geçerli sahipleri bir "onay" bekleyen giriş görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="781e6-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="781e6-123">Bu davet Kaldırılabilir; diğer sahipleri olarak kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="781e6-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="781e6-124">Bu işlem davet, kullanıcılar diğer kullanıcılar paketlerini sahipleri olarak hatalı bir şekilde eklemesini önler.</span><span class="sxs-lookup"><span data-stu-id="781e6-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="781e6-125">"Yazar" meta veri tamamen serbest biçimli metin olduğunu unutmayın; yalnızca "sahip" denetlenir.</span><span class="sxs-lookup"><span data-stu-id="781e6-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="781e6-126">Sahibi kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="781e6-126">Removing Owners</span></span>

<span data-ttu-id="781e6-127">Bir paket birden fazla sahibe sahip ve bir kaldırılması gerektiğinde, basit bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="781e6-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="781e6-128">[Oturum](https://powershellgallery.com/users/account/LogOn) paketinin; geçerli sahibi olan hesapla PowerShell Galerisi</span><span class="sxs-lookup"><span data-stu-id="781e6-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="781e6-129">Paketleri sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir paket sayfasına gidin ve ardından [ **My paketlerini Yönet**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="781e6-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="781e6-130">Bir paketin sahibi olarak oturum açıldığında, sol tarafta tıklayın Yönet'sahipleri ' bağlantısı bulunur;</span><span class="sxs-lookup"><span data-stu-id="781e6-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="781e6-131">Kaldırılacak sahibi yanındaki 'remove' bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="781e6-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="781e6-132">Paket sahipliğini devretme</span><span class="sxs-lookup"><span data-stu-id="781e6-132">Transferring Package Ownership</span></span>

<span data-ttu-id="781e6-133">Bazen bir kullanıcı başka bir paket sahipliğini devretmek için destek isteklerini aldığımız ancak neredeyse her zaman bu işlemi kendiniz gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="781e6-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="781e6-134">Bir kullanıcıdan sahipliğini aktarma Yukarıdaki iki özelliği yalnızca bir birleşiminden oluşur.</span><span class="sxs-lookup"><span data-stu-id="781e6-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="781e6-135">Geçerli sahip bir ortak sahip olmak için yeni kullanıcı davet eder ve yeni kullanıcı daveti kabul eder;</span><span class="sxs-lookup"><span data-stu-id="781e6-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="781e6-136">Yeni kullanıcı eski kullanıcı sahipleri listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="781e6-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="781e6-137">Bu istek birkaç formlar geldi ancak işlemi çalışır.</span><span class="sxs-lookup"><span data-stu-id="781e6-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="781e6-138">Paket sahipliğini başka bir geliştiriciden değişiyor</span><span class="sxs-lookup"><span data-stu-id="781e6-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="781e6-139">Paket, yanlışlıkla yanlış hesap kullanmanın yayımlandı</span><span class="sxs-lookup"><span data-stu-id="781e6-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="781e6-140">Yalnız bırakılmış paketleri</span><span class="sxs-lookup"><span data-stu-id="781e6-140">Orphaned Packages</span></span>

<span data-ttu-id="781e6-141">Son senaryolardan biri, değil birçok kez oluştu.</span><span class="sxs-lookup"><span data-stu-id="781e6-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="781e6-142">Paketler artık hale gelmiştir ve yalnızca paket sahip hesabı yeni sahip eklemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="781e6-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="781e6-143">Bu senaryonun bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="781e6-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="781e6-144">Sahibin hesabını artık mevcut bir e-posta adresiyle ilişkili ve kullanıcı parolasını unutmuş</span><span class="sxs-lookup"><span data-stu-id="781e6-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="781e6-145">Kayıtlı sahip bir paket oluşturur ve paket sahipliği güncelleştirmek için ulaşılamıyor şirketten</span><span class="sxs-lookup"><span data-stu-id="781e6-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="781e6-146">Yalnızca birkaç paketleri etkiledi bir hata nedeniyle, paket şekilde galeride ownerless</span><span class="sxs-lookup"><span data-stu-id="781e6-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="781e6-147">PowerShell Galerisi Yöneticiler, herhangi bir paket 'Sahipleri Yönet' bağlantısını erişebilir.</span><span class="sxs-lookup"><span data-stu-id="781e6-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="781e6-148">Bir paket gerçek sahibi ve sahiplik izin almak için geçerli sahibi erişilemiyor, 'uygunsuz bağlantıyı PowerShell Galerisi Yöneticiler ulaşmak için galeride kullanın.</span><span class="sxs-lookup"><span data-stu-id="781e6-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="781e6-149">Biz, ardından, paket sahipliğini doğrulamak için bir sürecini takip eder.</span><span class="sxs-lookup"><span data-stu-id="781e6-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="781e6-150">Paketinin sahibi olmanız karar verirseniz, biz paket için kendimize 'Sahipleri Yönet' bağlantısını kullanın ve sahibi olmaya davetiye gönderin.</span><span class="sxs-lookup"><span data-stu-id="781e6-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="781e6-151">Yalnızca bu sahibi olmanız ve bu işlem tarafından durumlarda değişir doğruladıktan sonra yapacağız.</span><span class="sxs-lookup"><span data-stu-id="781e6-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="781e6-152">Çoğu zaman, proje sahibiyle iletişim kurmak için bir yolunu bulmak için paketin proje URL'si kullanacağız, ancak proje sahibi ile iletişim kurulmasından Twitter, e-posta ya da başka araçlar da kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="781e6-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
