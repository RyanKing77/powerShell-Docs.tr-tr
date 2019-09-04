---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, PowerShell, psgallery
title: Elle Paket İndirme
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215449"
---
# <a name="manual-package-download"></a><span data-ttu-id="18772-103">Elle Paket İndirme</span><span class="sxs-lookup"><span data-stu-id="18772-103">Manual Package Download</span></span>

<span data-ttu-id="18772-104">PowerShell Galerisi, PowerShellGet cmdlet 'leri kullanılmadan doğrudan Web sitesinden bir paketin indirilmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="18772-104">The PowerShell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="18772-105">Herhangi bir paketi, bir NuGet paketi (`.nupkg`) dosyası olarak indirebilir ve ardından bir iç depoya kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18772-105">You can download any package as a NuGet package (`.nupkg`) file, which you can then copy to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="18772-106">El ile paket `Install-Module` indirme **, cmdlet** 'in yerini alacak şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="18772-106">Manual package download is **not** intended as a replacement for the `Install-Module` cmdlet.</span></span>
> <span data-ttu-id="18772-107">Paketin indirilmesi modül veya betiği yüklemez.</span><span class="sxs-lookup"><span data-stu-id="18772-107">Downloading the package doesn't install the module or script.</span></span> <span data-ttu-id="18772-108">Bağımlılıklar, indirilen NuGet paketine dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="18772-108">Dependencies aren't included in the NuGet package downloaded.</span></span> <span data-ttu-id="18772-109">Aşağıdaki yönergeler yalnızca başvuru amaçları için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="18772-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="18772-110">Paket almak için el ile indirme kullanma</span><span class="sxs-lookup"><span data-stu-id="18772-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="18772-111">Her sayfada, burada gösterildiği gibi el Ile Indirme bağlantısı bulunur:</span><span class="sxs-lookup"><span data-stu-id="18772-111">Each page has a link for Manual Download, as shown here:</span></span>

