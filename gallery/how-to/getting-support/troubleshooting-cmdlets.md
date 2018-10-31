---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002471"
---
# <a name="troubleshooting-cmdlets"></a>Sorun giderme cmdlet'leri

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Nasıl çözümleneceğini "Uyarı: ', paket adı' paket başarısız indirmek" sorun

Bu rapor, `Install-Module` veya `Update-Module` bazen bazı makinelerde başarısız olur.
Araştırmamıza göre bunu ağ bağlantısı ile yapmak için bir şeydir.
Güvenilir bir şekilde paketleri indirebilmeniz en son NuGet sağlayıcısı güncelleştirdik.
NuGet sağlayıcısı en son derlemesini yüklemek ve yüklemeyi veya modülünüzde güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.
Şimdi 'Azure' modülü bir örnek olarak kullanın.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
