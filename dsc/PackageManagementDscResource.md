---
ms.date: 06/20/2018
keywords: DSC, powershell, yapılandırma, Kur
title: DSC PackageManagement kaynağı
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753796"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="622a1-103">DSC PackageManagement kaynağı</span><span class="sxs-lookup"><span data-stu-id="622a1-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="622a1-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="622a1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="622a1-105">**PackageManagement** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) yüklemek veya bir hedef düğüm üzerinde paket Yönetimi paketleri kaldırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="622a1-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="622a1-106">Bu kaynak için gerekli **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="622a1-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="622a1-107">**PackageManagement** modülü en az olmalıdır sürüm 1.1.7.0 doğru olması aşağıdaki özellik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="622a1-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="622a1-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="622a1-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="622a1-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="622a1-109">Properties</span></span>

|  <span data-ttu-id="622a1-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="622a1-110">Property</span></span>  |  <span data-ttu-id="622a1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="622a1-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="622a1-112">Ad</span><span class="sxs-lookup"><span data-stu-id="622a1-112">Name</span></span>| <span data-ttu-id="622a1-113">Yüklenecek veya için paket adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="622a1-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="622a1-114">AdditionalParameters</span></span>| <span data-ttu-id="622a1-115">Sağlayıcı belirli hashtable için aktarılabilecek parametrelerinin `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="622a1-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="622a1-116">Örneğin, NuGet sağlayıcısı HedefYolu gibi ek parametreleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="622a1-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="622a1-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="622a1-117">Ensure</span></span>| <span data-ttu-id="622a1-118">Paketin yüklü veya kaldırılmış olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="622a1-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="622a1-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="622a1-119">MaximumVersion</span></span>|<span data-ttu-id="622a1-120">Bulmak istediğiniz paketinin sürümünü, izin verilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="622a1-121">Bu parametreyi eklemezseniz, kaynak paketinin yüksek kullanılabilir sürümünü bulur.</span><span class="sxs-lookup"><span data-stu-id="622a1-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="622a1-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="622a1-122">MinimumVersion</span></span>|<span data-ttu-id="622a1-123">Bulmak istediğiniz paketinin sürümünü, izin verilen en düşük belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="622a1-124">Bu parametreyi eklemezseniz, yüksek kullanılabilir paketinin sürümünü, tarafından belirtilen tüm maksimum belirtilen sürüm de karşılayan kaynak bulan _MaximumVersion_ parametresi.</span><span class="sxs-lookup"><span data-stu-id="622a1-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="622a1-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="622a1-125">ProviderName</span></span>| <span data-ttu-id="622a1-126">Paket arama kapsamınızı kurmak için bir paket sağlayıcının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="622a1-127">Çalıştırarak paket sağlayıcı adları alabilirsiniz `Get-PackageProvider` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="622a1-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="622a1-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="622a1-128">RequiredVersion</span></span>| <span data-ttu-id="622a1-129">Yüklemek istediğiniz paketi'nün tam sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="622a1-130">Bu parametre belirtmezseniz, bu DSC kaynağı tarafından belirtilen herhangi bir en fazla sürümünü de karşılayan paketi kullanılabilir en yeni sürümünü yükler _MaximumVersion_ parametresi.</span><span class="sxs-lookup"><span data-stu-id="622a1-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="622a1-131">Kaynak</span><span class="sxs-lookup"><span data-stu-id="622a1-131">Source</span></span>| <span data-ttu-id="622a1-132">Paket bulunabileceği paket kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="622a1-133">Bu bir URI olabilir veya bir kaynak kayıtlı `Register-PackageSource` veya PackageManagementSource DSC kaynağı.</span><span class="sxs-lookup"><span data-stu-id="622a1-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="622a1-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="622a1-134">SourceCredential</span></span> | <span data-ttu-id="622a1-135">Belirtilen paket sağlayıcısı veya kaynak için bir paketi yüklemek için haklarına sahip bir kullanıcı hesabı belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="622a1-136">Ek parametreler</span><span class="sxs-lookup"><span data-stu-id="622a1-136">Additional Parameters</span></span>

<span data-ttu-id="622a1-137">Aşağıdaki tabloda AdditionalParameters özelliği için seçenekleri listeler.</span><span class="sxs-lookup"><span data-stu-id="622a1-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="622a1-138">Parametre</span><span class="sxs-lookup"><span data-stu-id="622a1-138">Parameter</span></span>  | <span data-ttu-id="622a1-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="622a1-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="622a1-140">HedefYolu</span><span class="sxs-lookup"><span data-stu-id="622a1-140">DestinationPath</span></span>| <span data-ttu-id="622a1-141">Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="622a1-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="622a1-142">Yüklenecek paket istediğiniz bir dosya konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="622a1-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="622a1-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="622a1-143">InstallationPolicy</span></span>| <span data-ttu-id="622a1-144">Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="622a1-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="622a1-145">Paket kaynağına güveniyorsanız olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="622a1-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="622a1-146">Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".</span><span class="sxs-lookup"><span data-stu-id="622a1-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="622a1-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="622a1-147">Example</span></span>

<span data-ttu-id="622a1-148">Bu örnek yükler **JQuery** NuGet paketi ve **GistProvider** PowerShell modülünü kullanarak **PackageManagement** DSC kaynağı.</span><span class="sxs-lookup"><span data-stu-id="622a1-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="622a1-149">Bu örnek ilk gerekli paket kaynaklarını kullanılabilir sonra beklenen durumunu tanımlar sağlar **JQuery** ve **GistProvider** paketleri (NuGet ve PowerShell, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="622a1-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```