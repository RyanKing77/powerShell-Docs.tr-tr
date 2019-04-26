---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Sosyal medya veya yorumlar geri bildirim sağlama
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076081"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="d7505-103">Sosyal medya veya yorumlar geri bildirim sağlama</span><span class="sxs-lookup"><span data-stu-id="d7505-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="d7505-104">PowerShell Galerisi kullanıcılar üzerindeki bir paket genel geri bildirim sağlamak için iki yaklaşım destekler:</span><span class="sxs-lookup"><span data-stu-id="d7505-104">The PowerShell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="d7505-105">"Facebook, LinkedIn ve Twitter sosyal medya siteleri paketinde paylaşmak için" sol kenarda bağlantıları kullanın</span><span class="sxs-lookup"><span data-stu-id="d7505-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="d7505-106">Açıklama özelliği üzerindeki bir paket açıklamaları gönderin ve bunlar yayımlama paketleri için yorum izlemek yazarlar izin vermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7505-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="d7505-107">Sosyal medya geri bildirim</span><span class="sxs-lookup"><span data-stu-id="d7505-107">Social Media Feedback</span></span>

<span data-ttu-id="d7505-108">Her bir paket PowerShell Galerisi'nde sayfanın sol tarafındaki Facebook, LinkedIn ve Twitter için bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="d7505-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="d7505-109">Bu bağlantılara tıklayarak sosyal medya sitesini açın ve hızlı bir şekilde paket Bağlantısı Paylaşımı izin.</span><span class="sxs-lookup"><span data-stu-id="d7505-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="d7505-110">Kullanıcıların siteye PowerShell Galerisi paket paylaşımı için seçtiğiniz oturum açmalısınız.</span><span class="sxs-lookup"><span data-stu-id="d7505-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="d7505-111">Kullanıcılar, bir paketi bir şey başkalarına önerme olasılığınız olduğunu fark ederseniz, bunu yapmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="d7505-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="d7505-112">PowerShell Galerisi "paylaşımlar" paketi için her bir sosyal medya sitesini denetler ve her sosyal medya siteleri bir görüntü paketini kaç kez paylaşıldı.</span><span class="sxs-lookup"><span data-stu-id="d7505-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="d7505-113">Bu yalnızca bir şey paylaşılan bir kez sayısını gösteren bu yana olacak diğer kullanıcılar olarak yorumlanan "Paket özelleştirebilir".</span><span class="sxs-lookup"><span data-stu-id="d7505-113">Since this shows only the count of times something has been shared, it will be interpreted other users as "liking" the package.</span></span>

## <a name="comments"></a><span data-ttu-id="d7505-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7505-114">Comments</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7505-115">Livefyre yorum, bir üçüncü taraf satıcı tarafından sağlanan ve artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d7505-115">Livefyre commenting is provided by a third-party vendor and is no longer supported.</span></span>
> <span data-ttu-id="d7505-116">Livefyre yorum artık başlangıç PowerShell galerisinde kullanılabilir olacak 01/05/2019.</span><span class="sxs-lookup"><span data-stu-id="d7505-116">Livefyre commenting will no longer be available on the PowerShell Gallery starting 05/01/2019.</span></span> 

<span data-ttu-id="d7505-117">PowerShell Galerisi LiveFyre hizmet paketleri açıklama eklemek kullanıcıların kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7505-117">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="d7505-118">Öneriler veya geri bildirim sahip kullanıcılar, paket sayfasını ziyaret herkes tarafından görülebilir geri bildirim sağlamak için bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7505-118">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="d7505-119">Paket sahipleri, bu geri bildirim izleyebilirsiniz ve birisi bir yorum gönderildiğinde bildirim.</span><span class="sxs-lookup"><span data-stu-id="d7505-119">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="d7505-120">Microsoft tarafından yönetilmez ve kullanmak için benzersiz bir oturum açma gerektiren ayrı bir hizmet olan LiveFyre üzerinde açıklama sistemini temel alır.</span><span class="sxs-lookup"><span data-stu-id="d7505-120">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="d7505-121">Bir yorum yazın veya açıklamaları, paketlerinizi birini izleyin tercih ilk kez bir LiveFyre hesabı oluşturmanız istenir.</span><span class="sxs-lookup"><span data-stu-id="d7505-121">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="d7505-122">Bir LiveFyre hesabı oluşturdunuz ve oturum, paketi geri bildirim sağlayan bir açıklama hazırlayabilirsiniz, "Post açıklama..."'ye tıklayın Açıklamanın hemen görünmez.</span><span class="sxs-lookup"><span data-stu-id="d7505-122">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="d7505-123">Galeri paketleri için herhangi bir yorum PowerShell Galerisi yöneticileri tarafından yönetiliyor ve yayımlanan ve başkalarına görünür edilmeden önce tüm gönderileri Moderatörler tarafından gözden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d7505-123">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="d7505-124">Amacımız açıklamaları yönetme de PowerShell Galerisi ile tutarlı genel davranış Hizala sağlamaktır [kullanım](https://www.powershellgallery.com/policies/Terms).</span><span class="sxs-lookup"><span data-stu-id="d7505-124">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="d7505-125">Paket sahipleri için LiveFyre gönderilen yorumlar izlemeleri önerilir.</span><span class="sxs-lookup"><span data-stu-id="d7505-125">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="d7505-126">Bir LiveFyre hesabı gereklidir ve LiveFyre içinde paketinizi yayımlamak için kullandığınız aynı e-posta adresini kullanmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="d7505-126">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="d7505-127">Yorumları takip etmeye LiveFyre oturum ve burada bir sahibi olarak listelenmez herhangi bir paket gidin.</span><span class="sxs-lookup"><span data-stu-id="d7505-127">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="d7505-128">Her paket sonundaki Açıklama kutusuna Aşağıda, bkz: "izleyin +".</span><span class="sxs-lookup"><span data-stu-id="d7505-128">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="d7505-129">Bu tıkladığınızda LiveFyre kayıtlı e-posta adresine bir e-posta pakete yapılan hiçbir zaman yeni yorumları gönderin.</span><span class="sxs-lookup"><span data-stu-id="d7505-129">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>
