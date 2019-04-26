---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: NuGet önyükleniyor
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084394"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="ffa53-103">NuGet sağlayıcısı ve NuGet.exe önyükleme</span><span class="sxs-lookup"><span data-stu-id="ffa53-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="ffa53-104">NuGet.exe en son NuGet sağlayıcısında yer almaz.</span><span class="sxs-lookup"><span data-stu-id="ffa53-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="ffa53-105">Yayımlama işlemleri bir modül veya betik için ikili yürütülebilir NuGet.exe PowerShellGet gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ffa53-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span> <span data-ttu-id="ffa53-106">NuGet sağlayıcısı gerekli diğer tüm işlemler için yalnızca dahil olmak üzere *bulmak*, *yükleme*, *Kaydet*, ve *kaldırma*.</span><span class="sxs-lookup"><span data-stu-id="ffa53-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="ffa53-107">PowerShellGet, birleşik bir bootstrap NuGet sağlayıcısı ve NuGet.exe veya önyükleme NuGet sağlayıcısı ya da işlemek için mantığı içerir.</span><span class="sxs-lookup"><span data-stu-id="ffa53-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="ffa53-108">Her iki durumda da, yalnızca tek bir komut istemi ileti gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ffa53-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="ffa53-109">Makinenin Internet'e bağlı değilse, kullanıcı veya yönetici NuGet sağlayıcısı ve/veya NuGet.exe dosya güvenilen bir örneğini bağlantısı kesilmiş makineyi kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffa53-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="ffa53-110">NuGet sağlayıcısı sürüm 6 ile başlayarak, PowerShell yüklenmesi dahildir.</span><span class="sxs-lookup"><span data-stu-id="ffa53-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="ffa53-111">NuGet sağlayıcısı Internet bir makinede yüklü olmayan, hatayı çözmede bağlı</span><span class="sxs-lookup"><span data-stu-id="ffa53-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="ffa53-112">NuGet sağlayıcısı kullanılabilir ve NuGet.exe bir makinede Internet yayımlama işlemi sırasında kullanılabilir olmadığında çözümlenirken hata oluştu bağlı</span><span class="sxs-lookup"><span data-stu-id="ffa53-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="ffa53-113">NuGet sağlayıcısı ve NuGet.exe hem bir makinede Internet yayımlama işlemi sırasında mevcut olmadığı durumlarda hata giderme bağlı</span><span class="sxs-lookup"><span data-stu-id="ffa53-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="ffa53-114">NuGet sağlayıcısı Internet'e bağlı olmayan bir makineye el ile önyükleme</span><span class="sxs-lookup"><span data-stu-id="ffa53-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="ffa53-115">Yukarıda gösterilen işlemler, makine Internet'e bağlı ve dosyalarını ortak bir konumdan indirebilirsiniz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="ffa53-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="ffa53-116">Bu mümkün değilse, yalnızca seçeneğin kullanılması, yukarıda verilen işlemlerin bir makine önyükleme ve sağlayıcı çevrimdışı bir güvenilen işlem yalıtılmış düğümünden el ile kopyalayın sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ffa53-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="ffa53-117">Bu senaryo için en yaygın kullanım örneği, özel bir galeri, yalıtılmış bir ortam desteklemek kullanılabilir andır.</span><span class="sxs-lookup"><span data-stu-id="ffa53-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="ffa53-118">İnternet'e bağlı bir makinede önyükleme için yukarıda işlemi tamamladıktan sonra sağlayıcı dosyalar konumda bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ffa53-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="ffa53-119">NuGet sağlayıcısı klasör/dosya yapısı (büyük olasılıkla farklı sürüm numarasıyla) olacaktır:</span><span class="sxs-lookup"><span data-stu-id="ffa53-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="ffa53-120">Bu klasör ve dosya kullanarak güvenilir bir işlemi çevrimdışı makinelere kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ffa53-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="ffa53-121">Yayımlama işlemleri Internet'e bağlı olmayan bir makineye el ile desteklemek için NuGet.exe önyüklemesi</span><span class="sxs-lookup"><span data-stu-id="ffa53-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="ffa53-122">Makine modüller ya da komut dosyaları için özel bir galeri kullanarak yayımlamak için kullanılacaksa NuGet sağlayıcısını el ile önyükleme işlemi yanı sıra `Publish-Module` veya `Publish-Script` cmdlet'lerini NuGet.exe ikili yürütülebilir dosya gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="ffa53-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="ffa53-123">Bu senaryo için en yaygın kullanım örneği, özel bir galeri, yalıtılmış bir ortam desteklemek kullanılabilir andır.</span><span class="sxs-lookup"><span data-stu-id="ffa53-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="ffa53-124">NuGet.exe dosyası almak için iki seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="ffa53-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="ffa53-125">İnternet'e bağlı olan bir makine önyükleme ve güvenilir bir işlem kullanılarak çevrimdışı makineler için dosyaları kopyalamak için bir seçenek var.</span><span class="sxs-lookup"><span data-stu-id="ffa53-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="ffa53-126">İnternet'e bağlı makine önyüklemesinden sonra NuGet.exe ikili iki klasörlerden birinde yer alır:</span><span class="sxs-lookup"><span data-stu-id="ffa53-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="ffa53-127">Varsa `Publish-Module` veya `Publish-Script` cmdlet'leri (bir yönetici olarak) yükseltilmiş izinlerle yürütülmesini:</span><span class="sxs-lookup"><span data-stu-id="ffa53-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="ffa53-128">Cmdlet'lerin yükseltilmiş izinleri olmayan bir kullanıcı olarak yürütüldü varsa:</span><span class="sxs-lookup"><span data-stu-id="ffa53-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="ffa53-129">NuGet.exe NuGet.Org Web sitesinden indirme ikinci bir seçenektir: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) NugGet sürümü için üretim makinelerinden seçerken, 2.8.5.208 sonraki olduğundan emin olun ve "önerilen" etiketli sürümü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ffa53-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="ffa53-130">Bir tarayıcı kullanarak indirilen, dosyanın Engellemeyi Kaldır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ffa53-130">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="ffa53-131">Bunu kullanarak gerçekleştirilebilir `Unblock-File` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="ffa53-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="ffa53-132">Her iki durumda da NuGet.exe dosyanın herhangi bir konuma kopyalanabilir `$env:path`, ancak Standart konumlar:</span><span class="sxs-lookup"><span data-stu-id="ffa53-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="ffa53-133">Tüm kullanıcılar kullanabilmesi için yürütülebilir dosya kullanılabilir hale getirmek `Publish-Module` ve `Publish-Script` cmdlet'leri:</span><span class="sxs-lookup"><span data-stu-id="ffa53-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="ffa53-134">Yürütülebilir dosyanın yalnızca belirli bir kullanıcı tarafından kullanılabilir hale getirmek için yalnızca bu kullanıcının profilinde bir konuma kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="ffa53-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
