---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: PowerShellGet yükleme
ms.openlocfilehash: 23a53a9117c9f6a7ad157b635cd7ff4b3b3444c5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054841"
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

- PowerShellGet ve PackageManagement modüllerini tüm diğer işlemler yüklenmeyen emin olun.
- İçeriğini silin `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` ve `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` klasörleri.
- PS konsolunda yükseltilmiş izinlerle yeniden açın, ardından aşağıdaki komutları çalıştırın.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
