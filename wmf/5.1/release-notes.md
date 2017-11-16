---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: "WMF 5.1 sürüm notları"
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Windows Management Framework (WMF) 5.1 sürüm notları #

WMF 5.1, Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve yazılım envanteri günlüğü (SIL) bileşenleri içerir.
WMF 5.1 yüklenebilmesi için Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2 ve WMF 5.0 RTM dahil olmak üzere üzerinden bazı geliştirmeler sağlar:

- Yeni cmdlet'leri: yerel kullanıcılar ve gruplar; Get-ComputerInfo
- PowerShellGet geliştirmeler imzalı modülleri, zorlama ve JEA modülleri yükleme
- PackageManagement kapsayıcıları, CBS Kurulum EXE tabanlı Kurulum, CAB paketleri için destek eklendi
- DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri
- Zorlama PowerShellGet cmdlet'lerini kullanırken çekme sunucudan gelen ve gelen katalog imzalı modüllerin dahil olmak üzere güvenlik geliştirmeleri
- Çok sayıda kullanıcı isteklerini ve sorunları yanıtlarını

**Önemli Notlar:**

- **WMF 5.1 için .NET Framework 4.5.2** (veya üstü). Yükleme başarılı olur, ancak temel özellikleri başarısız olur, .NET 4.5.2 (veya üstü) yüklü değil. Yönergeler bulunan [yükleme ve yapılandırma WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) konu.
- 5.1 WMF RTM yüklenmeden önce WMF 5.1 önizleme kaldırılması gerekir.
- WMF 5.1 doğrudan WMF 5.0 veya WMF 4.0 üzerinden yüklenebilir.
- Bu __gerekli değil__ WMF 5.1 Windows 7 ve Windows Server 2008 R2 yüklenmeden önce WMF 4.0 sürümünü yüklemek için. WMF 5.1 önizleme sürümü için bir sorun oluştu ve çözümlendi.  


