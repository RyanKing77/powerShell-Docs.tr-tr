---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a>Sorun giderme cmdlet'leri

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Nasıl çözümleneceğini "Uyarı: 'paket adı,' paketi yükleyemedi" sorunu?

Modül yükleme veya güncelleştirme modülü bazen bazı makinelerde başarısız olduğunu bildirilir.
Araştırmamıza göre bunu ağ bağlantısı yapmak için bir şeydir.
Yakın zamanda, güvenilir bir şekilde paketleri indirebilmesi biz NuGet sağlayıcı güncelleştirildi.
NuGet Sağlayıcısı'nın en son sürüme yükleyin ve ardından yüklemek veya modülünüzün güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.
Şimdi 'Azure' modülü bir örnek olarak kullanabilirsiniz.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```