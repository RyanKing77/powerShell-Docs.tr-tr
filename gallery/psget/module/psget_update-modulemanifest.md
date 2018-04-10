---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Güncelleştirme ModuleManifest
ms.openlocfilehash: 45f40f753af17e82c83dbf57dea13749ba626503
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="update-modulemanifest"></a><span data-ttu-id="ff1b0-103">Güncelleştirme ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="ff1b0-103">Update-ModuleManifest</span></span>
<span data-ttu-id="ff1b0-104">Modül bildirim dosyasını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="ff1b0-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff1b0-105">Description</span></span>

<span data-ttu-id="ff1b0-106">Güncelleştirme ModuleManifest cmdlet'i bir modül bildirimi (.psd1) dosyasını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="ff1b0-107">Notlar</span><span class="sxs-lookup"><span data-stu-id="ff1b0-107">Notes</span></span>
    - <span data-ttu-id="ff1b0-108">DscResourcesToExport yalnızca en son PowerShell sürüm 5.0 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="ff1b0-109">Daha düşük PowerShell sürümlerinde çalıştırılıyorsa alanını güncelleştirmek mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="ff1b0-110">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff1b0-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="ff1b0-111">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="ff1b0-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="ff1b0-112">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="ff1b0-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="ff1b0-113">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="ff1b0-113">Example commands</span></span>

<span data-ttu-id="ff1b0-114">Bu yeni cmdlet Yardım giriş özellik değerlerini dosyasıyla bildirim güncelleştirmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="ff1b0-115">Yeni ModuleManifest yaptığı tüm parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="ff1b0-116">Çok sayıda modülü yazarlar belirtmek istediğiniz fark "\*" gibi FunctionsToExport, CmdletsToExport, dışarı aktarılan değerleri vb. PowerShell Galerisi modülü yayımlama sırasında belirtilmeyen işlevleri ve komutları düzgün galeri doldurulmaz.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="ff1b0-117">Bu nedenle, modül yazarlar güncelleştirme kendi bildirimleri uygun değerlerle öneririz.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="ff1b0-118">Özellikler dışarı aktardığınız modülleri varsa, güncelleştirme ModuleManifest belirtilen bildirim dosyası dışarı aktarılan işlevler, cmdlet'leri, değişkenler vb. alınan bilgilerle doldurun:</span><span class="sxs-lookup"><span data-stu-id="ff1b0-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="ff1b0-119">Güncelleştirme ModuleManifest sonra:</span><span class="sxs-lookup"><span data-stu-id="ff1b0-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="ff1b0-120">Her modül için de ilişkili meta veri alanları vardır.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="ff1b0-121">Meta veri PowrShell galerisinde düzgün görüntülemek için güncelleştirme ModuleManifest PrivateData altında bu alanları doldurmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff1b0-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="ff1b0-122">Bildirim dosyası şablondan PrivateData hashtable aşağıdaki özelliklere sahip</span><span class="sxs-lookup"><span data-stu-id="ff1b0-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```