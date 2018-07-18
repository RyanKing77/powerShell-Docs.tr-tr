---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Modülleri ile uyumlu PowerShell sürümleri
ms.openlocfilehash: 2b11d833e7abc50f26b1581f678b9509a098c2c5
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093533"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="3d102-103">Modülleri ile uyumlu PowerShell sürümleri</span><span class="sxs-lookup"><span data-stu-id="3d102-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="3d102-104">Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3d102-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="3d102-105">**Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d102-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="3d102-106">**Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d102-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="3d102-107">PowerShell’in çalışan sürümü, $PSVersionTable’ın PSEdition özelliğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3d102-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable
```

```output
Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="3d102-108">Modül yazarları CompatiblePSEditions modül bildirim anahtarını kullanarak kendi modüllerinin bir veya birden çok PowerShell sürümüyle uyumlu olduğunu bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="3d102-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="3d102-109">Bu anahtar yalnızca PowerShell 5.1 veya üstünde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3d102-109">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="3d102-110">Bir modül bildirimi CompatiblePSEditions anahtarla belirlendikten sonra alt PowerShell sürümlerinde alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="3d102-110">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="3d102-111">Kullanılabilir modüllerin listesini alırken, listeyi PowerShell sürümüne göre filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d102-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```output
Desktop
Core
```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="3d102-112">Modül yazarları tek modülü hedefleme veya her ikisi de PowerShell sürümleri için (Masaüstü ve çekirdek) yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d102-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="3d102-113">Tek bir modül, hem Masaüstü hem de çekirdek sürümleri üzerinde çalışabilir, ya da RootModule veya $PSEdition değişkenini kullanarak modül bildirimindeki gerekli mantığı eklemek, yazarın Bu modülde olur.</span><span class="sxs-lookup"><span data-stu-id="3d102-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="3d102-114">Modüller, CoreCLR hem FullCLR hedefleyen derlenen DLL'leri iki kümesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d102-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="3d102-115">Birkaç seçeneğiniz modülünüzde uygun DLL'leri yükleme için mantığı paketlemek için aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d102-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="3d102-116">1. seçenek: birden çok sürümü ve birden çok PowerShell sürümü hedeflemek için bir modül paketleme</span><span class="sxs-lookup"><span data-stu-id="3d102-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="3d102-117">Modül klasör içeriği</span><span class="sxs-lookup"><span data-stu-id="3d102-117">Module folder contents</span></span>

- <span data-ttu-id="3d102-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="3d102-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="3d102-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="3d102-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="3d102-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="3d102-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="3d102-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="3d102-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="3d102-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3d102-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="3d102-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3d102-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="3d102-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="3d102-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="3d102-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="3d102-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="3d102-126">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="3d102-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="3d102-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="3d102-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="3d102-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="3d102-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="3d102-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="3d102-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="3d102-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="3d102-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="3d102-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="3d102-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="3d102-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="3d102-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="3d102-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="3d102-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="3d102-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="3d102-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="3d102-135">PSScriptAnalyzer.psd1 dosyasının içeriği</span><span class="sxs-lookup"><span data-stu-id="3d102-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="3d102-136">PSScriptAnalyzer.psm1 dosyasının içeriği</span><span class="sxs-lookup"><span data-stu-id="3d102-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="3d102-137">Mantıksal geçerli sürümü veya bağlı olarak gerekli bütünleştirilmiş kodları yükler.</span><span class="sxs-lookup"><span data-stu-id="3d102-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="3d102-138">2. seçenek: $PSEdition değişkeni PSD1 uygun DLL'ler ve iç içe geçmiş ve gerekli modülleri yüklemek için kullanın</span><span class="sxs-lookup"><span data-stu-id="3d102-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="3d102-139">PS 5.1 veya yeni, $PSEdition genel değişkeni modül bildirim dosyasında izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3d102-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="3d102-140">Bu değişkeni kullanarak, modül yazarına modül bildirim dosyasında koşullu değerleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d102-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="3d102-141">Kısıtlı dil modu veya veri bölümündeki $PSEdition değişkeni başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="3d102-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="3d102-142">Bir modül bildirimi CompatiblePSEditions anahtarı ile belirtilen ya da $PSEdition değişkenini kullanır sonra daha düşük PowerShell sürümlerinde alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="3d102-142">Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>

#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="3d102-143">Örnek modülü bildirim dosyası CompatiblePSEditions anahtarı</span><span class="sxs-lookup"><span data-stu-id="3d102-143">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
# - - -

# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}

# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}

# -- - -
}
```

#### <a name="module-contents"></a><span data-ttu-id="3d102-144">Modül içeriği</span><span class="sxs-lookup"><span data-stu-id="3d102-144">Module contents</span></span>

```powershell
dir -Recurse
```

```output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/5/2016   1:37 PM                clr
d-----         7/5/2016   1:36 PM                coreclr
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl
```

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="3d102-145">PowerShell Galerisi kullanıcılar etiketleri PSEdition_Desktop ve PSEdition_Core kullanarak belirli bir PowerShell sürümünde desteklenen modüllerin listesini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d102-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="3d102-146">PSEdition_Desktop ve PSEdition_Core etiketleri olmadan modülleri PowerShell Masaüstü sürümleri için üzerinde sorunsuz çalışacak şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3d102-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="3d102-147">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="3d102-147">More details</span></span>

[<span data-ttu-id="3d102-148">PSEditions’ı olan Betikler</span><span class="sxs-lookup"><span data-stu-id="3d102-148">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="3d102-149">PowerShellGallery pseditions'ı desteği</span><span class="sxs-lookup"><span data-stu-id="3d102-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)

[<span data-ttu-id="3d102-150">Modül bildirimini güncelleştir</span><span class="sxs-lookup"><span data-stu-id="3d102-150">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)