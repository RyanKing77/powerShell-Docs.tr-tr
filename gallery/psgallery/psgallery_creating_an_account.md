---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Bir PowerShell Galerisi hesabı oluşturma
ms.openlocfilehash: c9c263a1926957cbdf059e062326b1903c117f46
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="52c76-103">Bir PowerShell Galerisi hesabı oluşturma</span><span class="sxs-lookup"><span data-stu-id="52c76-103">Creating a PowerShell Gallery Account</span></span>

<span data-ttu-id="52c76-104">Bir PowerShell Galerisi hesabı herhangi bir şey için PowerShell Galerisi yayımlamadan önce oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52c76-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="52c76-105">PowerShell Galerisi hesapları e-posta etkin bir Azure Active Directory hesabı veya bir Microsoft e-posta hesabıyla (bir etki alanı outlook.com, hotmail.com, vs.) ile bağlantılı olması gerekir</span><span class="sxs-lookup"><span data-stu-id="52c76-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="52c76-106">Bir PowerShell Galerisi hesabı oluşturmak için şu adrese gidin https://PowerShellGallery.com ve "Kayıt"'i tıklatın (aşağıdaki görüntü bakın).</span><span class="sxs-lookup"><span data-stu-id="52c76-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![Yeni hesabı Kaydettir](./images/CreatingAccount-Register.png)

<span data-ttu-id="52c76-108">Sonraki sayfada bir Azure Active Directory hesabı kullanmak için "İş veya Okul hesabı" seçin ve hesabınızla oturum açın.</span><span class="sxs-lookup"><span data-stu-id="52c76-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="52c76-109">-Hotmail.com veya Outlook.com domain - birinde gibi bir Microsoft hesabı kullanmak için "Kişisel hesap" seçin ve oturum açın.</span><span class="sxs-lookup"><span data-stu-id="52c76-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="52c76-110">Oturum açtıktan sonra PowerShell Galerisi için bir kullanıcı adı oluşturmak için istenir.</span><span class="sxs-lookup"><span data-stu-id="52c76-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="52c76-111">Bağlı kullanım koşulları ve gizlilik ilkesini inceleyin, bir kullanıcı adı girin ve Kaydet'i tıklatın.</span><span class="sxs-lookup"><span data-stu-id="52c76-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="52c76-112">Not: Bu hesap adı oluşturulduktan sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="52c76-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="52c76-113">Bkz: [yönetme öğesi sahiplerinin](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) bu konuyla ilgili ek ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="52c76-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="52c76-114">PowerShell Galerisi hesaplar için önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="52c76-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="52c76-115">PowerShell Galerisi hesabınızla kullanılan e-posta hesabı etkin bir şekilde izlenmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="52c76-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="52c76-116">PowerShell Galerisi hesabınızla ilişkili adresini kullanarak e-posta aracılığıyla tüm communiction PowerShell galeri öğeleri sahipleri sahip olur.</span><span class="sxs-lookup"><span data-stu-id="52c76-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="52c76-117">Bir öğe sahibine başvurun bağlanamıyoruz, işletim ekibi bazı koşullarda bir öğeyi silmek için gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="52c76-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="52c76-118">PowerShell galerisinde genellikle yayımlamak kuruluşlar, Outlook.com veya başka bir Microsoft hesabı etki alanında bu amaç için benzersiz bir hesabı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52c76-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="52c76-119">Çoğu durumda bu hesabı düzenli olarak izlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="52c76-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="52c76-120">En iyi uygulama bu durumda Outlook iletme genellikle bir sahibi öğesi görüntülemenize tarafından izlenecek kuruluş içinde başka bir hesap için e-posta göndermek için kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="52c76-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="52c76-121">Bir öğesiyle ilişkili birden çok sahipleri varsa, PowerShell Galerisi'nden gelen tüm iletişimlerin tüm sahiplerine gidin.</span><span class="sxs-lookup"><span data-stu-id="52c76-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="52c76-122">Bkz: [yönetme öğesi sahiplerinin](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) sahipleri için bir öğe ekleme hakkında ek bilgi.</span><span class="sxs-lookup"><span data-stu-id="52c76-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>