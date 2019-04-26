---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsPackageCab kaynağı
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076948"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="9087f-103">DSC WindowsPackageCab kaynağı</span><span class="sxs-lookup"><span data-stu-id="9087f-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="9087f-104">Uygulama hedefi: Windows PowerShell 5.1 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="9087f-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="9087f-105">**WindowsPackageCab** kaynak olarak Windows PowerShell Desired State Configuration (DSC) yüklemek veya bir hedef düğümde Windows dolap (.cab) paketleri kaldırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9087f-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="9087f-106">Hedef düğüm DISM PowerShell Modülü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9087f-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="9087f-107">Bilgi için [Windows PowerShell DISM kullanım](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="9087f-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="9087f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9087f-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="9087f-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9087f-109">Properties</span></span>

|  <span data-ttu-id="9087f-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="9087f-110">Property</span></span>  |  <span data-ttu-id="9087f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9087f-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="9087f-112">Adı</span><span class="sxs-lookup"><span data-stu-id="9087f-112">Name</span></span>| <span data-ttu-id="9087f-113">Belirli bir durumu sağlamak istediğiniz için paket adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9087f-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9087f-114">Emin olun</span><span class="sxs-lookup"><span data-stu-id="9087f-114">Ensure</span></span>| <span data-ttu-id="9087f-115">Paketin yüklü olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9087f-115">Indicates if the package is installed.</span></span> <span data-ttu-id="9087f-116">Bu özelliği "Yok" paketi yüklü emin olun (veya paket yüklüyse kaldırmak için) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9087f-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="9087f-117">"Paket yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9087f-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="9087f-118">Yol</span><span class="sxs-lookup"><span data-stu-id="9087f-118">Path</span></span>| <span data-ttu-id="9087f-119">Paketin bulunduğu yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="9087f-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="9087f-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="9087f-120">LogPath</span></span>| <span data-ttu-id="9087f-121">Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9087f-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="9087f-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="9087f-122">DependsOn</span></span> | <span data-ttu-id="9087f-123">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9087f-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9087f-124">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="9087f-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="9087f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="9087f-125">Example</span></span>

<span data-ttu-id="9087f-126">Aşağıdaki örnek yapılandırma parametrelerini alır ve .cab dosyası tarafından belirtilen sağlar `$Name` parametresi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9087f-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```