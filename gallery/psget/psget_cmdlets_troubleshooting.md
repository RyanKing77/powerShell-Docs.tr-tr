---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
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

