---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery
title: Elle Paket İndirme
ms.openlocfilehash: 0952aa4ec474850af5219fb2e0e9ee3e954b0f9a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004145"
---
# <a name="manual-package-download"></a><span data-ttu-id="8e702-103">Elle Paket İndirme</span><span class="sxs-lookup"><span data-stu-id="8e702-103">Manual Package Download</span></span>

<span data-ttu-id="8e702-104">Powershell Galerisi PowerShellGet cmdlet'leri kullanmadan, doğrudan Web sitesinden bir paket indiriliyor destekler.</span><span class="sxs-lookup"><span data-stu-id="8e702-104">The Powershell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="8e702-105">Paket, daha sonra kolayca iç bir depoya kopyalanabilir bir NuGet paketi (.nupkg) dosyası olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="8e702-105">The package will be downloaded as a NuGet package (.nupkg) file, which can then be easily copied to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="8e702-106">El ile paket **değil** Install-Module cmdlet'i bir ardılı olarak yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8e702-106">Manual package download is **not** intended as a replacement for the Install-Module cmdlet.</span></span>
> <span data-ttu-id="8e702-107">Paket indiriliyor modül veya komut dosyası yüklemez.</span><span class="sxs-lookup"><span data-stu-id="8e702-107">Downloading the package does not install the module or script.</span></span> <span data-ttu-id="8e702-108">NuGet paketinin indirilen bağımlılıklar dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="8e702-108">Dependencies are not included in the NuGet package downloaded.</span></span> <span data-ttu-id="8e702-109">Aşağıdaki yönergeler, yalnızca başvuru amacıyla verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8e702-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="8e702-110">Bir paket almak için el ile yükleme kullanma</span><span class="sxs-lookup"><span data-stu-id="8e702-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="8e702-111">Her sayfanın bağlantısını el ile indirmek için burada gösterildiği gibi sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8e702-111">Each page has a link for Manual Download, as shown here:</span></span>

