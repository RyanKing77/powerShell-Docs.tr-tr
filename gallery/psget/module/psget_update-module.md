---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Güncelleştirme Modülü
ms.openlocfilehash: 89b0111eda4421606843f108dca90519b2c9379e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="update-module"></a><span data-ttu-id="76efe-103">Güncelleştirme Modülü</span><span class="sxs-lookup"><span data-stu-id="76efe-103">Update-Module</span></span>

<span data-ttu-id="76efe-104">İndirir ve yerel bilgisayarda bir çevrimiçi galeriden belirtilen modülleri en yeni sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="76efe-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="76efe-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76efe-105">Description</span></span>

<span data-ttu-id="76efe-106">Güncelleştirme modülü cmdlet daha yeni bir çevrimiçi galeriden yerel bilgisayarda yükle-Module çalıştırarak yüklü olduğu bir Windows PowerShell modülü sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="76efe-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="76efe-107">Gerekli sürümü belirtmediğiniz sürece varsayılan olarak, en yeni sürümünü çevrimiçi galerisinde kullanılabilir Belirtilen modül, yüklenir.</span><span class="sxs-lookup"><span data-stu-id="76efe-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="76efe-108">Modül adı belirterek varolan, yüklü bir modül güncelleştirebilirsiniz; Güncelleştirme modülü $env arar: PSModulePath güncelleştirmek istediğiniz modülü için.</span><span class="sxs-lookup"><span data-stu-id="76efe-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="76efe-109">Name parametresi olmadan güncelleştirme modülünü çalıştıran yerel bilgisayarda güncelleştirilebilir olan tüm modülleri güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="76efe-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="76efe-110">Notlar</span><span class="sxs-lookup"><span data-stu-id="76efe-110">Notes</span></span>

- <span data-ttu-id="76efe-111">Bu cmdlet, Windows PowerShell 3.0 veya sonraki sürümleri Windows PowerShell, Windows 7 veya Windows 2008 R2 ve Windows'un sonraki sürümleri üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="76efe-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="76efe-112">Yükleme modülünü kullanarak ad parametresiyle belirttiğiniz Modülü yüklü değil, bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="76efe-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="76efe-113">Yalnızca, Update-Module yükle-Module çalıştırarak çevrimiçi galeriden yüklü modülleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76efe-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="76efe-114">Kullanımda olan ikili dosyaları güncelleştirmek güncelleştirme modülü çalışırsa, güncelleştirme modül, sorunu işlemleri tanımlayan ve güncelleştirme modülü işlemleri durdurduktan sonra yeniden denemek için kullanıcıya bildirir bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="76efe-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="76efe-115">Güncelleştirme modülü bir modül güncelleştirdiğinde eski ve yeni sürümleri artık yana birimi aynı dizinde; bu nedenle PowerShell 5.0 veya daha yeni sürümleri, bu modülü en son (veya belirtilen) sürümü ekler.</span><span class="sxs-lookup"><span data-stu-id="76efe-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="76efe-116">Bunu söyleyin ve bu komutların çıktısı örneği göstermek için yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="76efe-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="76efe-117">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76efe-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="76efe-118">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="76efe-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="76efe-119">Güncelleştirme Modülü</span><span class="sxs-lookup"><span data-stu-id="76efe-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="76efe-120">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="76efe-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="76efe-121">Bir ön sürümüyle modülü güncelleştirme, - AllowPrerelease bayrağı gerektirir</span><span class="sxs-lookup"><span data-stu-id="76efe-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="76efe-122">TestDepWithNestedRequiredModules1 modülü bağımlılıkları ile güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="76efe-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```