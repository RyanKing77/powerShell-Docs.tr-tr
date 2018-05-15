
---
<span data-ttu-id="73121-101">MS.Date: 06/12/2017 katkıda bulunan: manikb ms.topic: başvuru anahtar sözcükler: Galerisi, powershell, cmdlet, psget Başlık: önyükleme NuGet</span><span class="sxs-lookup"><span data-stu-id="73121-101">ms.date :  06/12/2017 contributor:  manikb ms.topic:  reference keywords:  gallery,powershell,cmdlet,psget title:  Bootstrapping NuGet</span></span>
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="73121-102">NuGet sağlayıcısı ve NuGet.exe bootstrap</span><span class="sxs-lookup"><span data-stu-id="73121-102">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="73121-103">NuGet.exe son NuGet sağlayıcısında dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="73121-103">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="73121-104">Yayım bir modül veya komut dosyası işlemleri için ikili yürütülebilir NuGet.exe PowerShellGet gerektirir.</span><span class="sxs-lookup"><span data-stu-id="73121-104">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="73121-105">Diğer tüm işlemler için NuGet sağlayıcısı yalnızca dahil olmak üzere *Bul*, *yükleme*, *kaydetmek*, ve *kaldırma*.</span><span class="sxs-lookup"><span data-stu-id="73121-105">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="73121-106">PowerShellGet NuGet sağlayıcı NuGet.exe ve birleştirilmiş bir önyükleme ya da yalnızca NuGet sağlayıcısının önyükleme ya da işlemek için mantığı içerir.</span><span class="sxs-lookup"><span data-stu-id="73121-106">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="73121-107">Her iki durumda da, yalnızca tek bir komut istemi ileti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73121-107">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="73121-108">Makine Internet'e bağlı değilse, kullanıcı veya yönetici NuGet sağlayıcı ve/veya NuGet.exe dosya güvenilir bir örneğini bağlantısı kesilmiş makineye kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73121-108">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

><span data-ttu-id="73121-109">**Not**: sürüm 6 ile başlayarak, NuGet sağlayıcı PowerShell yüklemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="73121-109">**Note**: Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="73121-110">NuGet sağlayıcısı Internet bir makinede yüklü değil, hatayı giderme bağlı</span><span class="sxs-lookup"><span data-stu-id="73121-110">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="73121-111">NuGet sağlayıcısı kullanılabilir ve NuGet.exe Internet bir makinede yayımlama işlemi sırasında kullanılabilir olmadığında hatayı giderme bağlı</span><span class="sxs-lookup"><span data-stu-id="73121-111">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="73121-112">NuGet sağlayıcısı ve NuGet.exe Internet bir makinede yayımlama işlemi sırasında kullanılabilir olmadığında hatayı giderme bağlı</span><span class="sxs-lookup"><span data-stu-id="73121-112">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="73121-113">El ile Internet'e bağlı olmayan bir makinede NuGet sağlayıcısı önyükleme</span><span class="sxs-lookup"><span data-stu-id="73121-113">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="73121-114">Yukarıda gösterilen işlemleri makine Internet'e bağlı ve dosyaları genel bir konumdan yükleyebilirsiniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="73121-114">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="73121-115">Bu mümkün değilse, yalnızca yukarıda verilen işlemleri kullanarak bir makine bootstrap ve el ile çevrimdışı güvenilen işlemi aracılığıyla yalıtılmış düğüme sağlayıcı kopyalamak için bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="73121-115">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="73121-116">Bu senaryo için en yaygın kullanım örneği Özel Galeri yalıtılmış bir ortamı desteklemek kullanılabilir olduğunda.</span><span class="sxs-lookup"><span data-stu-id="73121-116">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="73121-117">Internet bağlantılı makine bootstrap yukarıdaki işlemini tamamladıktan sonra sağlayıcı dosyalar konumda bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="73121-117">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="73121-118">NuGet sağlayıcısı klasör/dosya yapısını (büyük olasılıkla farklı sürüm numarasıyla) olacaktır:</span><span class="sxs-lookup"><span data-stu-id="73121-118">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

