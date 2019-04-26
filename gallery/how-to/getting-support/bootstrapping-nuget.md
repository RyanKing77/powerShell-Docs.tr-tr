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
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>NuGet sağlayıcısı ve NuGet.exe önyükleme

NuGet.exe en son NuGet sağlayıcısında yer almaz. Yayımlama işlemleri bir modül veya betik için ikili yürütülebilir NuGet.exe PowerShellGet gerektirir. NuGet sağlayıcısı gerekli diğer tüm işlemler için yalnızca dahil olmak üzere *bulmak*, *yükleme*, *Kaydet*, ve *kaldırma*.
PowerShellGet, birleşik bir bootstrap NuGet sağlayıcısı ve NuGet.exe veya önyükleme NuGet sağlayıcısı ya da işlemek için mantığı içerir. Her iki durumda da, yalnızca tek bir komut istemi ileti gerçekleşmelidir. Makinenin Internet'e bağlı değilse, kullanıcı veya yönetici NuGet sağlayıcısı ve/veya NuGet.exe dosya güvenilen bir örneğini bağlantısı kesilmiş makineyi kopyalamanız gerekir.

> [!NOTE]
> NuGet sağlayıcısı sürüm 6 ile başlayarak, PowerShell yüklenmesi dahildir.

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>NuGet sağlayıcısı Internet bir makinede yüklü olmayan, hatayı çözmede bağlı

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>NuGet sağlayıcısı kullanılabilir ve NuGet.exe bir makinede Internet yayımlama işlemi sırasında kullanılabilir olmadığında çözümlenirken hata oluştu bağlı

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

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>NuGet sağlayıcısı ve NuGet.exe hem bir makinede Internet yayımlama işlemi sırasında mevcut olmadığı durumlarda hata giderme bağlı

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

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>NuGet sağlayıcısı Internet'e bağlı olmayan bir makineye el ile önyükleme

Yukarıda gösterilen işlemler, makine Internet'e bağlı ve dosyalarını ortak bir konumdan indirebilirsiniz varsayılır. Bu mümkün değilse, yalnızca seçeneğin kullanılması, yukarıda verilen işlemlerin bir makine önyükleme ve sağlayıcı çevrimdışı bir güvenilen işlem yalıtılmış düğümünden el ile kopyalayın sağlamaktır. Bu senaryo için en yaygın kullanım örneği, özel bir galeri, yalıtılmış bir ortam desteklemek kullanılabilir andır.

İnternet'e bağlı bir makinede önyükleme için yukarıda işlemi tamamladıktan sonra sağlayıcı dosyalar konumda bulabilirsiniz:

`C:\Program Files\PackageManagement\ProviderAssemblies\`

NuGet sağlayıcısı klasör/dosya yapısı (büyük olasılıkla farklı sürüm numarasıyla) olacaktır:

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Bu klasör ve dosya kullanarak güvenilir bir işlemi çevrimdışı makinelere kopyalayın.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Yayımlama işlemleri Internet'e bağlı olmayan bir makineye el ile desteklemek için NuGet.exe önyüklemesi

Makine modüller ya da komut dosyaları için özel bir galeri kullanarak yayımlamak için kullanılacaksa NuGet sağlayıcısını el ile önyükleme işlemi yanı sıra `Publish-Module` veya `Publish-Script` cmdlet'lerini NuGet.exe ikili yürütülebilir dosya gerekecektir.

Bu senaryo için en yaygın kullanım örneği, özel bir galeri, yalıtılmış bir ortam desteklemek kullanılabilir andır. NuGet.exe dosyası almak için iki seçenek vardır.

İnternet'e bağlı olan bir makine önyükleme ve güvenilir bir işlem kullanılarak çevrimdışı makineler için dosyaları kopyalamak için bir seçenek var. İnternet'e bağlı makine önyüklemesinden sonra NuGet.exe ikili iki klasörlerden birinde yer alır:

Varsa `Publish-Module` veya `Publish-Script` cmdlet'leri (bir yönetici olarak) yükseltilmiş izinlerle yürütülmesini:

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Cmdlet'lerin yükseltilmiş izinleri olmayan bir kullanıcı olarak yürütüldü varsa:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

NuGet.exe NuGet.Org Web sitesinden indirme ikinci bir seçenektir: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) NugGet sürümü için üretim makinelerinden seçerken, 2.8.5.208 sonraki olduğundan emin olun ve "önerilen" etiketli sürümü tanımlayın. Bir tarayıcı kullanarak indirilen, dosyanın Engellemeyi Kaldır unutmayın. Bunu kullanarak gerçekleştirilebilir `Unblock-File` cmdlet'i.

Her iki durumda da NuGet.exe dosyanın herhangi bir konuma kopyalanabilir `$env:path`, ancak Standart konumlar:

Tüm kullanıcılar kullanabilmesi için yürütülebilir dosya kullanılabilir hale getirmek `Publish-Module` ve `Publish-Script` cmdlet'leri:

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Yürütülebilir dosyanın yalnızca belirli bir kullanıcı tarafından kullanılabilir hale getirmek için yalnızca bu kullanıcının profilinde bir konuma kopyalayın:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
