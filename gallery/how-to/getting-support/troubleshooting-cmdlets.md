---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084190"
---
# <a name="troubleshooting-cmdlets"></a>Sorun giderme cmdlet'leri

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Nasıl çözümleneceğini "Uyarı: Paket 'paket adı' karşıdan yüklenemedi"sorun

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
