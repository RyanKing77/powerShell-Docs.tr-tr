---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery, GDPR
title: PowerShell Galerisi GDPR uyumluluk
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189763"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="c2fab-103">PowerShell Galerisi GDPR uyumluluk</span><span class="sxs-lookup"><span data-stu-id="c2fab-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="c2fab-104">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="c2fab-104">Overview</span></span>

<span data-ttu-id="c2fab-105">Mayıs 2018 genel veri koruma düzenleme (GDPR), bir Avrupa gizlilik yasalarına etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="c2fab-106">GDPR şirketler, devlet dairesi, kar kaybı olmayan ve diğer kuruluşlardan teklif mal ve hizmet Avrupa Birliği (AB) ya da, kişilere toplamak ve analiz etmek için AB Satışlar bağlı veri yeni kuralları uygular.</span><span class="sxs-lookup"><span data-stu-id="c2fab-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="c2fab-107">Bulunduğunuz olsun GDPR geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="c2fab-108">Bu makalede PowerShell Galerisi'nden kişisel verilerini silmek adımlar sağlar ve sizin yükümlülüklerin GDPR altında desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="c2fab-109">GDPR hakkında genel bilgi arıyorsanız bkz [Hizmeti'ne güvenen portal GDPR bölümünü](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="c2fab-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="c2fab-110">Kişisel olarak tanımlanabilecek veriler</span><span class="sxs-lookup"><span data-stu-id="c2fab-110">Personally identifiable data</span></span>

<span data-ttu-id="c2fab-111">PowerShell Galerisi kişisel bilgiler içerebilir kullanıcılar tarafından sağlanan aşağıdaki bilgileri depolar:</span><span class="sxs-lookup"><span data-stu-id="c2fab-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="c2fab-112">PowerShell Galerisi hesabı</span><span class="sxs-lookup"><span data-stu-id="c2fab-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="c2fab-113">PowerShell Galerisi yayımlanan öğeler</span><span class="sxs-lookup"><span data-stu-id="c2fab-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="c2fab-114">E-posta yazışmaları PowerShell Galerisi ekibi ile</span><span class="sxs-lookup"><span data-stu-id="c2fab-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="c2fab-115">Kullanıcıların çoğunun bir PowerShell Galerisi hesabı oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="c2fab-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="c2fab-116">Bir öğe yayımlamak veya PowerShell galerisinde "Kişi sahip" Bu özelliği kullanmak için çalıştırmayacağınız sürece bir hesap gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="c2fab-117">Kullanıcı tarafından başlatılan e-posta yazışmaları dışında bir hesap oluşturmadınız kullanıcıların kişisel olarak tanımlanabilecek veriler PowerShell Galerisi depolamaz.</span><span class="sxs-lookup"><span data-stu-id="c2fab-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="c2fab-118">Bir PowerShell Galerisi hesabı oluşturma kullanıcılar öğeleri PowerShell Galerisi yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fab-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="c2fab-119">Bu öğeler PowerShell kodu olması beklenir, ancak kişisel bilgiler dahil olmak üzere diğer bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="c2fab-120">Aşağıdaki bilgiler tüm öğelerin nasıl erişebileceğini gösterecektir PowerShell Galerisine yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="c2fab-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="c2fab-121">PowerShell Galerisi verilerin DSR aktarma</span><span class="sxs-lookup"><span data-stu-id="c2fab-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="c2fab-122">Aşağıdaki bölümlerde PowerShell Galerisi veri konu isteklerinin (DSR) nasıl destekler? PowerShell galerisinde depolanan bilgileri dışarı aktarma ve bu bilgilerin silme isteği nasıl açıklayarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2fab-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="c2fab-123">E-posta</span><span class="sxs-lookup"><span data-stu-id="c2fab-123">Email</span></span>