<span data-ttu-id="73121-119">NuGet</span><span class="sxs-lookup"><span data-stu-id="73121-119">NuGet</span></span><br>
<span data-ttu-id="73121-120">--2.8.5.208</span><span class="sxs-lookup"><span data-stu-id="73121-120">--2.8.5.208</span></span><br>
<span data-ttu-id="73121-121">---Microsoft.PackageManagement.NuGetProvider.dll</span><span class="sxs-lookup"><span data-stu-id="73121-121">----Microsoft.PackageManagement.NuGetProvider.dll</span></span>

<span data-ttu-id="73121-122">Bu klasörler ve çevrimdışı makinelere güvenilir bir işlemi kullanarak dosyasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="73121-122">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="73121-123">El ile desteklemek için NuGet.exe önyükleme yayımlama Internet'e bağlı olmayan bir makine üzerindeki işlemleri</span><span class="sxs-lookup"><span data-stu-id="73121-123">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="73121-124">Makine modülleri veya komut dosyalarını kullanarak bir özel galeri yayımlamak için kullanılacaksa NuGet sağlayıcısını el ile bootstrap işleminin yanı sıra *Yayımla-Module* veya *Yayımla-komut dosyası* cmdlet'leri NuGet.exe ikili yürütülebilir dosya gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="73121-124">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the *Publish-Module* or *Publish-Script* cmdlets, the NuGet.exe binary executable file will be required.</span></span>
<span data-ttu-id="73121-125">Bu senaryo için en yaygın kullanım örneği Özel Galeri yalıtılmış bir ortamı desteklemek kullanılabilir olduğunda.</span><span class="sxs-lookup"><span data-stu-id="73121-125">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="73121-126">NuGet.exe dosyasını almak için iki seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="73121-126">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="73121-127">Internet'e bağlı bir makinede bootstrap ve güvenilir bir işlemi kullanarak çevrimdışı makineler dosyaları kopyalamak için bir seçenek değil.</span><span class="sxs-lookup"><span data-stu-id="73121-127">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="73121-128">Internet bağlantılı makine önyüklemesinden sonra NuGet.exe ikili iki klasörlerden birinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="73121-128">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="73121-129">Varsa *Yayımla-Module* veya *Yayımla-komut dosyası* cmdlet yükseltilmiş izinlerle (bir yönetici olarak) yürütülen:</span><span class="sxs-lookup"><span data-stu-id="73121-129">If the *Publish-Module* or *Publish-Script* cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="73121-130">Cmdlet yükseltilmiş izinler olmadan bir kullanıcı olarak yürütüldü ise:</span><span class="sxs-lookup"><span data-stu-id="73121-130">If the cmdlets were executed as a user without elevated permissions:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="73121-131">NuGet.exe NuGet.Org Web sitesinden indirin ikinci bir seçenektir: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span><span class="sxs-lookup"><span data-stu-id="73121-131">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span></span><br>
<span data-ttu-id="73121-132">Üretim makineler için NugGet sürümü seçerken, 2.8.5.208 sonraki olduğundan emin olun ve "önerilen" etiketli sürüm belirleyin.</span><span class="sxs-lookup"><span data-stu-id="73121-132">When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="73121-133">Bir tarayıcı kullanarak indirildiği, dosyanın Engellemeyi Kaldır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="73121-133">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="73121-134">Bu kullanılarak gerçekleştirilebilir *Engellemeyi Kaldır dosya* cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73121-134">This can be performed by using the *Unblock-File* cmdlet.</span></span>

<span data-ttu-id="73121-135">Her iki durumda da, herhangi bir konuma NuGet.exe dosya kopyalanabilir *$env: yol*, ancak Standart konumlar:</span><span class="sxs-lookup"><span data-stu-id="73121-135">In either case, the NuGet.exe file can be copied to any location in *$env:path*, but the standard locations are:</span></span>

<span data-ttu-id="73121-136">Tüm kullanıcıların kullanabilmesi için yürütülebilir dosya kullanılabilir hale getirmek *Yayımla-Module* ve *Yayımla-komut dosyası* cmdlet:</span><span class="sxs-lookup"><span data-stu-id="73121-136">To make the executable available so that all users can use *Publish-Module* and *Publish-Script* cmdlets:</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="73121-137">Yürütülebilir dosya yalnızca belirli bir kullanıcı tarafından kullanılabilir hale getirmek yalnızca o kullanıcının profilindeki konuma kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="73121-137">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```