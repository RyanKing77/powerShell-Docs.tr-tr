---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Kaldırma Modülü
ms.openlocfilehash: 90f26e64a8a6bc95faf444b1d3ce82a8e3bbefc1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-module"></a><span data-ttu-id="e8194-103">Kaldırma Modülü</span><span class="sxs-lookup"><span data-stu-id="e8194-103">Uninstall-Module</span></span>

<span data-ttu-id="e8194-104">PowerShellGet cmdlet'leri kullanılarak yüklenmiş bir modül kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e8194-104">Uninstalls a module which was installed using PowerShellGet cmdlets.</span></span>

## <a name="description"></a><span data-ttu-id="e8194-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8194-105">Description</span></span>

<span data-ttu-id="e8194-106">Uninstall-modül cmdlet Belirtilen modül yerel bilgisayardan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e8194-106">The Uninstall-Module cmdlet uninstalls the specified module from the local computer.</span></span>
<span data-ttu-id="e8194-107">Bazı diğer modüller üzerinde bir bağımlılık varsa, bir modül kaldıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="e8194-107">You cannot uninstall a module if some other modules have a dependency on it.</span></span>
<span data-ttu-id="e8194-108">Kaldırma modülü cmdlet'leri ayrıca kaldırılıyor modülü kullanımda olup olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="e8194-108">The Uninstall-Module cmdlets also validates if the module being uninstalled is in-use or not.</span></span> <span data-ttu-id="e8194-109">Modül kullanılıyorsa bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e8194-109">An error will be thrown if the module is in use.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="e8194-110">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8194-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Uninstall-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="e8194-111">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="e8194-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="e8194-112">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="e8194-112">Uninstall-Module</span></span>](http://go.microsoft.com/fwlink/?LinkId=526864)


## <a name="example-commands"></a><span data-ttu-id="e8194-113">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="e8194-113">Example commands</span></span>

###  <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a><span data-ttu-id="e8194-114">PowerShellGet kullanarak yüklü bir modül kaldırmak için Uninstall-Module cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e8194-114">Run the Uninstall-Module cmdlet to uninstall a module that you installed by using PowerShellGet.</span></span>
<span data-ttu-id="e8194-115">Silmek istediğiniz modülü üzerinde başka bir modül bağımlı olması durumunda, PowerShellGet bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8194-115">If any other module depends on the module that you want to delete, PowerShellGet throws an error.</span></span>
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

### <a name="uninstalling-a-module-when-some-other-modules-have-a-dependency-on-it"></a><span data-ttu-id="e8194-116">Bazı diğer modüller üzerinde bir bağımlılık olduğunda bir modül kaldırılıyor.</span><span class="sxs-lookup"><span data-stu-id="e8194-116">Uninstalling a module when some other modules have a dependency on it.</span></span>

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\ProgramFiles\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.3\PSModule.psm1:1803 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

### <a name="you-can-override-this-by-specify--force-option-on-uninstall-module-cmdlet"></a><span data-ttu-id="e8194-117">Bu geçersiz kılma tarafından belirtin - Force seçeneği kaldırma modül cmdlet hakkında</span><span class="sxs-lookup"><span data-stu-id="e8194-117">You can override this by specify -Force option on Uninstall-Module cmdlet</span></span>
<span data-ttu-id="e8194-118">**Not:** bu önerilen bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="e8194-118">**NOTE:** This is not a recommended practice.</span></span> <span data-ttu-id="e8194-119">Diğer modüller Bu eylemle çalışmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e8194-119">Other modules will break with this action.</span></span>

```powershell
Uninstall-Module SnippetPx -Force
```

### <a name="uninstall-a-module-which-is-already-in-use"></a><span data-ttu-id="e8194-120">Zaten kullanımda olan bir modül kaldırma</span><span class="sxs-lookup"><span data-stu-id="e8194-120">Uninstall a module which is already in use</span></span>

```powershell
Get-InstalledModule TypePx,SnippetPx

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experi...
```

### <a name="uninstall-snippetpx-fails-due-to-the-dependent-module"></a><span data-ttu-id="e8194-121">Bağımlı modül nedeniyle SnippetPx başarısız kaldırma</span><span class="sxs-lookup"><span data-stu-id="e8194-121">Uninstall SnippetPx fails due to the dependent module</span></span>

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx'
are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

### <a name="uninstall-typepx-then-uninstall-the-snippetpx"></a><span data-ttu-id="e8194-122">TypePx kaldırın ve sonra SnippetPx kaldırma</span><span class="sxs-lookup"><span data-stu-id="e8194-122">Uninstall TypePx then uninstall the SnippetPx</span></span>

```powershell
Uninstall-Module TypePx
Uninstall-Module SnippetPx

WARNING: The version '1.0.5.18' of module 'SnippetPx' is currently in use. Retry the operation after closing the
applications.
PackageManagement\Uninstall-Package : Module 'SnippetPx' is in currently in use.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : ModuleIsInUse,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.Uninstall
   Package
```


### <a name="for-a-module-name-which-is-not-installed-using-powershellget-cmdlets"></a><span data-ttu-id="e8194-123">Modül adı için hangi PowerShellGet cmdlet'lerini kullanarak yüklü değil</span><span class="sxs-lookup"><span data-stu-id="e8194-123">For a module name which is not installed using PowerShellGet cmdlets</span></span>

```powershell
Uninstall-Module SnipptPx

PackageManagement\Uninstall-Package : No match was found for the specified search criteria and module names 'SnipptPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package]
   , Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```