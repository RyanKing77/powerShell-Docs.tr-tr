---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC PackageManagementSource kaynağı
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="96358-103">DSC PackageManagementSource kaynağı</span><span class="sxs-lookup"><span data-stu-id="96358-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="96358-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="96358-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="96358-105">**PackageManagementSource** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) kaydetmek veya paket Yönetimi kaynakları bir hedef düğümdeki kaydı için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="96358-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="96358-106">**Bu şekilde kayıtlı paket Yönetimi kaynaklarını bağlamında sistem, sistem hesabı veya DSC altyapısı tarafından kullanılabilir kaydedilir.**</span><span class="sxs-lookup"><span data-stu-id="96358-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="96358-107">Bu kaynak için gerekli **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="96358-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="96358-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96358-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="96358-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="96358-109">Properties</span></span>
|  <span data-ttu-id="96358-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="96358-110">Property</span></span>  |  <span data-ttu-id="96358-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96358-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="96358-112">Ad</span><span class="sxs-lookup"><span data-stu-id="96358-112">Name</span></span>| <span data-ttu-id="96358-113">Kayıtlı veya sisteminizde kaydı için paket kaynağı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96358-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="96358-114">Emin olun</span><span class="sxs-lookup"><span data-stu-id="96358-114">Ensure</span></span>| <span data-ttu-id="96358-115">Paket kaynağı kaydedildiğinde veya kaydı için olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="96358-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="96358-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="96358-116">InstallationPolicy</span></span>| <span data-ttu-id="96358-117">Paket kaynağı güven olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="96358-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="96358-118">Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".</span><span class="sxs-lookup"><span data-stu-id="96358-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="96358-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="96358-119">ProviderName</span></span>| <span data-ttu-id="96358-120">Paket kaynağı ile birlikte çalışma ile yapabilecekleriniz OneGet sağlayıcının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96358-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="96358-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="96358-121">SourceUri</span></span>| <span data-ttu-id="96358-122">Paket kaynağının URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="96358-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="96358-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="96358-123">SourceCredential</span></span>| <span data-ttu-id="96358-124">Uzak bir kaynağı üzerinde paket erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="96358-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="96358-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="96358-125">Example</span></span>

<span data-ttu-id="96358-126">Bu örnek kaydeder http://nuget.org kaynak paketini kullanarak **PackageManagementSource** DSC kaynağı.</span><span class="sxs-lookup"><span data-stu-id="96358-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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