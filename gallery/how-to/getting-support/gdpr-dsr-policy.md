---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery, GDPR
title: PowerShell Galerisi GDPR uyumluluğu
ms.openlocfilehash: 14b82fa07df52f02f0d7577cb0eef70faa4285a2
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893255"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="93b2f-103">PowerShell Galerisi GDPR uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="93b2f-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="93b2f-104">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="93b2f-104">Overview</span></span>

<span data-ttu-id="93b2f-105">Mayıs 2018'de genel veri koruma yönetmeliği (GDPR), bir Avrupa gizlilik yasaları etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="93b2f-106">GDPR, yeni şirketler, devlet kurumları, gütmeyen ve teklif mal ve hizmet kişilere Avrupa Birliği (AB) veya AB vatandaşlar için bağlı verileri toplayıp analiz, diğer kuruluşların kuralları uygular.</span><span class="sxs-lookup"><span data-stu-id="93b2f-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="93b2f-107">Burada, nerede olursanız olun GDPR geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="93b2f-108">Bu makalede, PowerShell Galerisi'nden kişisel verilerini silme adımlar sağlar ve sizin yükümlülükleriniz GDPR altında desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="93b2f-109">GDPR hakkında genel bilgiler arıyorsanız bkz [hizmet güveni portalı GDPR bölümünü](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="93b2f-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="93b2f-110">Kişisel olarak tanımlanabilen veriler</span><span class="sxs-lookup"><span data-stu-id="93b2f-110">Personally identifiable data</span></span>

<span data-ttu-id="93b2f-111">PowerShell Galerisi, kişisel bilgileri içerebilen kullanıcılar tarafından sağlanan aşağıdaki bilgileri depolar:</span><span class="sxs-lookup"><span data-stu-id="93b2f-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="93b2f-112">PowerShell Galerisi hesabı</span><span class="sxs-lookup"><span data-stu-id="93b2f-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="93b2f-113">PowerShell Galerisi'nde yayımlanmış öğeler</span><span class="sxs-lookup"><span data-stu-id="93b2f-113">Items published to the PowerShell Gallery</span></span>
- <span data-ttu-id="93b2f-114">PowerShell Galerisi ekibi ile e-posta yazışmaları</span><span class="sxs-lookup"><span data-stu-id="93b2f-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="93b2f-115">Çoğu kullanıcı, bir PowerShell Galerisi hesabı oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="93b2f-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="93b2f-116">Bir öğe yayımlayın veya PowerShell galerisinde "Kişi sahip" Bu özelliği kullanmak için çalıştırmayacağınız sürece bir hesap gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="93b2f-117">Kullanıcı tarafından başlatılan e-posta yazışmaları dışında PowerShell Galerisi bir hesabı oluşturmadığınızı kullanıcılar kişisel verilerini depolamaz.</span><span class="sxs-lookup"><span data-stu-id="93b2f-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="93b2f-118">PowerShell Galerisi hesabı oluşturan kullanıcılar öğeleri PowerShell Galerisi'nde yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93b2f-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="93b2f-119">Bu öğeleri PowerShell kodu olması bekleniyor, ancak kişisel bilgiler dahil olmak üzere diğer bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="93b2f-120">Tüm öğeleri nasıl alabileceğiniz aşağıdaki bilgileri gösterir PowerShell Galerisi'nden yayımlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="93b2f-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="93b2f-121">PowerShell Galerisi verileri DSR dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="93b2f-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="93b2f-122">Aşağıdaki bölümlerde PowerShell Galerisi'nde bilgi dışarı aktarma ve silme, bu bilgilerin nasıl açıklayarak PowerShell Galerisi gdpr veri sahibi istekleri (DSR) nasıl desteklediği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93b2f-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="93b2f-123">E-posta</span><span class="sxs-lookup"><span data-stu-id="93b2f-123">Email</span></span>

<span data-ttu-id="93b2f-124">E-posta yazışmaları aşağıdakilerden herhangi birini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="93b2f-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="93b2f-125">Kod Analizi tarar, öğeler PowerShell Galerisi'nde yayımlanmış herhangi bir öğe ile ilgili bir sorun algıladı PowerShell Galerisi sahiplerine gönderilen e-posta</span><span class="sxs-lookup"><span data-stu-id="93b2f-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="93b2f-126">Hiç kimse tarafından "Bize başvurun" sayfasında e-posta adresini kullanarak PowerShell Galerisi ekibine gönderilen e-posta [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="93b2f-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="93b2f-127">PowerShell galerisinde bir öğenin sahibi e-posta göndermek için PowerShell galerisinde "Kişi sahip" özelliğini kullanan kullanıcılar kayıtlı</span><span class="sxs-lookup"><span data-stu-id="93b2f-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="93b2f-128">PowerShell Galerisi veya tarafından gönderilen e-postaları, olası güvenlik araştırmalar kötü amaçlı kod PowerShell galerisinde bulunmasına desteklemek için 90 günlük bir bekletme ilkesi olması.</span><span class="sxs-lookup"><span data-stu-id="93b2f-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="93b2f-129">E-posta İlkesi tarafından 90 gün sonra silinir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="93b2f-130">Gelen e-posta adresinizi ve PowerShell Galerisi veya önceki 90 gün içinde gönderilen tüm e-posta kopyalarını isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="93b2f-131">Bu yazışma istemek için bir e-posta Gönder [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), başlıklı: "Bu hesaba ilişkin e-postalar için DSR istek".</span><span class="sxs-lookup"><span data-stu-id="93b2f-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="93b2f-132">Hangi bilgilerin istiyorsunuz iletisinin gövdesinde, durum (örneğin: Lütfen bu e-posta adresinden alınan veya gönderilen tüm e-posta gönderin.) 7 iş günü içinde e-posta adresinizi isteğin 90 gün içinde ilgili tüm e-postalar gönderilir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="93b2f-133">PowerShell Galerisi hesap bilgileri</span><span class="sxs-lookup"><span data-stu-id="93b2f-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="93b2f-134">PowerShell Galerisi hesabı oluşturduysanız, PowerShell Galerisi'nde aşağıdaki adımları izleyerek daha fazladır saklanan tüm kişisel bilgileri bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="93b2f-135">PowerShell Galerisi için oturum açın, sonra kullanıcı adınıza tıklayın</span><span class="sxs-lookup"><span data-stu-id="93b2f-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="93b2f-136">Sonraki sayfada görüntülenen gösterir PowerShell Galerisi hesabı için kullanılan e-posta adresine hesap sayfası olan</span><span class="sxs-lookup"><span data-stu-id="93b2f-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="93b2f-137">PowerShell galerisinde birden fazla hesabı oluşturduysanız, her hesap için bu adımları yinelemeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="93b2f-138">PowerShell galeride bulunan öğeler</span><span class="sxs-lookup"><span data-stu-id="93b2f-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="93b2f-139">Dışarı aktarılan öğeleri PowerShell Galerisi'nde yayımlanmış kolaylaştırmak için "GetPSGalleryItemsForAuthor" betik PowerShell Galerisi'nde yayımladık.</span><span class="sxs-lookup"><span data-stu-id="93b2f-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="93b2f-140">Bu betik, her öğesinde depolanan Yazar bilgileri temel alarak PowerShell Galerisi yerleştirerek her öğe sürümünün bir kopyasını dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="93b2f-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="93b2f-141">Öğenizi yayımladığınızda Yazar öğesi bildiriminde saklanır.</span><span class="sxs-lookup"><span data-stu-id="93b2f-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="93b2f-142">Yazar PowerShell Galerisi'nde kullandığınız hesap aynı kimliğe olduğunu garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="93b2f-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="93b2f-143">Yazar alanı başka bir değer kullanıyorsanız, bu komut dosyası kullanırken bu değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="93b2f-144">Aşağıdaki PowerShell komutunu kullanarak betiği yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="93b2f-145">Betik aşağıdaki PowerShell komutlarını çalıştırarak, doğrudan, ardından çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="93b2f-146">Yazar ve kaydedilmesi için öğeleri istediğiniz klasör sisteminize sağlamanız istenir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="93b2f-147">PowerShell Galerisi'nden kişisel verileri silme</span><span class="sxs-lookup"><span data-stu-id="93b2f-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="93b2f-148">PowerShell Galerisi hesabınız veya PowerShell Galerisi'nde olduğunuz herhangi bir öğeyi silmek için e-posta Gönder cgadmin@microsoft.com başlığıyla: "Bu hesaba ilişkin öğeleri için GDPR isteği".</span><span class="sxs-lookup"><span data-stu-id="93b2f-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="93b2f-149">Hangi bilgilerin, silinen istediğiniz iletisinin gövdesindeki durumu.</span><span class="sxs-lookup"><span data-stu-id="93b2f-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="93b2f-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="93b2f-150">For example:</span></span>

- <span data-ttu-id="93b2f-151">Lütfen "öğe adı" my öğesinin sürümü x.y.z silin</span><span class="sxs-lookup"><span data-stu-id="93b2f-151">Please delete version x.y.z of my item "item name"</span></span>
- <span data-ttu-id="93b2f-152">Lütfen "öğe adı" öğe tüm sürümleri sil</span><span class="sxs-lookup"><span data-stu-id="93b2f-152">Please delete all versions of my item "item name"</span></span>
- <span data-ttu-id="93b2f-153">Lütfen PowerShell Galerisi Hesabımı silin</span><span class="sxs-lookup"><span data-stu-id="93b2f-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="93b2f-154">PowerShell Galerisi Yöneticiler 7 iş günü içinde yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="93b2f-155">Belirtilen öğelerin istek gönderildikten sonra 30 gün içinde silinecek.</span><span class="sxs-lookup"><span data-stu-id="93b2f-155">The items specified will be deleted within 30 days after the request is sent.</span></span>