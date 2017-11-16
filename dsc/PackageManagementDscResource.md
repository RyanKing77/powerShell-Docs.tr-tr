---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC PackageManagement kaynağı"
ms.openlocfilehash: a984fbf5db561a696d89b60dde8b92096c6e4924
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="c6161-103">DSC PackageManagement kaynağı</span><span class="sxs-lookup"><span data-stu-id="c6161-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="c6161-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c6161-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c6161-105">**PackageManagement** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) yüklemek veya bir hedef düğüm üzerinde paket Yönetimi paketleri kaldırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6161-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="c6161-106">Bu kaynak için gerekli **PackageManagement** modülü, http://PowerShellGallery.com kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6161-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6161-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6161-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="c6161-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c6161-108">Properties</span></span>
|  <span data-ttu-id="c6161-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="c6161-109">Property</span></span>  |  <span data-ttu-id="c6161-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6161-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="c6161-111">Ad</span><span class="sxs-lookup"><span data-stu-id="c6161-111">Name</span></span>| <span data-ttu-id="c6161-112">Yüklenecek veya için paket adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="c6161-113">Kaynak</span><span class="sxs-lookup"><span data-stu-id="c6161-113">Source</span></span>| <span data-ttu-id="c6161-114">Paket bulunabileceği paket kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="c6161-115">Bu bir URI olabilir veya bir kaynak kaydı PackageSource veya PackageManagementSource DSC kaynağı ile kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="c6161-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="c6161-116">DSC kaynağı MSFT_PackageManagementSource bir paket kaynağı da kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6161-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="c6161-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="c6161-117">Ensure</span></span>| <span data-ttu-id="c6161-118">Paketin yüklü veya kaldırılmış olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c6161-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="c6161-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c6161-119">RequiredVersion</span></span>| <span data-ttu-id="c6161-120">Yüklemek istediğiniz paketi'nün tam sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="c6161-121">Bu parametre belirtmezseniz, bu DSC kaynağı MaximumVersion parametresi tarafından belirtilen herhangi bir en fazla sürümünü de karşılayan paketin kullanılabilir en yeni sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="c6161-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="c6161-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c6161-122">MinimumVersion</span></span>| <span data-ttu-id="c6161-123">Yüklemek istediğiniz paketinin sürümünü, izin verilen en düşük belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="c6161-124">Bu parametreyi eklemezseniz, bu DSC kaynağı intalls yüksek kullanılabilir paketinin sürümünü, herhangi bir maksimum belirtilen sürümünü de karşılayan MaximumVersion parametresi tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c6161-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="c6161-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c6161-125">MaximumVersion</span></span>| <span data-ttu-id="c6161-126">Yüklemek istediğiniz paketinin sürümünü, izin verilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="c6161-127">Bu parametre belirtmezseniz, bu DSC kaynağı en yüksek numaralı kullanılabilir paketin sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="c6161-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="c6161-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="c6161-128">SourceCredential</span></span> | <span data-ttu-id="c6161-129">Belirtilen paket sağlayıcısı veya kaynak için bir paketi yüklemek için haklarına sahip bir kullanıcı hesabı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="c6161-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="c6161-130">ProviderName</span></span>| <span data-ttu-id="c6161-131">Paket arama kapsamınızı kurmak için bir paket sağlayıcının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="c6161-132">Get-PackageProvider cmdlet'ini çalıştırarak paket sağlayıcı adları elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6161-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="c6161-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="c6161-133">AdditionalParameters</span></span>| <span data-ttu-id="c6161-134">Bir karma tablosu olarak geçirilen belirli parametreleri sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="c6161-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="c6161-135">Örneğin, NuGet sağlayıcısı HedefYolu gibi ek parametreleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6161-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="c6161-136">Ek parametreler</span><span class="sxs-lookup"><span data-stu-id="c6161-136">Additional Parameters</span></span>
<span data-ttu-id="c6161-137">Aşağıdaki tabloda AdditionalParameters özelliği için seçenekleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c6161-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="c6161-138">Parametre</span><span class="sxs-lookup"><span data-stu-id="c6161-138">Parameter</span></span>  | <span data-ttu-id="c6161-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6161-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="c6161-140">HedefYolu</span><span class="sxs-lookup"><span data-stu-id="c6161-140">DestinationPath</span></span>| <span data-ttu-id="c6161-141">Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6161-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="c6161-142">Yüklenecek paket istediğiniz bir dosya konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6161-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="c6161-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="c6161-143">InstallationPolicy</span></span>| <span data-ttu-id="c6161-144">Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6161-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="c6161-145">Paket kaynağına güveniyorsanız olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c6161-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="c6161-146">Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".</span><span class="sxs-lookup"><span data-stu-id="c6161-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="c6161-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6161-147">Example</span></span>

<span data-ttu-id="c6161-148">Bu örnek yükler **JQuery** NuGet paketi ve **GistProvider** PowerShell modülünü kullanarak **PackageManagement** DSC kaynağı.</span><span class="sxs-lookup"><span data-stu-id="c6161-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="c6161-149">Bu örnek ilk gerekli paket kaynaklarını kullanılabilir sonra beklenen durumunu tanımlar sağlar **JQuery** ve **GistProvider** paketleri (NuGet ve PowerShell, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="c6161-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
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

