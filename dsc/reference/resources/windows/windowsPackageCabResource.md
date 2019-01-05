---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsPackageCab kaynağı
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048655"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="afeb9-103">DSC WindowsPackageCab kaynağı</span><span class="sxs-lookup"><span data-stu-id="afeb9-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="afeb9-104">Şunun için geçerlidir: Windows PowerShell 5.1 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="afeb9-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="afeb9-105">**WindowsPackageCab** kaynak olarak Windows PowerShell Desired State Configuration (DSC) yüklemek veya bir hedef düğümde Windows dolap (.cab) paketleri kaldırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="afeb9-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="afeb9-106">Hedef düğüm DISM PowerShell Modülü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="afeb9-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="afeb9-107">Bilgi için [Windows PowerShell DISM kullanım](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="afeb9-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="afeb9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afeb9-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="afeb9-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="afeb9-109">Properties</span></span>

|  <span data-ttu-id="afeb9-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="afeb9-110">Property</span></span>  |  <span data-ttu-id="afeb9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afeb9-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="afeb9-112">Ad</span><span class="sxs-lookup"><span data-stu-id="afeb9-112">Name</span></span>| <span data-ttu-id="afeb9-113">Belirli bir durumu sağlamak istediğiniz için paket adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="afeb9-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="afeb9-114">Emin olun</span><span class="sxs-lookup"><span data-stu-id="afeb9-114">Ensure</span></span>| <span data-ttu-id="afeb9-115">Paketin yüklü olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="afeb9-115">Indicates if the package is installed.</span></span> <span data-ttu-id="afeb9-116">Bu özelliği "Yok" paketi yüklü emin olun (veya paket yüklüyse kaldırmak için) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="afeb9-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="afeb9-117">"Paket yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="afeb9-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="afeb9-118">Yol</span><span class="sxs-lookup"><span data-stu-id="afeb9-118">Path</span></span>| <span data-ttu-id="afeb9-119">Paketin bulunduğu yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="afeb9-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="afeb9-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="afeb9-120">LogPath</span></span>| <span data-ttu-id="afeb9-121">Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="afeb9-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="afeb9-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="afeb9-122">DependsOn</span></span> | <span data-ttu-id="afeb9-123">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="afeb9-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="afeb9-124">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="afeb9-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="afeb9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="afeb9-125">Example</span></span>

<span data-ttu-id="afeb9-126">Aşağıdaki örnek yapılandırma parametrelerini alır ve .cab dosyası tarafından belirtilen sağlar `$Name` parametresi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="afeb9-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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