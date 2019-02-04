---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: PowerShellGet yükleme
ms.openlocfilehash: 5c51cb1c7ea2538cc5f8503ce6c5d80edda70e15
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683880"
---
# <a name="installing-powershellget"></a><span data-ttu-id="1c15e-103">PowerShellGet yükleme</span><span class="sxs-lookup"><span data-stu-id="1c15e-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="1c15e-104">PowerShellGet aşağıdaki sürümlerden bir yerleşik modüldür</span><span class="sxs-lookup"><span data-stu-id="1c15e-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="1c15e-105">[Windows 10](https://www.microsoft.com/windows) ya da daha yeni</span><span class="sxs-lookup"><span data-stu-id="1c15e-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="1c15e-106">[Windows Server 2016](/windows-server/windows-server) ya da daha yeni</span><span class="sxs-lookup"><span data-stu-id="1c15e-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="1c15e-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ya da daha yeni</span><span class="sxs-lookup"><span data-stu-id="1c15e-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="1c15e-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="1c15e-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="1c15e-109">PowerShell sürüm 3.0 ve 4.0 için PowerShellGet modülü Al</span><span class="sxs-lookup"><span data-stu-id="1c15e-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="1c15e-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="1c15e-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="1c15e-111">PowerShell Galerisi'nden en son sürümü Al</span><span class="sxs-lookup"><span data-stu-id="1c15e-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="1c15e-112">PowerShellGet güncelleştirmeden önce her zaman en son Nuget sağlayıcısı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c15e-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="1c15e-113">Bunu yapmak için yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c15e-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="1c15e-114">PowerShell 5.0 (veya daha yeni) sistemleri için en son PowerShellGet yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c15e-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="1c15e-115">Windows 10'da bunu yapmak için Windows Server 2016, herhangi bir sistemle WMF 5.0 veya yüklü 5.1 veya PowerShell 6 ile herhangi bir sistem çalıştırmak aşağıdaki komutları yükseltilmiş bir PowerShell oturumundan.</span><span class="sxs-lookup"><span data-stu-id="1c15e-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="1c15e-116">Kullanım `Update-Module` daha yeni sürümlerini almak için.</span><span class="sxs-lookup"><span data-stu-id="1c15e-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="1c15e-117">PowerShell 3 veya PowerShell 4 çalıştıran sistemlerde, yüklü [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="1c15e-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="1c15e-118">PowerShellGet cmdlet'ini yükseltilmiş bir PowerShell oturumunda aşağıdaki modüller, yerel bir dizine kaydetmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="1c15e-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="1c15e-119">Tüm diğer işlemler PowerShellGet ve PackageManagment modülleri yüklü değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c15e-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="1c15e-120">İçeriğini silin `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` ve `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` klasörleri.</span><span class="sxs-lookup"><span data-stu-id="1c15e-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="1c15e-121">PS konsolunda yükseltilmiş izinlerle yeniden açın, ardından aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c15e-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