![El ile Indir](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="18772-113">El ile indirmek için **Ham nupkg dosyasını indir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="18772-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="18772-114">Paketin bir kopyası, tarayıcınızla `<name>.<version>.nupkg`ilgili indirme klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="18772-114">A copy of the package is copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="18772-115">NuGet paketi, paketin içeriğiyle ilgili bilgiler içeren ek dosyalar içeren bir ZIP arşividir.</span><span class="sxs-lookup"><span data-stu-id="18772-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="18772-116">Internet Explorer gibi bazı tarayıcılar `.nupkg` dosya uzantısını ile `.zip`otomatik olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="18772-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="18772-117">Paketi genişletmek için, gerekirse `.nupkg` dosyayı olarak `.zip`yeniden adlandırın ve ardından içeriği yerel bir klasöre ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="18772-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="18772-118">NuGet paket dosyası orijinal paketlenmiş kodun parçası olmayan aşağıdaki **NuGet 'e özgü öğeleri** içerir:</span><span class="sxs-lookup"><span data-stu-id="18772-118">A NuGet package file includes the following **NuGet-specific elements** that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="18772-119">Adlı `_rels` bir klasör, bağımlılıkları listeleyen `.rels` bir dosya içerir</span><span class="sxs-lookup"><span data-stu-id="18772-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="18772-120">Adlı `package` bir klasör, NuGet 'e özgü verileri içerir</span><span class="sxs-lookup"><span data-stu-id="18772-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="18772-121">Adlı `[Content_Types].xml` bir dosya-PowerShellGet gibi uzantıların NuGet ile nasıl çalıştığını açıklar</span><span class="sxs-lookup"><span data-stu-id="18772-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="18772-122">Adlı `<name>.nuspec` bir dosya, meta verilerin toplu içeriğini içerir</span><span class="sxs-lookup"><span data-stu-id="18772-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="18772-123">NuGet paketinden PowerShell modülleri yükleme</span><span class="sxs-lookup"><span data-stu-id="18772-123">Installing PowerShell modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="18772-124">Bu yönergeler **,** çalıştırmaya `Install-Module`aynı sonucu vermez.</span><span class="sxs-lookup"><span data-stu-id="18772-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="18772-125">Bu yönergeler en düşük gereksinimleri karşılar.</span><span class="sxs-lookup"><span data-stu-id="18772-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="18772-126">Bunların yerini alacak `Install-Module`şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="18772-126">They aren't intended to be a replacement for `Install-Module`.</span></span>
> <span data-ttu-id="18772-127">Tarafından `Install-Module` gerçekleştirilen bazı adımlar dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="18772-127">Some steps performed by `Install-Module` aren't included.</span></span>

<span data-ttu-id="18772-128">En kolay yaklaşım, NuGet 'e özgü öğeleri klasöründen kaldırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18772-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="18772-129">Öğeleri kaldırmak, paket yazarı tarafından oluşturulan PowerShell kodundan çıkar.</span><span class="sxs-lookup"><span data-stu-id="18772-129">Removing the elements leaves the PowerShell code created by the package author.</span></span>
<span data-ttu-id="18772-130">NuGet 'e özgü öğelerin listesi için bkz. [paket edinmek için el ile Indirme kullanma](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="18772-130">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

<span data-ttu-id="18772-131">Adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="18772-131">The steps are as follows:</span></span>

1. <span data-ttu-id="18772-132">NuGet paketinin içeriğini yerel bir klasöre ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="18772-132">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="18772-133">NuGet 'e özgü öğeleri klasörden silin.</span><span class="sxs-lookup"><span data-stu-id="18772-133">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="18772-134">Klasörü yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="18772-134">Rename the folder.</span></span> <span data-ttu-id="18772-135">Varsayılan klasör adı genellikle `<name>.<version>`olur.</span><span class="sxs-lookup"><span data-stu-id="18772-135">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="18772-136">Modül bir ön sürüm `-prerelease` sürümü olarak etiketlenmişse, bu sürüm dahil olabilir.</span><span class="sxs-lookup"><span data-stu-id="18772-136">The version can include `-prerelease` if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="18772-137">Klasörü yalnızca modül adıyla yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="18772-137">Rename the folder to just the module name.</span></span> <span data-ttu-id="18772-138">Örneğin, `azurerm.storage.5.0.4-preview` olur `azurerm.storage`.</span><span class="sxs-lookup"><span data-stu-id="18772-138">For example, `azurerm.storage.5.0.4-preview` becomes `azurerm.storage`.</span></span>
4. <span data-ttu-id="18772-139">Klasörünü içindeki `$env:PSModulePath value`klasörlerden birine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="18772-139">Copy the folder to one of the folders in the `$env:PSModulePath value`.</span></span> <span data-ttu-id="18772-140">`$env:PSModulePath`, PowerShell 'in modülleri arayacağı bir noktalı virgülle ayrılmış yol kümesidir.</span><span class="sxs-lookup"><span data-stu-id="18772-140">`$env:PSModulePath` is a semicolon-delimited set of paths in which PowerShell should look for modules.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18772-141">El ile indirme, modülün gerektirdiği hiçbir bağımlılığı içermez.</span><span class="sxs-lookup"><span data-stu-id="18772-141">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="18772-142">Pakette bağımlılıklar varsa, Bu modülün düzgün çalışması için sistemde yüklü olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="18772-142">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="18772-143">PowerShell Galerisi, paket için gereken tüm bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="18772-143">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="18772-144">NuGet paketinden PowerShell betikleri yükleme</span><span class="sxs-lookup"><span data-stu-id="18772-144">Installing PowerShell scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="18772-145">Bu yönergeler **,** çalıştırmaya `Install-Script`aynı sonucu vermez.</span><span class="sxs-lookup"><span data-stu-id="18772-145">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="18772-146">Bu yönergeler en düşük gereksinimleri karşılar.</span><span class="sxs-lookup"><span data-stu-id="18772-146">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="18772-147">Bunların yerini alacak `Install-Script`şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="18772-147">They aren't intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="18772-148">En kolay yaklaşım, NuGet paketini ayıklamanın ardından betiği doğrudan kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="18772-148">The easiest approach is to extract the NuGet package, then use the script directly.</span></span>

<span data-ttu-id="18772-149">Adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="18772-149">The steps are as follows:</span></span>

1. <span data-ttu-id="18772-150">NuGet paketinin içeriğini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="18772-150">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="18772-151">Klasördeki `.PS1` dosya doğrudan bu konumdan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18772-151">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="18772-152">Klasördeki NuGet 'e özgü öğeleri silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18772-152">You may delete the NuGet-specific elements in the folder.</span></span>

<span data-ttu-id="18772-153">NuGet 'e özgü öğelerin listesi için bkz. [paket edinmek için el ile Indirme kullanma](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="18772-153">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18772-154">El ile indirme, modülün gerektirdiği hiçbir bağımlılığı içermez.</span><span class="sxs-lookup"><span data-stu-id="18772-154">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="18772-155">Pakette bağımlılıklar varsa, Bu modülün düzgün çalışması için sistemde yüklü olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="18772-155">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="18772-156">PowerShell Galerisi, paket için gereken tüm bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="18772-156">The PowerShell Gallery shows all dependencies required by the package.</span></span>
