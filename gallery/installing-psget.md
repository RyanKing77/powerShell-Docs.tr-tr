---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: PowerShellGet yükleme
ms.openlocfilehash: 6190c7caee61b43e70073ff7b30f867a901d3042
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="get-powershellget-module"></a>PowerShellGet modülü Al

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet aşağıdaki sürümlerden bir yerleşik modülüdür.

- [Windows 10](https://www.microsoft.com/windows/get-windows-10) ya da daha yeni
- [Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) ya da daha yeni
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ya da daha yeni
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>PowerShell sürüm 3.0 ve 4.0 için PowerShellGet modülü Al

- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a>PowerShell Galerisi'nden en son sürümünü alın

- PowerShellGet güncelleştirmeden önce her zaman son Nuget sağlayıcı yüklemeniz gerekir. Bunu yapmak için yükseltilmiş bir PowerShell oturumunda aşağıdakini çalıştırın.

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>PowerShell 5.0 (veya daha yeni) sistemler için en son PowerShellGet yükleyebilirsiniz.

- Bu Windows 10'yapmak için Windows Server 2016, WMF 5.0 yüklü olan tüm sistemler veya yüklü 5.1 veya PowerShell 6 ile tüm sistem çalıştırın aşağıdaki komutları yükseltilmiş bir PowerShell oturumundan.

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Daha yeni sürümlerini almak için güncelleştirmeyi modülü kullanın.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>PowerShell 3 veya PowerShell 4 çalıştıran sistemler için yüklü olan [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Yerel bir dizine modülleri kaydetmek için aşağıdaki PowerShellGet cmdlet'i yükseltilmiş bir PowerShell oturumunda kullanın

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Başka bir işlem içinde PowerShellGet ve PackageManagment modülleri yüklü değil emin olun.
- İçeriğini silin `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` ve `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` klasörler.
- Yükseltilmiş izinleri olan PS konsolunu yeniden açın, ardından aşağıdaki komutları çalıştırın.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```