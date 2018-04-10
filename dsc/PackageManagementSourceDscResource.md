---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC PackageManagementSource Resource
ms.openlocfilehash: 8c0cb5a3b0a019ddb5ed995406f499298103b07c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="c5e2b-103">DSC PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="c5e2b-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="c5e2b-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c5e2b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c5e2b-105">**PackageManagementSource** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) kaydetmek veya paket Yönetimi kaynakları bir hedef düğümdeki kaydı için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="c5e2b-106">**Bu şekilde kayıtlı paket Yönetimi kaynaklarını bağlamında sistem, sistem hesabı veya DSC altyapısı tarafından kullanılabilir kaydedilir.**</span><span class="sxs-lookup"><span data-stu-id="c5e2b-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="c5e2b-107">Bu kaynak için gerekli **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5e2b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5e2b-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c5e2b-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c5e2b-109">Properties</span></span>
|  <span data-ttu-id="c5e2b-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="c5e2b-110">Property</span></span>  |  <span data-ttu-id="c5e2b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5e2b-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="c5e2b-112">Ad</span><span class="sxs-lookup"><span data-stu-id="c5e2b-112">Name</span></span>| <span data-ttu-id="c5e2b-113">Kayıtlı veya sisteminizde kaydı için paket kaynağı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="c5e2b-114">Emin olun</span><span class="sxs-lookup"><span data-stu-id="c5e2b-114">Ensure</span></span>| <span data-ttu-id="c5e2b-115">Paket kaynağı kaydedildiğinde veya kaydı için olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="c5e2b-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="c5e2b-116">InstallationPolicy</span></span>| <span data-ttu-id="c5e2b-117">Paket kaynağı güven olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="c5e2b-118">Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".</span><span class="sxs-lookup"><span data-stu-id="c5e2b-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="c5e2b-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="c5e2b-119">ProviderName</span></span>| <span data-ttu-id="c5e2b-120">Paket kaynağı ile birlikte çalışma ile yapabilecekleriniz OneGet sağlayıcının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="c5e2b-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="c5e2b-121">SourceUri</span></span>| <span data-ttu-id="c5e2b-122">Paket kaynağının URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="c5e2b-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="c5e2b-123">SourceCredential</span></span>| <span data-ttu-id="c5e2b-124">Uzak bir kaynağı üzerinde paket erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="c5e2b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5e2b-125">Example</span></span>

<span data-ttu-id="c5e2b-126">Bu örnek kaydeder http://nuget.org kaynak paketini kullanarak **PackageManagementSource** DSC kaynağı.</span><span class="sxs-lookup"><span data-stu-id="c5e2b-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```