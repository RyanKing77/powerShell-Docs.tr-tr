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
# <a name="installing-powershellget"></a>PowerShellGet yükleme

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet aşağıdaki sürümlerden bir yerleşik modüldür

- [Windows 10](https://www.microsoft.com/windows) ya da daha yeni
- [Windows Server 2016](/windows-server/windows-server) ya da daha yeni
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ya da daha yeni
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>PowerShell sürüm 3.0 ve 4.0 için PowerShellGet modülü Al

- [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>PowerShell Galerisi'nden en son sürümü Al

- PowerShellGet güncelleştirmeden önce her zaman en son Nuget sağlayıcısı yüklemeniz gerekir. Bunu yapmak için yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırın.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>PowerShell 5.0 (veya daha yeni) sistemleri için en son PowerShellGet yükleyebilirsiniz.

- Windows 10'da bunu yapmak için Windows Server 2016, herhangi bir sistemle WMF 5.0 veya yüklü 5.1 veya PowerShell 6 ile herhangi bir sistem çalıştırmak aşağıdaki komutları yükseltilmiş bir PowerShell oturumundan.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- Kullanım `Update-Module` daha yeni sürümlerini almak için.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>PowerShell 3 veya PowerShell 4 çalıştıran sistemlerde, yüklü [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

- PowerShellGet cmdlet'ini yükseltilmiş bir PowerShell oturumunda aşağıdaki modüller, yerel bir dizine kaydetmek için kullanın:

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Tüm diğer işlemler PowerShellGet ve PackageManagment modülleri yüklü değil emin olun.
- İçeriğini silin `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` ve `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` klasörleri.
- PS konsolunda yükseltilmiş izinlerle yeniden açın, ardından aşağıdaki komutları çalıştırın.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
