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
# <a name="installing-powershellget"></a>PowerShellGet yükleme

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet, aşağıdaki sürümlerde yerleşik bir modüldür

- [Windows 10](https://www.microsoft.com/windows) veya üzeri
- [Windows Server 2016](/windows-server/windows-server) veya üzeri
- [Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) veya üzeri
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>PowerShell sürümleri 3,0 ve 4,0 için PowerShellGet modülünü alın

- [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>PowerShell Galerisi en son sürümü Al

- PowerShellGet 'i güncelleştirmeden önce en son NuGet sağlayıcısını her zaman yüklemelisiniz. Bunu yapmak için, yükseltilmiş bir PowerShell oturumunda aşağıdakileri çalıştırın.

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>PowerShell 5,0 (veya daha yeni) olan sistemler için en son PowerShellGet 'i yükleyebilirsiniz

- Bunu Windows 10, Windows Server 2016, WMF 5,0 veya 5,1 yüklü herhangi bir sisteme veya PowerShell 6 ile herhangi bir sisteme sahip olmak için, yükseltilmiş bir PowerShell oturumundan aşağıdaki komutları çalıştırın.

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- Daha `Update-Module` yeni sürümleri almak için kullanın.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>[Package Management MSI](https://www.microsoft.com/download/details.aspx?id=51451) ' yi yükleyen PowerShell 3 veya PowerShell 4 çalıştıran sistemler için

- Modülleri yerel bir dizine kaydetmek için yükseltilmiş bir PowerShell oturumundan PowerShellGet cmdlet 'ini kullanın

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- PowerShellGet ve PackageManagement modüllerinin başka bir işlemde yüklenmediğinden emin olun.
- `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` Ve`$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` klasörlerinin içeriğini silin.
- PS konsolunu yükseltilmiş izinlerle yeniden açın ve aşağıdaki komutları çalıştırın.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
