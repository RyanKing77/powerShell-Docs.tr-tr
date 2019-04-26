---
ms.date: 06/20/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC PackageManagementSource kaynak
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077594"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="29af0-103">DSC PackageManagementSource kaynak</span><span class="sxs-lookup"><span data-stu-id="29af0-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="29af0-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="29af0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="29af0-105">**PackageManagementSource** kaynak olarak Windows PowerShell Desired State Configuration (DSC) kaydetmek veya paket Yönetimi kaynakları bir hedef düğümdeki kaydını silmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="29af0-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="29af0-106">**Bu şekilde kayıtlı paket Yönetimi kaynakları, sistem hesabı veya DSC altyapısı tarafından kullanılabilir sistem bağlamı altında kaydedilir.**</span><span class="sxs-lookup"><span data-stu-id="29af0-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="29af0-107">Bu kaynak gerektiriyor **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="29af0-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29af0-108">**PackageManagement** modülü olmalıdır en az sürüm 1.1.7.0 doğru olması aşağıdaki özellik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="29af0-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="29af0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29af0-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="29af0-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="29af0-110">Properties</span></span>

|  <span data-ttu-id="29af0-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="29af0-111">Property</span></span>  |  <span data-ttu-id="29af0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29af0-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="29af0-113">Adı</span><span class="sxs-lookup"><span data-stu-id="29af0-113">Name</span></span>| <span data-ttu-id="29af0-114">Kayıtlı veya Kayıtsız sisteminizde için paket kaynağının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29af0-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="29af0-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="29af0-115">ProviderName</span></span>| <span data-ttu-id="29af0-116">Paket kaynağı ile birlikte çalışma ile yapabilecekleriniz OneGet sağlayıcısı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29af0-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="29af0-117">Kaynak konumu</span><span class="sxs-lookup"><span data-stu-id="29af0-117">SourceLocation</span></span>| <span data-ttu-id="29af0-118">Paket kaynağının URI'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="29af0-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="29af0-119">Emin olun</span><span class="sxs-lookup"><span data-stu-id="29af0-119">Ensure</span></span>| <span data-ttu-id="29af0-120">Kayıtlı veya Kayıtsız için paket kaynağı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="29af0-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="29af0-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="29af0-121">InstallationPolicy</span></span>| <span data-ttu-id="29af0-122">Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29af0-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="29af0-123">Kaynak paketin güvendiğiniz olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="29af0-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="29af0-124">Biri: "Güvenilmeyen", "güvenilir".</span><span class="sxs-lookup"><span data-stu-id="29af0-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="29af0-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="29af0-125">SourceCredential</span></span>| <span data-ttu-id="29af0-126">Uzak bir kaynak üzerinde paket erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="29af0-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="29af0-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="29af0-127">Example</span></span>

<span data-ttu-id="29af0-128">Bu örnekte kaydeder http://nuget.org kaynak paketini kullanarak **PackageManagementSource** DSC kaynağı.</span><span class="sxs-lookup"><span data-stu-id="29af0-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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