![El ile yükleme](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="8e702-113">El ile yüklemek için tıklayın **ham nupkg dosya indirme**.</span><span class="sxs-lookup"><span data-stu-id="8e702-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="8e702-114">Paketinin bir kopyasını kopyalar indirme klasörü için tarayıcınızı adıyla `<name>.<version>.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="8e702-114">A copy of the package copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="8e702-115">Ek dosyaları paket içeriği hakkında bilgi içeren bir ZIP arşivi NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="8e702-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="8e702-116">Internet Explorer gibi bazı tarayıcılar otomatik değiştirme `.nupkg` dosya uzantısıyla `.zip`.</span><span class="sxs-lookup"><span data-stu-id="8e702-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="8e702-117">Paket genişletmek için yeniden adlandırma `.nupkg` dosyasını `.zip`, gerekli, içeriği yerel bir klasöre ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="8e702-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="8e702-118">NuGet paket dosyası, özgün paketli kod parçası olmayan aşağıdaki NuGet özgü öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e702-118">A NuGet package file includes the following NuGet-specific elements that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="8e702-119">Adlı bir klasör `_rels` -içeren bir `.rels` bağımlılıkları listeler dosyası</span><span class="sxs-lookup"><span data-stu-id="8e702-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="8e702-120">Adlı bir klasör `package` -NuGet özgü verileri içerir</span><span class="sxs-lookup"><span data-stu-id="8e702-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="8e702-121">Adlı bir dosya `[Content_Types].xml` -PowerShellGet gibi uzantısı NuGet ile nasıl çalıştığı açıklanır</span><span class="sxs-lookup"><span data-stu-id="8e702-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="8e702-122">Adlı bir dosya `<name>.nuspec` -meta verilerin toplu içerir</span><span class="sxs-lookup"><span data-stu-id="8e702-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="8e702-123">Bir NuGet paketinden PowerShell modüllerini yükleme</span><span class="sxs-lookup"><span data-stu-id="8e702-123">Installing PowerShell Modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="8e702-124">Bu yönergeler **yok** çalışan aynı sonucu verir `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="8e702-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="8e702-125">Bu yönergeler, en düşük gereksinimleri karşılamak.</span><span class="sxs-lookup"><span data-stu-id="8e702-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="8e702-126">Bir ardılı olarak amaçlanmamıştır `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="8e702-126">They are not intended to be a replacement for `Install-Module`.</span></span> <span data-ttu-id="8e702-127">Tarafından gerçekleştirilen bazı adımlar `Install-Module` dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="8e702-127">Some steps performed by `Install-Module` are not included.</span></span>

<span data-ttu-id="8e702-128">En kolay yaklaşım, NuGet özgü öğeleri klasöründen kaldırmaktır.</span><span class="sxs-lookup"><span data-stu-id="8e702-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="8e702-129">Bu paketi yazarı tarafından oluşturulan PowerShell kodu bırakır.</span><span class="sxs-lookup"><span data-stu-id="8e702-129">This leaves the PowerShell code created by the package author.</span></span> <span data-ttu-id="8e702-130">Adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8e702-130">The steps are:</span></span>

1. <span data-ttu-id="8e702-131">Yerel bir klasöre NuGet paketinin içeriğini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="8e702-131">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="8e702-132">NuGet özgü öğeleri klasöründen silin.</span><span class="sxs-lookup"><span data-stu-id="8e702-132">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="8e702-133">Klasörünü yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="8e702-133">Rename the folder.</span></span> <span data-ttu-id="8e702-134">Varsayılan klasör adı genellikle olan `<name>.<version>`.</span><span class="sxs-lookup"><span data-stu-id="8e702-134">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="8e702-135">Sürüm içerebilir "-yayın öncesi" modül yayım öncesi bir sürümü etiketlenmiş olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="8e702-135">The version can include "-prerelease" if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="8e702-136">Klasörü yeniden adlandırmak için yalnızca modül adı.</span><span class="sxs-lookup"><span data-stu-id="8e702-136">Rename the folder to just the module name.</span></span> <span data-ttu-id="8e702-137">Örneğin, "azurerm.storage.5.0.4-preview", "azurerm.storage" haline gelir.</span><span class="sxs-lookup"><span data-stu-id="8e702-137">For example, "azurerm.storage.5.0.4-preview" becomes "azurerm.storage".</span></span>
4. <span data-ttu-id="8e702-138">Klasör için PSModulePath kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="8e702-138">Copy the folder to your PSModulePath.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e702-139">El ile yükleme modülü tarafından gerekli herhangi bir bağımlılığın içermez.</span><span class="sxs-lookup"><span data-stu-id="8e702-139">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="8e702-140">Paket bağımlılıkları varsa, sistemde düzgün çalışması için bu modülü yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e702-140">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="8e702-141">PowerShell Galerisi, paket için gerekli tüm bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e702-141">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="8e702-142">PowerShell betiklerini bir NuGet paketi yükleniyor</span><span class="sxs-lookup"><span data-stu-id="8e702-142">Installing PowerShell Scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="8e702-143">Bu yönergeler **yok** çalışan aynı sonucu verir `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="8e702-143">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="8e702-144">Bu yönergeler, en düşük gereksinimleri karşılamak.</span><span class="sxs-lookup"><span data-stu-id="8e702-144">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="8e702-145">Bir ardılı olarak amaçlanmamıştır `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="8e702-145">They are not intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="8e702-146">Kolay ayıklama NuGet paketini ve ardından betiği doğrudan bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="8e702-146">The easiest approach is to extract the NuGet package, then use the script directly.</span></span> <span data-ttu-id="8e702-147">Adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8e702-147">The steps are:</span></span>

1. <span data-ttu-id="8e702-148">NuGet paketinin içeriğini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="8e702-148">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="8e702-149">`.PS1` Klasöründeki dosyasını bu konumdan doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e702-149">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="8e702-150">NuGet özgü öğeleri klasörü silebilir.</span><span class="sxs-lookup"><span data-stu-id="8e702-150">You may delete the NuGet-specific elements in the folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e702-151">El ile yükleme modülü tarafından gerekli herhangi bir bağımlılığın içermez.</span><span class="sxs-lookup"><span data-stu-id="8e702-151">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="8e702-152">Paket bağımlılıkları varsa, sistemde düzgün çalışması için bu modülü yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e702-152">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="8e702-153">PowerShell Galerisi, paket için gerekli tüm bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e702-153">The PowerShell Gallery shows all dependencies required by the package.</span></span>
