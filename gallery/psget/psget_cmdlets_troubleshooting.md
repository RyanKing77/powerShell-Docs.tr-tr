---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
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