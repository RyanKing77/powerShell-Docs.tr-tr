---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: WMF 5.1 Sürüm Notları
ms.openlocfilehash: eb22267c1af28a9fcdd049c76d363fff687f6167
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Windows Management Framework (WMF) 5.1 sürüm notları #

WMF 5.1, Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve yazılım envanteri günlüğü (SIL) bileşenleri içerir.
WMF 5.1; Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2’ye yüklenebilir ve WMF 5.0 RTM’ye şu gibi iyileştirmeler getirir:

- Yeni cmdlet’ler: yerel kullanıcılar ve gruplar; Get-ComputerInfo
- PowerShellGet iyileştirmeleri arasında imzalı modülleri zorlama ve JEA modülleri yükleme bulunur
- PackageManagement; Kapsayıcılar, CBS Kurulumu, EXE temelli kurulum ve CAD paketleri için destek ekledi
- DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri
- PowerShellGet cmdlet’leri kullanırken Çekme Sunucusundan gelen katalog imzalı modülleri zorlamayı da içeren güvenlik iyileştirmeleri
- Birkaç kullanıcı talebi ve sorununa yanıt

**Önemli Notlar:**

- **WMF 5.1 için .NET Framework 4.5.2** (veya üstü). Yükleme başarılı olur, ancak temel özellikleri başarısız olur, .NET 4.5.2 (veya üstü) yüklü değil. Yönergeler bulunan [yükleme ve yapılandırma WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) konu.
- 5.1 WMF RTM yüklenmeden önce WMF 5.1 önizleme kaldırılması gerekir.
- WMF 5.1 doğrudan WMF 5.0 veya WMF 4.0 üzerinden yüklenebilir.
- Bu __gerekli değil__ WMF 5.1 Windows 7 ve Windows Server 2008 R2 yüklenmeden önce WMF 4.0 sürümünü yüklemek için. WMF 5.1 önizleme sürümü için bir sorun oluştu ve çözümlendi.