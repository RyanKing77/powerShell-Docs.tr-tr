---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi hesabı oluşturma
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522852"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="690c7-103">PowerShell Galerisi hesabı oluşturma</span><span class="sxs-lookup"><span data-stu-id="690c7-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="690c7-104">Her şeyi PowerShell Galerisi'nden yayımlamadan önce PowerShell Galerisi hesabı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="690c7-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="690c7-105">PowerShell Galerisi hesapları bir e-posta etkin bir oturum açma hesabına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="690c7-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="690c7-106">Bu hesap Azure Active Directory hesabını veya bir e-posta hesabından outlook.com veya hotmail.com gibi a Microsoft ID olabilir.</span><span class="sxs-lookup"><span data-stu-id="690c7-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="690c7-107">PowerShell Galerisi hesabı oluşturmak için Git [ https://PowerShellGallery.com ](https://PowerShellGallery.com) tıklayın **oturum** aşağıdaki görüntüde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="690c7-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Yeni hesabı Kaydet](../../Images/CreateAccount-Register.png)

<span data-ttu-id="690c7-109">Bir Azure Active Directory hesabını kullanmayı tercih **iş veya Okul hesabı**ve hesabınızla oturum açın.</span><span class="sxs-lookup"><span data-stu-id="690c7-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="690c7-110">A Microsoft ID kullanmayı tercih **kişisel hesap** ve oturum açın.</span><span class="sxs-lookup"><span data-stu-id="690c7-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="690c7-111">Ardından, PowerShell Galerisi için bir kullanıcı adı oluşturmanız istenir.</span><span class="sxs-lookup"><span data-stu-id="690c7-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="690c7-112">Kullanım koşulları ve gizlilik ilkesi gözden geçirin, bir kullanıcı adı girin ve ardından **kaydetme**.</span><span class="sxs-lookup"><span data-stu-id="690c7-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="690c7-113">Hesap adı, oluşturulduktan sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="690c7-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="690c7-114">Daha fazla bilgi için [öğe sahiplerini yönetme](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="690c7-114">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="690c7-115">PowerShell Galerisi hesaplar için önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="690c7-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="690c7-116">PowerShell Galerisi hesabınızla kullanılan e-posta hesabı etkin bir şekilde izlemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="690c7-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="690c7-117">PowerShell Galerisi öğelerinin sahibi olan tüm iletişim bu e-posta adresidir.</span><span class="sxs-lookup"><span data-stu-id="690c7-117">All communication with owners of PowerShell Gallery items is through this email address.</span></span> <span data-ttu-id="690c7-118">PowerShell Galerisi operasyon ekibinin öğesi sahibi ile iletişim kuramıyor, biz bir öğeyi silmek için gerekli.</span><span class="sxs-lookup"><span data-stu-id="690c7-118">If the PowerShell Gallery Operations team is unable to contact an item owner, we may be required to delete an item.</span></span>

<span data-ttu-id="690c7-119">PowerShell Galerisi için sık sık yayımlayın kuruluşların bu amaç için benzersiz bir dış hesap oluşturun.</span><span class="sxs-lookup"><span data-stu-id="690c7-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="690c7-120">Kuruluşunuzda bir adresine bildirimleri iletecek şekilde e-posta iletme kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="690c7-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="690c7-121">Birden fazla sahibe sahip bir öğe ilişkilendirildiğinde, tüm PowerShell Galerisi bildirimleri tüm sahiplerine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="690c7-121">When multiple owners are associated with an item, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="690c7-122">Daha fazla bilgi için [öğe sahiplerini yönetme](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="690c7-122">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>
