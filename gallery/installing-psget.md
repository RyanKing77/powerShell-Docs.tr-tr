---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, PowerShell, cmdlet, psget
title: PowerShellGet yükleme
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601425"
---
# <a name="installing-powershellget"></a><span data-ttu-id="7565f-103">PowerShellGet yükleme</span><span class="sxs-lookup"><span data-stu-id="7565f-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="7565f-104">PowerShellGet, aşağıdaki sürümlerde yerleşik bir modüldür</span><span class="sxs-lookup"><span data-stu-id="7565f-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="7565f-105">[Windows 10](https://www.microsoft.com/windows) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="7565f-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="7565f-106">[Windows Server 2016](/windows-server/windows-server) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="7565f-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="7565f-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="7565f-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="7565f-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="7565f-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="7565f-109">PowerShell sürümleri 3,0 ve 4,0 için PowerShellGet modülünü alın</span><span class="sxs-lookup"><span data-stu-id="7565f-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="7565f-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="7565f-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="7565f-111">PowerShell Galerisi en son sürümü Al</span><span class="sxs-lookup"><span data-stu-id="7565f-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="7565f-112">PowerShellGet 'i güncelleştirmeden önce en son NuGet sağlayıcısını her zaman yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7565f-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="7565f-113">Bunu yapmak için, yükseltilmiş bir PowerShell oturumunda aşağıdakileri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7565f-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="7565f-114">PowerShell 5,0 (veya daha yeni) olan sistemler için en son PowerShellGet 'i yükleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="7565f-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="7565f-115">Bunu Windows 10, Windows Server 2016, WMF 5,0 veya 5,1 yüklü herhangi bir sisteme veya PowerShell 6 ile herhangi bir sisteme sahip olmak için, yükseltilmiş bir PowerShell oturumundan aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7565f-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- <span data-ttu-id="7565f-116">Daha `Update-Module` yeni sürümleri almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7565f-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="7565f-117">[Package Management MSI](https://www.microsoft.com/download/details.aspx?id=51451) ' yi yükleyen PowerShell 3 veya PowerShell 4 çalıştıran sistemler için</span><span class="sxs-lookup"><span data-stu-id="7565f-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="7565f-118">Modülleri yerel bir dizine kaydetmek için yükseltilmiş bir PowerShell oturumundan PowerShellGet cmdlet 'ini kullanın</span><span class="sxs-lookup"><span data-stu-id="7565f-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="7565f-119">PowerShellGet ve PackageManagement modüllerinin başka bir işlemde yüklenmediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7565f-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="7565f-120">`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` Ve`$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` klasörlerinin içeriğini silin.</span><span class="sxs-lookup"><span data-stu-id="7565f-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="7565f-121">PS konsolunu yükseltilmiş izinlerle yeniden açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7565f-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
