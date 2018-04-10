---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: PowerShellGet Modülü Al
ms.openlocfilehash: a392f795d8c065ff881bc6cc113e63a1f18bcb44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
<a name="get-powershellget-module"></a><span data-ttu-id="b23d4-103">PowerShellGet Modülü Al</span><span class="sxs-lookup"><span data-stu-id="b23d4-103">Get PowerShellGet Module</span></span>
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="b23d4-104">PowerShellGet aşağıdaki sürümlerden bir yerleşik modülüdür.</span><span class="sxs-lookup"><span data-stu-id="b23d4-104">PowerShellGet is an in-box module in the following releases</span></span>
- <span data-ttu-id="b23d4-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) ya da daha yeni</span><span class="sxs-lookup"><span data-stu-id="b23d4-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="b23d4-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) ya da daha yeni</span><span class="sxs-lookup"><span data-stu-id="b23d4-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="b23d4-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ya da daha yeni</span><span class="sxs-lookup"><span data-stu-id="b23d4-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="b23d4-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="b23d4-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="b23d4-109">PowerShell sürüm 3.0 ve 4.0 için PowerShellGet modülü Al</span><span class="sxs-lookup"><span data-stu-id="b23d4-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>
- [<span data-ttu-id="b23d4-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="b23d4-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

### <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="b23d4-111">PowerShell Galerisi'nden en son sürümünü alın</span><span class="sxs-lookup"><span data-stu-id="b23d4-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="b23d4-112">PowerShellGet güncelleştirmeden önce her zaman son Nuget sağlayıcı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b23d4-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="b23d4-113">Bunu yapmak için yükseltilmiş bir PowerShell oturumunda aşağıdakini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b23d4-113">To do that, run the following in an elevated PowerShell session.</span></span>
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="b23d4-114">PowerShell 5.0 (veya daha yeni) sistemler için en son PowerShellGet yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b23d4-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>
- <span data-ttu-id="b23d4-115">Bu Windows 10'yapmak için Windows Server 2016, WMF 5.0 yüklü olan tüm sistemler veya yüklü 5.1 veya PowerShell 6 ile tüm sistem çalıştırın aşağıdaki komutları yükseltilmiş bir PowerShell oturumundan.</span><span class="sxs-lookup"><span data-stu-id="b23d4-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="b23d4-116">Daha yeni sürümlerini almak için güncelleştirmeyi modülü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b23d4-116">Use Update-Module to get newer versions.</span></span>
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="b23d4-117">PowerShell 3 veya PowerShell 4 çalıştıran sistemler için yüklü olan [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="b23d4-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="b23d4-118">Yerel bir dizine modülleri kaydetmek için aşağıdaki PowerShellGet cmdlet'i yükseltilmiş bir PowerShell oturumunda kullanın</span><span class="sxs-lookup"><span data-stu-id="b23d4-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="b23d4-119">Başka bir işlem içinde PowerShellGet ve PackageManagment modülleri yüklü değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="b23d4-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="b23d4-120">İçeriğini silin `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` ve `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` klasörler.</span><span class="sxs-lookup"><span data-stu-id="b23d4-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="b23d4-121">Yükseltilmiş izinleri olan PS konsolunu yeniden açın, ardından aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b23d4-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```