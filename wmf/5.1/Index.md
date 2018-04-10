---
ms.date: 08/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: WMF 5.1 Sürüm Notları
ms.openlocfilehash: 9df21afe52e79dc248871b999afead21f8678d52
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51"></a>Windows Management Framework (WMF) 5.1 #

WMF; kullanıcılara mevcut Windows sistemlerini Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve Yazılım Envanter Günlüğü (SIL) bileşenleri ile güncelleştirme imkanı verir.

WMF 5.1; Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2’ye yüklenebilir ve WMF 5.0 RTM’ye şu gibi iyileştirmeler getirir:

- Yeni cmdlet’ler: yerel kullanıcılar ve gruplar; Get-ComputerInfo
- PowerShellGet iyileştirmeleri arasında imzalı modülleri zorlama ve JEA modülleri yükleme bulunur
- PackageManagement; Kapsayıcılar, CBS Kurulumu, EXE temelli kurulum ve CAD paketleri için destek ekledi
- DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri
- PowerShellGet cmdlet’leri kullanırken Çekme Sunucusundan gelen katalog imzalı modülleri zorlamayı da içeren güvenlik iyileştirmeleri
- Birkaç kullanıcı talebi ve sorununa yanıt

Bu sürümdeki yenilikler hakkında daha fazla bilgi için [Yeni Senaryolar ve Özellikler](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features) başlığı altında listelenen konulara göz atın.

[Yükleme ve Yapılandırma](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) konusunda gereksinimler listelenmiş ve WMF yükleme yönergeleri verilmiştir.

[Uyumluluk](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) konusunda, hangi Windows sürümünde hangi WMF sürümünün yüklü olabileceği listelenmiştir.

[Ürün Uyumluluğu](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) konusunda WMF 5.1’in kullanımını henüz onaylamamış olan Microsoft uygulamaları listelenmiştir.

WMF bileşenleri hakkında ayrıntılı bilgi, MSDN belgelerinde bulunabilir:

- [PowerShell 5.1](https://docs.microsoft.com/en-us/powershell/)
- [WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)
- [WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)
- [Yazılım Envanter Günlüğü](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)