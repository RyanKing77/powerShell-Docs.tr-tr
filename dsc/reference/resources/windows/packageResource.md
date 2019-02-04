---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Paket DSC kaynağı
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686064"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="664fc-103">Paket DSC kaynağı</span><span class="sxs-lookup"><span data-stu-id="664fc-103">DSC Package Resource</span></span>

<span data-ttu-id="664fc-104">_Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="664fc-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="664fc-105">**Paket** kaynak olarak Windows PowerShell Desired State Configuration (DSC) yüklemek veya bir hedef düğüm üzerinde Windows Installer ve setup.exe paketleri gibi paketleri kaldırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="664fc-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="664fc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="664fc-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="664fc-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="664fc-107">Properties</span></span>

| <span data-ttu-id="664fc-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="664fc-108">Property</span></span> | <span data-ttu-id="664fc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="664fc-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="664fc-110">Adı</span><span class="sxs-lookup"><span data-stu-id="664fc-110">Name</span></span>| <span data-ttu-id="664fc-111">Belirli bir durumu sağlamak istediğiniz paketinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="664fc-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="664fc-112">Yol</span><span class="sxs-lookup"><span data-stu-id="664fc-112">Path</span></span>| <span data-ttu-id="664fc-113">Paketin bulunduğu yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="664fc-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="664fc-114">ProductID</span><span class="sxs-lookup"><span data-stu-id="664fc-114">ProductId</span></span>| <span data-ttu-id="664fc-115">Paketi benzersiz olarak tanımlayan ürün Kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="664fc-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="664fc-116">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="664fc-116">Arguments</span></span>| <span data-ttu-id="664fc-117">Paketi tam olarak sağlanan şekilde geçirilecek bağımsız değişken bir dize listeler.</span><span class="sxs-lookup"><span data-stu-id="664fc-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="664fc-118">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="664fc-118">Credential</span></span>| <span data-ttu-id="664fc-119">Uzak bir kaynak üzerinde paket erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="664fc-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="664fc-120">Bu özellik, paketi yüklemek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="664fc-120">This property is not used to install the package.</span></span> <span data-ttu-id="664fc-121">Paket her zaman yerel sistemde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="664fc-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="664fc-122">Emin olun</span><span class="sxs-lookup"><span data-stu-id="664fc-122">Ensure</span></span>| <span data-ttu-id="664fc-123">Paketin yüklü olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="664fc-123">Indicates if the package is installed.</span></span> <span data-ttu-id="664fc-124">Bu özelliği "Yok" paketi yüklü emin olun (veya paket yüklüyse kaldırmak için) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="664fc-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="664fc-125">"Paket yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="664fc-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="664fc-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="664fc-126">LogPath</span></span>| <span data-ttu-id="664fc-127">Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="664fc-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="664fc-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="664fc-128">DependsOn</span></span> | <span data-ttu-id="664fc-129">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="664fc-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="664fc-130">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="664fc-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="664fc-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="664fc-131">ReturnCode</span></span>| <span data-ttu-id="664fc-132">Beklenen dönüş kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="664fc-132">Indicates the expected return code.</span></span> <span data-ttu-id="664fc-133">Gerçek kodu döndürmesi durumunda beklenen değer, burada, yapılandırma, bir hata döndürür sağlanan eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="664fc-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="664fc-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="664fc-134">Example</span></span>

<span data-ttu-id="664fc-135">Bu örnek belirtilen yolda bulunur ve belirtilen ürün kimliği olan .msi yükleyicisini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="664fc-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```