<span data-ttu-id="c2fab-124">E-posta yazışmaları aşağıdakilerden herhangi birini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="c2fab-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="c2fab-125">PowerShell Galerisi Kod Analizi tarar, öğeleri PowerShell Galerisi yayımladığınız herhangi bir öğe ile ilgili bir sorun tespit sahiplerine gönderilen e-posta</span><span class="sxs-lookup"><span data-stu-id="c2fab-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="c2fab-126">"Bize başvurun" sayfasında e-posta adresini kullanarak PowerShell Galerisi takımı herkes tarafından gönderilen e-posta (cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="c2fab-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="c2fab-127">PowerShell Galerisi bir öğede sahibi e-posta göndermek için PowerShell galerisinde "Kişi sahip" özelliğini kullanan kullanıcılar kayıtlı</span><span class="sxs-lookup"><span data-stu-id="c2fab-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="c2fab-128">PowerShell Galerisi veya tarafından gönderilen e-postaların kötü amaçlı kod PowerShell Galerisi bulunmasına olası güvenlik araştırmalar desteklemek için 90 günlük bir bekletme ilkesi olması.</span><span class="sxs-lookup"><span data-stu-id="c2fab-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="c2fab-129">E-posta İlkesi tarafından 90 gün sonra silinir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="c2fab-130">E-posta adresinizi ve PowerShell Galerisi bilgisayardan veya önceki 90 gün içinde gönderilen tüm e-postaları kopyalarını isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="c2fab-131">Bu ilişkiyi istemek için bir e-posta Gönder cgadmin@microsoft.com, başlıkla: "Bu hesaba ilişkin e-posta talebi DSR".</span><span class="sxs-lookup"><span data-stu-id="c2fab-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="c2fab-132">İleti gövdesinde isteyen hangi bilgilerin belirtin (örneğin: Lütfen bu e-posta adresinden alınan veya gönderilen tüm e-postalar gönderin.) İsteğin 90 gün içinde e-posta adresinizi içeren tüm e-postalar 7 iş günü içinde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="c2fab-133">PowerShell Galerisi hesap bilgileri</span><span class="sxs-lookup"><span data-stu-id="c2fab-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="c2fab-134">Bir PowerShell Galerisi hesabı oluşturduysanız, PowerShell galerisinde aşağıdaki adımları uygulayarak zamandır saklanan tüm kişisel bilgileri bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c2fab-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="c2fab-135">PowerShell Galerisi oturum açın, sonra kullanıcı adınıza tıklayın</span><span class="sxs-lookup"><span data-stu-id="c2fab-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="c2fab-136">Görüntülenen sonraki sayfa PowerShell Galerisi hesabı için kullanılan e-posta adresi gösterir hesap sayfa.</span><span class="sxs-lookup"><span data-stu-id="c2fab-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="c2fab-137">PowerShell galerisinde birden fazla hesabı oluşturduysanız, her hesap için bu adımları yinelemeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="c2fab-138">PowerShell galerisinde öğeleri</span><span class="sxs-lookup"><span data-stu-id="c2fab-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="c2fab-139">PowerShell Galerisi yayımlanan verme öğeleri kolaylaştırmak için biz "GetPSGalleryItemsForAuthor" komut dosyası için PowerShell Galerisi yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="c2fab-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="c2fab-140">Bu komut dosyası her bir sürümüyle öğesinde depolanan Yazar bilgilere dayanarak PowerShell Galerisi yerleştirin her öğenin bir kopyasını dışa aktarır.</span><span class="sxs-lookup"><span data-stu-id="c2fab-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="c2fab-141">Öğenizi yayımladığınızda Yazar öğesi bildiriminde depolanır.</span><span class="sxs-lookup"><span data-stu-id="c2fab-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="c2fab-142">Yazarın PowerShell galerisinde kullandığınız hesabı ile aynı kimlik olduğunu garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c2fab-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="c2fab-143">Başka bir değer yazar alanı kullanıyorsanız, bu komut dosyası kullanırken bu değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="c2fab-144">Aşağıdaki PowerShell komutunu kullanarak betiği yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c2fab-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="c2fab-145">Aşağıdaki PowerShell komutlarını çalıştırarak komut dosyasını doğrudan, ardından çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c2fab-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="c2fab-146">Yazar ve kaydedilmesi için öğelerini bir klasörü sisteminizdeki sağlamanız istenir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="c2fab-147">PowerShell Galerisi'nden kişisel verileri silme</span><span class="sxs-lookup"><span data-stu-id="c2fab-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="c2fab-148">PowerShell Galerisi hesabınız veya PowerShell galerisinde sahip herhangi bir öğeyi silmek için e-posta Gönder cgadmin@microsoft.com başlıkla: "GDPR isteği bu hesaba ilişkin öğeleri için".</span><span class="sxs-lookup"><span data-stu-id="c2fab-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="c2fab-149">İleti gövdesinde hangi bilgilerin silinen istediğiniz durumu.</span><span class="sxs-lookup"><span data-stu-id="c2fab-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="c2fab-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c2fab-150">For example:</span></span>

* <span data-ttu-id="c2fab-151">Lütfen "öğe adı" Benim öğesinin sürüm x.y.z silin</span><span class="sxs-lookup"><span data-stu-id="c2fab-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="c2fab-152">Lütfen "öğe adı" öğe tüm sürümlerini silin</span><span class="sxs-lookup"><span data-stu-id="c2fab-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="c2fab-153">Lütfen PowerShell Galerisi Hesabımı silin</span><span class="sxs-lookup"><span data-stu-id="c2fab-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="c2fab-154">PowerShell Galerisi Yöneticiler 7 iş günü içinde yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="c2fab-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="c2fab-155">İstek gönderildikten sonra 30 gün içinde belirtilen öğeler silinecek.</span><span class="sxs-lookup"><span data-stu-id="c2fab-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
