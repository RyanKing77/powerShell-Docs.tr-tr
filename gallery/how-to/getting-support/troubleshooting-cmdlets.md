---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892483"
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