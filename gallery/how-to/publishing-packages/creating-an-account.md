---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi hesabı oluşturma
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084223"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="3a593-103">PowerShell Galerisi hesabı oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a593-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="3a593-104">Her şeyi PowerShell Galerisi'nden yayımlamadan önce PowerShell Galerisi hesabı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a593-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="3a593-105">PowerShell Galerisi hesapları bir e-posta etkin bir oturum açma hesabına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a593-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="3a593-106">Bu hesap Azure Active Directory hesabını veya bir e-posta hesabından outlook.com veya hotmail.com gibi a Microsoft ID olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a593-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="3a593-107">PowerShell Galerisi hesabı oluşturmak için Git [ https://PowerShellGallery.com ](https://PowerShellGallery.com) tıklayın **oturum** aşağıdaki görüntüde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3a593-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Yeni hesabı Kaydet](../../Images/CreateAccount-Register.png)

<span data-ttu-id="3a593-109">Bir Azure Active Directory hesabını kullanmayı tercih **iş veya Okul hesabı**ve hesabınızla oturum açın.</span><span class="sxs-lookup"><span data-stu-id="3a593-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="3a593-110">A Microsoft ID kullanmayı tercih **kişisel hesap** ve oturum açın.</span><span class="sxs-lookup"><span data-stu-id="3a593-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="3a593-111">Ardından, PowerShell Galerisi için bir kullanıcı adı oluşturmanız istenir.</span><span class="sxs-lookup"><span data-stu-id="3a593-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="3a593-112">Kullanım koşulları ve gizlilik ilkesi gözden geçirin, bir kullanıcı adı girin ve ardından **kaydetme**.</span><span class="sxs-lookup"><span data-stu-id="3a593-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="3a593-113">Hesap adı, oluşturulduktan sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="3a593-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="3a593-114">Daha fazla bilgi için [paketinin sahiplerini yönetme](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="3a593-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="3a593-115">PowerShell Galerisi hesaplar için önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="3a593-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="3a593-116">PowerShell Galerisi hesabınızla kullanılan e-posta hesabı etkin bir şekilde izlemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3a593-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="3a593-117">PowerShell Galerisi paketlerin sahibi olan tüm iletişim bu e-posta adresidir.</span><span class="sxs-lookup"><span data-stu-id="3a593-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="3a593-118">PowerShell Galerisi operasyon ekibinin bir paket sahibi ile iletişim kuramıyor, biz bir paketi silmek için gerekli.</span><span class="sxs-lookup"><span data-stu-id="3a593-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="3a593-119">PowerShell Galerisi için sık sık yayımlayın kuruluşların bu amaç için benzersiz bir dış hesap oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a593-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="3a593-120">Kuruluşunuzda bir adresine bildirimleri iletecek şekilde e-posta iletme kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="3a593-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="3a593-121">Birden çok sahipleri bir paket ile ilişkili olduğunda, tüm PowerShell Galerisi bildirimleri tüm sahiplerine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3a593-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="3a593-122">Daha fazla bilgi için [paketinin sahiplerini yönetme](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="3a593-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
