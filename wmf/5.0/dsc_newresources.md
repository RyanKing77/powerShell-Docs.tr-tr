---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: c9ccd91a791c74682325cb8ee704ac32b9edf284
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="new-built-in-dsc-resources"></a><span data-ttu-id="5ea76-102">Yeni yerleşik DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="5ea76-102">New built-in DSC resources</span></span>

<span data-ttu-id="5ea76-103">WMF 5.0 RTM 4 yeni DSC kaynakları sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5ea76-103">WMF 5.0 RTM has 4 new DSC resources:</span></span>
* <span data-ttu-id="5ea76-104">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-104">WindowsFeatureSet</span></span>
* <span data-ttu-id="5ea76-105">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-105">WindowsOptionalFeatureSet</span></span>
* <span data-ttu-id="5ea76-106">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-106">ServiceSet</span></span>
* <span data-ttu-id="5ea76-107">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-107">ProcessSet</span></span>

<span data-ttu-id="5ea76-108">Bu kaynaklar, tek kaynak çağrısı kullanarak birden çok örneği yapılandırmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ea76-108">These resources provide an easy way to configure multiple instances using a single resource call.</span></span>

## <a name="windowsfeatureset"></a><span data-ttu-id="5ea76-109">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-109">WindowsFeatureSet</span></span>

```powershell
# Get the syntax of WindowsFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsFeatureSet -Syntax

WindowsFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [Ensure = [String]]
    [Source = [String]]
    [IncludeAllSubFeature = [Boolean]]
    [Credential = [PSCredential]]
    [LogPath = [String]]
}
```

## <a name="windowsoptionalfeatureset"></a><span data-ttu-id="5ea76-110">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-110">WindowsOptionalFeatureSet</span></span>

```powershell
# Get the syntax of WindowsOptionalFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsOptionalFeatureSet -Syntax

WindowsOptionalFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    Ensure = [String]
    [Source = [String[]]]
    [RemoveFilesOnDisable = [Boolean]]
    [LogPath = [String]]
    [NoWindowsUpdateCheck = [Boolean]]
    [LogLevel = [String]]
}
```

## <a name="serviceset"></a><span data-ttu-id="5ea76-111">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-111">ServiceSet</span></span>

```powershell
# Get the syntax of ServiceSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ServiceSet -Syntax

ServiceSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [StartupType = [String]]
    [BuiltInAccount = [String]]
    [State = [String]]
    [Ensure = [String]]
    [Credential = [PSCredential]]
}
```

## <a name="processset"></a><span data-ttu-id="5ea76-112">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="5ea76-112">ProcessSet</span></span>

```powershell
# Get the syntax of ProcessSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ProcessSet -Syntax

ProcessSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Path = [String[]]
    [Credential = [PSCredential]]
    [Ensure = [String]]
    [StandardOutputPath = [String]]
    [StandardErrorPath = [String]]
    [StandardInputPath = [String]]
    [WorkingDirectory = [String]]
}
```