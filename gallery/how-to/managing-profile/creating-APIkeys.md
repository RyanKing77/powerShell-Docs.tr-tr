---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: API anahtarları yönetme
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002522"
---
# <a name="managing-api-keys"></a><span data-ttu-id="f69c6-103">API anahtarları yönetme</span><span class="sxs-lookup"><span data-stu-id="f69c6-103">Managing API keys</span></span>

<span data-ttu-id="f69c6-104">PowerShell Galerisi gereksinimleri yayımlama aralığı desteklemek için birden çok API anahtarı oluşturma destekler.</span><span class="sxs-lookup"><span data-stu-id="f69c6-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="f69c6-105">Bir API anahtarı için bir veya daha fazla paket uygulayabilirsiniz, belirli ayrıcalıklar verir ve bir sona erme tarihi vardır.</span><span class="sxs-lookup"><span data-stu-id="f69c6-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f69c6-106">Kapsamı belirlenmiş bir API anahtarı giriş önce PowerShell Galerisi yayımlanan kullanıcılar, "tam erişim API anahtarı" gerekir.</span><span class="sxs-lookup"><span data-stu-id="f69c6-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="f69c6-107">Tam erişim anahtarlarını kapsamlı API anahtarlarına yerleşik güvenlik geliştirmeleri yok.</span><span class="sxs-lookup"><span data-stu-id="f69c6-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="f69c6-108">Tam erişim anahtarları asla süresi dolar ve kullanıcı tarafından sahip olunan her şeye uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f69c6-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="f69c6-109">Bu anahtarı silmek, yeniden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f69c6-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="f69c6-110">Aşağıdaki görüntüde, kapsamlı bir API anahtarı oluştururken kullanılabilen seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f69c6-110">The following image shows the options available when creating a scoped API key.</span></span>

