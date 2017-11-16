---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsPackageCab kaynağı"
ms.openlocfilehash: 9b1bf3cb95abcbe46976ae0fd328280a3a8d7f28
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="f167b-103">DSC WindowsPackageCab kaynağı</span><span class="sxs-lookup"><span data-stu-id="f167b-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="f167b-104">İçin geçerlidir: Windows PowerShell 5.1 ve sonrası</span><span class="sxs-lookup"><span data-stu-id="f167b-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="f167b-105">**WindowsPackageCab** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) yüklemek veya bir hedef düğümde Windows dolap (.cab) paketleri kaldırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f167b-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="f167b-106">Hedef düğüm DISM PowerShell modül yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f167b-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="f167b-107">Bilgi için bkz: [kullanım DISM Windows PowerShell'de](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="f167b-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span> 


## <a name="syntax"></a><span data-ttu-id="f167b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f167b-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="f167b-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f167b-109">Properties</span></span>

|  <span data-ttu-id="f167b-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="f167b-110">Property</span></span>  |  <span data-ttu-id="f167b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f167b-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f167b-112">Ad</span><span class="sxs-lookup"><span data-stu-id="f167b-112">Name</span></span>| <span data-ttu-id="f167b-113">Belirli bir durumu sağlamak istediğiniz paketinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f167b-113">Indicates the name of the package for you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="f167b-114">Emin olun</span><span class="sxs-lookup"><span data-stu-id="f167b-114">Ensure</span></span>| <span data-ttu-id="f167b-115">Paketin yüklü olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f167b-115">Indicates if the package is installed.</span></span> <span data-ttu-id="f167b-116">Bu özelliği paketi yüklü değil emin olun (veya paket yüklüyse kaldırmak için) "yok" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f167b-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="f167b-117">"Paketinin yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f167b-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="f167b-118">Yol</span><span class="sxs-lookup"><span data-stu-id="f167b-118">Path</span></span>| <span data-ttu-id="f167b-119">Paketin bulunduğu yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f167b-119">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="f167b-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="f167b-120">LogPath</span></span>| <span data-ttu-id="f167b-121">Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz yeri tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f167b-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="f167b-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f167b-122">DependsOn</span></span> | <span data-ttu-id="f167b-123">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="f167b-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f167b-124">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **ResourceType**, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.</span><span class="sxs-lookup"><span data-stu-id="f167b-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example"></a><span data-ttu-id="f167b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f167b-125">Example</span></span>

<span data-ttu-id="f167b-126">Aşağıdaki örnek yapılandırma giriş parametreleri alır ve bir .cab dosyası tarafından belirtilen sağlar `$Name` parametresi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f167b-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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

