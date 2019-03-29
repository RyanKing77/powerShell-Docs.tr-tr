---
ms.date: 03/28/2019
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Modülleri ile uyumlu PowerShell sürümleri
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623849"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="c2a0e-103">Modülleri ile uyumlu PowerShell sürümleri</span><span class="sxs-lookup"><span data-stu-id="c2a0e-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="c2a0e-104">Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="c2a0e-105">**Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş, hem Windows Masaüstü, Windows Server, Windows Sunucu Çekirdeği ve çoğu Windows sürümleri üzerinde Windows PowerShell 5.1, Windows PowerShell v4.0 ve aşağıda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="c2a0e-106">**Çekirdek sürümü:** .NET Core üzerine yapılandırılan, PowerShell Core 6.0 ve üzeri, Windows PowerShell 5.1 yanı sıra kapladığı alanın azaltılmış olması Windows IOT ve Windows Nanoserver gibi Windows sürümleri üzerinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="c2a0e-107">PowerShell sürümleri hakkında daha fazla bilgi için bkz. [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="c2a0e-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="c2a0e-108">Uyumlu sürümleri bildirme</span><span class="sxs-lookup"><span data-stu-id="c2a0e-108">Declaring compatible editions</span></span>

<span data-ttu-id="c2a0e-109">Modül yazarları CompatiblePSEditions modül bildirim anahtarını kullanarak kendi modüllerinin bir veya birden çok PowerShell sürümüyle uyumlu olduğunu bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="c2a0e-110">Bu anahtar yalnızca PowerShell 5.1 veya üstünde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a0e-111">Bir modül bildirimi CompatiblePSEditions anahtarla belirlendikten sonra PowerShell sürüm 4 ve aşağıdaki içeri aktarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="c2a0e-112">Kullanılabilir modüllerin listesini alırken, listeyi PowerShell sürümüne göre filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="c2a0e-113">Birden çok sürümü hedefleme</span><span class="sxs-lookup"><span data-stu-id="c2a0e-113">Targeting multiple editions</span></span>

<span data-ttu-id="c2a0e-114">Modül yazarları, tek bir modül hedefleme veya her ikisi de PowerShell sürümleri için (Masaüstü ve çekirdek) yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="c2a0e-115">Tek bir modül, hem Masaüstü hem de çekirdek sürümleri üzerinde çalışabilir, ya da RootModule veya $PSEdition değişkenini kullanarak modül bildirimindeki gerekli mantığı eklemek, yazarın Bu modülde olur.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="c2a0e-116">Modüller, CoreCLR hem FullCLR hedefleyen derlenen DLL'leri iki kümesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="c2a0e-117">Birkaç seçeneğiniz modülünüzde uygun DLL'leri yükleme için mantığı paketlemek için aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="c2a0e-118">Seçenek 1: Bir modülün birden çok sürümü ve birden çok PowerShell sürümü hedeflemek için paketleme</span><span class="sxs-lookup"><span data-stu-id="c2a0e-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="c2a0e-119">Modül klasör içeriği</span><span class="sxs-lookup"><span data-stu-id="c2a0e-119">Module folder contents</span></span>

- <span data-ttu-id="c2a0e-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="c2a0e-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="c2a0e-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="c2a0e-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="c2a0e-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="c2a0e-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="c2a0e-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="c2a0e-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="c2a0e-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="c2a0e-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="c2a0e-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="c2a0e-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="c2a0e-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="c2a0e-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="c2a0e-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="c2a0e-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="c2a0e-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="c2a0e-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="c2a0e-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="c2a0e-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="c2a0e-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="c2a0e-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="c2a0e-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="c2a0e-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="c2a0e-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="c2a0e-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="c2a0e-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="c2a0e-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="c2a0e-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="c2a0e-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="c2a0e-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="c2a0e-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="c2a0e-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="c2a0e-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="c2a0e-137">PSScriptAnalyzer.psd1 dosyasının içeriği</span><span class="sxs-lookup"><span data-stu-id="c2a0e-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<span data-ttu-id="c2a0e-138">Mantıksal geçerli sürümü veya bağlı olarak gerekli bütünleştirilmiş kodları yükler.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="c2a0e-139">PSScriptAnalyzer.psm1 dosyasının içeriği:</span><span class="sxs-lookup"><span data-stu-id="c2a0e-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="c2a0e-140">2. Seçenek: $PSEdition değişkeni PSD1 dosyası içinde uygun DLL'ler ve iç içe geçmiş ve gerekli modülleri yüklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="c2a0e-141">PS 5.1 veya yeni, $PSEdition genel değişkeni modül bildirim dosyasında izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="c2a0e-142">Bu değişkeni kullanarak, modül yazarına modül bildirim dosyasında koşullu değerleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="c2a0e-143">Kısıtlı dil modu veya veri bölümündeki $PSEdition değişkeni başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a0e-144">Bir modül bildirimi CompatiblePSEditions anahtarı ile belirtilen ya da kullanıyorsa sonra `$PSEdition` değişken, daha düşük PowerShell sürümlerinde içeri aktarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="c2a0e-145">Örnek modülü bildirim dosyası CompatiblePSEditions anahtarı</span><span class="sxs-lookup"><span data-stu-id="c2a0e-145">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
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
}
```

### <a name="module-contents"></a><span data-ttu-id="c2a0e-146">Modül içeriği</span><span class="sxs-lookup"><span data-stu-id="c2a0e-146">Module contents</span></span>

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

<span data-ttu-id="c2a0e-147">PowerShell Galerisi kullanıcılar etiketleri PSEdition_Desktop ve PSEdition_Core kullanarak belirli bir PowerShell sürümünde desteklenen modüllerin listesini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="c2a0e-148">PSEdition_Desktop ve PSEdition_Core etiketleri olmadan modülleri PowerShell Masaüstü sürümleri için üzerinde sorunsuz çalışacak şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c2a0e-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="c2a0e-149">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="c2a0e-149">More details</span></span>

[<span data-ttu-id="c2a0e-150">PSEditions’ı olan Betikler</span><span class="sxs-lookup"><span data-stu-id="c2a0e-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="c2a0e-151">PowerShellGallery pseditions'ı desteği</span><span class="sxs-lookup"><span data-stu-id="c2a0e-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="c2a0e-152">Modül bildirimini güncelleştir</span><span class="sxs-lookup"><span data-stu-id="c2a0e-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="c2a0e-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="c2a0e-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
