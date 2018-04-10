---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: NuGet sağlayıcısı ve EXE önyükleme
ms.openlocfilehash: 1c8d99491aec6d2a598facb909c1f36f4bb979e7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="bootstrap-both-nuget-provider-and-nugetexe-or-bootstrap-only-nuget-provider"></a>NuGet sağlayıcısı ve NuGet.exe bootstrap veya yalnızca NuGet sağlayıcısı bootstrap

NuGet.exe son NuGet sağlayıcısında dahil edilmez.
Yayım bir modül veya komut dosyası işlemleri için ikili yürütülebilir NuGet.exe PowerShellGet gerektirir.
Diğer tüm işlemler için NuGet sağlayıcısı yalnızca dahil olmak üzere *Bul*, *yükleme*, *kaydetmek*, ve *kaldırma*.
PowerShellGet NuGet sağlayıcı NuGet.exe ve birleştirilmiş bir önyükleme ya da yalnızca NuGet sağlayıcısının önyükleme ya da işlemek için mantığı içerir.
Her iki durumda da, yalnızca tek bir komut istemi ileti olmalıdır.
Makine Internet'e bağlı değilse, kullanıcı veya yönetici NuGet sağlayıcı ve/veya NuGet.exe dosya güvenilir bir örneğini bağlantısı kesilmiş makineye kopyalamanız gerekir.

>**Not**: sürüm 6 ile başlayarak, NuGet sağlayıcı PowerShell yüklemesinde bulunur. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>NuGet sağlayıcısı Internet bir makinede yüklü değil, hatayı giderme bağlı

```powershell
PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

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
## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>NuGet sağlayıcısı kullanılabilir ve NuGet.exe Internet bir makinede yayımlama işlemi sırasında kullanılabilir olmadığında hatayı giderme bağlı

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>NuGet sağlayıcısı ve NuGet.exe Internet bir makinede yayımlama işlemi sırasında kullanılabilir olmadığında hatayı giderme bağlı

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>El ile Internet'e bağlı olmayan bir makinede NuGet sağlayıcısı önyükleme

Yukarıda gösterilen işlemleri makine Internet'e bağlı ve dosyaları genel bir konumdan yükleyebilirsiniz varsayalım.
Bu mümkün değilse, yalnızca yukarıda verilen işlemleri kullanarak bir makine bootstrap ve el ile çevrimdışı güvenilen işlemi aracılığıyla yalıtılmış düğüme sağlayıcı kopyalamak için bir seçenektir.
Bu senaryo için en yaygın kullanım örneği Özel Galeri yalıtılmış bir ortamı desteklemek kullanılabilir olduğunda.

Internet bağlantılı makine bootstrap yukarıdaki işlemini tamamladıktan sonra sağlayıcı dosyalar konumda bulabilirsiniz:
```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

NuGet sağlayıcısı klasör/dosya yapısını (büyük olasılıkla farklı sürüm numarasıyla) olacaktır:

NuGet<br>
--2.8.5.208<br>
----Microsoft.PackageManagement.NuGetProvider.dll

Bu klasörler ve çevrimdışı makinelere güvenilir bir işlemi kullanarak dosyasını kopyalayın.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>El ile desteklemek için NuGet.exe önyükleme yayımlama Internet'e bağlı olmayan bir makine üzerindeki işlemleri

Makine modülleri veya komut dosyalarını kullanarak bir özel galeri yayımlamak için kullanılacaksa NuGet sağlayıcısını el ile bootstrap işleminin yanı sıra *Yayımla-Module* veya *Yayımla-komut dosyası* cmdlet'leri NuGet.exe ikili yürütülebilir dosya gerekli olacaktır.
Bu senaryo için en yaygın kullanım örneği Özel Galeri yalıtılmış bir ortamı desteklemek kullanılabilir olduğunda.
NuGet.exe dosyasını almak için iki seçenek vardır.

Internet'e bağlı bir makinede bootstrap ve güvenilir bir işlemi kullanarak çevrimdışı makineler dosyaları kopyalamak için bir seçenek değil.
Internet bağlantılı makine önyüklemesinden sonra NuGet.exe ikili iki klasörlerden birinde bulunur:

Varsa *Yayımla-Module* veya *Yayımla-komut dosyası* cmdlet yükseltilmiş izinlerle (bir yönetici olarak) yürütülen:
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Cmdlet yükseltilmiş izinler olmadan bir kullanıcı olarak yürütüldü ise:
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

NuGet.exe NuGet.Org Web sitesinden indirin ikinci bir seçenektir: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)<br>
Üretim makineler için NugGet sürümü seçerken, 2.8.5.208 sonraki olduğundan emin olun ve "önerilen" etiketli sürüm belirleyin.
Bir tarayıcı kullanarak indirildiği, dosyanın Engellemeyi Kaldır unutmayın.
Bu kullanılarak gerçekleştirilebilir *Engellemeyi Kaldır dosya* cmdlet'i.

Her iki durumda da, herhangi bir konuma NuGet.exe dosya kopyalanabilir *$env: yol*, ancak Standart konumlar:

Tüm kullanıcıların kullanabilmesi için yürütülebilir dosya kullanılabilir hale getirmek *Yayımla-Module* ve *Yayımla-komut dosyası* cmdlet:
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Yürütülebilir dosya yalnızca belirli bir kullanıcı tarafından kullanılabilir hale getirmek yalnızca o kullanıcının profilindeki konuma kopyalayın:
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```