![API anahtarları oluşturma](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="f69c6-112">Bu örnekte, oluşturduğumuz adlı bir API anahtarı **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="f69c6-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="f69c6-113">Bu anahtar değeri 'AzureRM.DataFactory' ile başlayan ve 365 gün boyunca geçerlidir adlarla paketleri göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f69c6-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="f69c6-114">Aynı kuruluştaki farklı ekipler farklı paketleri çalışırken tipik bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="f69c6-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="f69c6-115">Takım üyeleri, üzerinde çalıştıkları belirli bir paket için ayrıcalıkları verir bir anahtara sahip.</span><span class="sxs-lookup"><span data-stu-id="f69c6-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="f69c6-116">Süre sonu değeri eski veya unutulan anahtarları kullanımını engeller.</span><span class="sxs-lookup"><span data-stu-id="f69c6-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="f69c6-117">Glob desenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="f69c6-117">Using glob patterns</span></span>

<span data-ttu-id="f69c6-118">Birden çok paket üzerinde çalışıyorsanız, birden çok paket grubu olarak eşleşecek şekilde Glob desenlerinin kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f69c6-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="f69c6-119">API anahtarı izinleri glob deseni ile eşleşen tüm yeni paketleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f69c6-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="f69c6-120">Örneğin, önceki örnekte bir **Glob deseni** 'AzureRM.DataFactory\*' değeri.</span><span class="sxs-lookup"><span data-stu-id="f69c6-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="f69c6-121">'Paket glob deseni eşleştiğinden bu anahtarı kullanarak AzureRm.DataFactoryV2.Netcore' adlı bir paket gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f69c6-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="f69c6-122">API anahtarları güvenli bir şekilde oluşturun</span><span class="sxs-lookup"><span data-stu-id="f69c6-122">Create API keys securely</span></span>

<span data-ttu-id="f69c6-123">Güvenlik için yeni oluşturulan bir anahtar değeri ekranda asla gösterilir ve yalnızca aşağıda gösterilen şekilde Kopyala düğmesini ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f69c6-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Yeni API anahtarı değerini alma](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="f69c6-125">API anahtarı değerini yalnızca, hemen oluşturma veya yenilediğinizden sonra da kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f69c6-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="f69c6-126">Görüntülenmeyecek ve sayfa yenilendikten sonra yeniden erişilemez.</span><span class="sxs-lookup"><span data-stu-id="f69c6-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="f69c6-127">Anahtar değeri kaybederseniz yeniden kullanın ve yeniden oluşturuldu sonra anahtarı kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f69c6-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="f69c6-128">Anahtar izinleri ve sona erme tarihi</span><span class="sxs-lookup"><span data-stu-id="f69c6-128">Key permissions and expiration</span></span>

<span data-ttu-id="f69c6-129">Kapsamlı API anahtarları, aşağıdaki izinlerden birini atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f69c6-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="f69c6-130">Yeni paketleri gönder</span><span class="sxs-lookup"><span data-stu-id="f69c6-130">Push new packages</span></span>
- <span data-ttu-id="f69c6-131">Güncelleştirme paketleri veya New bildirme</span><span class="sxs-lookup"><span data-stu-id="f69c6-131">Push new or update packages</span></span>
- <span data-ttu-id="f69c6-132">Paket listeden Kaldır</span><span class="sxs-lookup"><span data-stu-id="f69c6-132">Unlist packages</span></span>

<span data-ttu-id="f69c6-133">Her yeni anahtarı bir zaman aşımı vardır.</span><span class="sxs-lookup"><span data-stu-id="f69c6-133">Every new key has an expiration.</span></span> <span data-ttu-id="f69c6-134">Süre sonu değeri, gün içinde ölçülür.</span><span class="sxs-lookup"><span data-stu-id="f69c6-134">The expiration value is measured in days.</span></span> <span data-ttu-id="f69c6-135">Süre sonu için olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f69c6-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="f69c6-136">1 gün</span><span class="sxs-lookup"><span data-stu-id="f69c6-136">1 day</span></span>
- <span data-ttu-id="f69c6-137">90 gün</span><span class="sxs-lookup"><span data-stu-id="f69c6-137">90 days</span></span>
- <span data-ttu-id="f69c6-138">180 gün</span><span class="sxs-lookup"><span data-stu-id="f69c6-138">180 days</span></span>
- <span data-ttu-id="f69c6-139">270 günde bir</span><span class="sxs-lookup"><span data-stu-id="f69c6-139">270 days</span></span>
- <span data-ttu-id="f69c6-140">365 gün (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="f69c6-140">365 days (default)</span></span>

<span data-ttu-id="f69c6-141">Anahtar oluşturulduktan sonra bu ayarlar değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f69c6-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="f69c6-142">Her zaman geçerli olsun yeni bir anahtar oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="f69c6-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="f69c6-143">Düzenleme ve mevcut API anahtarları silme</span><span class="sxs-lookup"><span data-stu-id="f69c6-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="f69c6-144">Varolan bir anahtarın bazı ayarları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f69c6-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="f69c6-145">Daha önce belirtildiği gibi mevcut bir API anahtarı için güvenlik kapsamı değiştiremez veya sona erme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f69c6-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="f69c6-146">Takımdaki herhangi biri seçeneği, aşağıdaki ekran görüntüsünde gösterilir:</span><span class="sxs-lookup"><span data-stu-id="f69c6-146">The changeable options are shown in the following screenshot:</span></span>

![Yeni API anahtarı değerini alma](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="f69c6-148">Bir anahtar tarafından denetlenen paketlerini değiştirmek için tek paketler listesinden seçim yapabilir veya glob deseni değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="f69c6-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="f69c6-149">Tıklayarak **yeniden** yeni bir anahtar değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f69c6-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="f69c6-150">Yalnızca anahtar ilk oluşturulduğunda gerekir gibi **kopyalama** güncelleştirmeden hemen sonra anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="f69c6-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="f69c6-151">**Kopyalama** seçeneği kullanılamaz bu sayfadan çıktıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="f69c6-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="f69c6-152">Tıklayarak **Sil** bir onay iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f69c6-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="f69c6-153">Bir anahtar silindikten sonra kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f69c6-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="f69c6-154">Anahtarı süre sonu</span><span class="sxs-lookup"><span data-stu-id="f69c6-154">Key expiration</span></span>

<span data-ttu-id="f69c6-155">On gün süresi dolmadan önce PowerShell Galerisi API anahtarını hesap sahibi uyarı e-posta gönderir.</span><span class="sxs-lookup"><span data-stu-id="f69c6-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="f69c6-156">Süre dolduktan sonra anahtarı kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f69c6-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="f69c6-157">Hangi anahtar artık geçerli olmayan gösteren API Anahtar Yönetimi sayfasının en üstündeki bir uyarı iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f69c6-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="f69c6-158">Yeni bir anahtar değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f69c6-158">You can generate a new key value.</span></span>
