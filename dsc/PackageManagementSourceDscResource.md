---
ms.date: 06/20/2018
keywords: DSC, powershell, yapılandırma, Kur
title: DSC PackageManagementSource kaynağı
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753779"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="e5770-103">DSC PackageManagementSource kaynağı</span><span class="sxs-lookup"><span data-stu-id="e5770-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="e5770-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5770-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="e5770-105">**PackageManagementSource** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) kaydetmek veya paket Yönetimi kaynakları bir hedef düğümdeki kaydı için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5770-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="e5770-106">**Bu şekilde kayıtlı paket Yönetimi kaynaklarını bağlamında sistem, sistem hesabı veya DSC altyapısı tarafından kullanılabilir kaydedilir.**</span><span class="sxs-lookup"><span data-stu-id="e5770-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="e5770-107">Bu kaynak için gerekli **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="e5770-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5770-108">**PackageManagement** modülü en az olmalıdır sürüm 1.1.7.0 doğru olması aşağıdaki özellik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e5770-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5770-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5770-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="e5770-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5770-110">Properties</span></span>

|  <span data-ttu-id="e5770-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="e5770-111">Property</span></span>  |  <span data-ttu-id="e5770-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5770-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="e5770-113">Ad</span><span class="sxs-lookup"><span data-stu-id="e5770-113">Name</span></span>| <span data-ttu-id="e5770-114">Kayıtlı veya sisteminizde kaydı için paket kaynağı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5770-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="e5770-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e5770-115">ProviderName</span></span>| <span data-ttu-id="e5770-116">Paket kaynağı ile birlikte çalışma ile yapabilecekleriniz OneGet sağlayıcının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5770-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="e5770-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="e5770-117">SourceLocation</span></span>| <span data-ttu-id="e5770-118">Paket kaynağının URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5770-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="e5770-119">Emin olun</span><span class="sxs-lookup"><span data-stu-id="e5770-119">Ensure</span></span>| <span data-ttu-id="e5770-120">Paket kaynağı kaydedildiğinde veya kaydı için olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e5770-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="e5770-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="e5770-121">InstallationPolicy</span></span>| <span data-ttu-id="e5770-122">Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5770-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="e5770-123">Paket kaynağına güveniyorsanız olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e5770-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="e5770-124">Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".</span><span class="sxs-lookup"><span data-stu-id="e5770-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="e5770-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="e5770-125">SourceCredential</span></span>| <span data-ttu-id="e5770-126">Uzak bir kaynağı üzerinde paket erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5770-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="e5770-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5770-127">Example</span></span>

<span data-ttu-id="e5770-128">Bu örnek kaydeder http://nuget.org kaynak paketini kullanarak **PackageManagementSource** DSC kaynağı.</span><span class="sxs-lookup"><span data-stu-id="e5770-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```