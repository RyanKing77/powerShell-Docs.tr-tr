---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery, psget
title: PowerShell Galerisi
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a>PowerShell Galerisi

PowerShell Galerisi PowerShell içerik için merkezi depodur. Galeriden yeni PowerShell komutlarını ya da istenen durum Yapılandırması'nı (DSC) kaynakları bulabilirsiniz.

## <a name="powershellget-overview"></a>PowerShellGet genel bakış

PowerShellGet modülü bulmak, yükleme, güncelleştirme ve modülleri, DSC kaynakları, rol özellikleri ve komut dosyalarından gibi PowerShell yapılarını yayımlama yönelik cmdlet'ler içeren [PowerShell Galerisi](https://www.PowerShellGallery.com) ve diğer özel depoları.

## <a name="getting-started-with-the-gallery"></a>Galerisi'ni kullanmaya başlama

Galeriden öğelerini yüklemesi, Windows 10, Windows Management Framework (WMF) 5.0 içinde veya MSI tabanlı Yükleyicisi (PowerShell 3. ve 4) kullanılabilir PowerShellGet modülünün en son sürümünü gerektirir.

- [**Windows 10 alma**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**WMF 5.0 alma**](http://go.microsoft.com/fwlink/?LinkId=398175), veya
- [**MSI yükleyicisi Al**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

En son [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modülü, şunları yapabilirsiniz:

-   Arama ile galeri öğeleri aracılığıyla [bulma Modülü](https://go.microsoft.com/fwlink/?LinkId=821658) ve [bulma komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Öğeleri ile galerisinden sisteminize kaydetmek [Kaydet-Module](https://go.microsoft.com/fwlink/?LinkId=821669) ve [Kaydet-komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Öğeleri ile galerisinden yüklemeyi [yükleme-Module](https://go.microsoft.com/fwlink/?LinkId=821663) ve [yükleme betiği](https://go.microsoft.com/fwlink/?LinkId=822327)
-   İle galeri öğeleri karşıya [Yayımla-Module](https://go.microsoft.com/fwlink/?LinkId=821666) ve [Yayımla-komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Kendi özel deposuyla eklemek [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Kullanıma [Başlarken](psgallery/psgallery_gettingstarted.md) PowerShellGet komutları Galerisi ile kullanma hakkında daha fazla bilgi için. De çalıştırabilirsiniz *Update-Help-modülü PowerShellGet* bu komutları için yerel Yardım yüklemek için.

## <a name="supported-operating-systems"></a>Desteklenen işletim sistemleri

**PowerShellGet** modülü gerektirir **PowerShell 3.0 veya daha yeni**.

Bu nedenle, **PowerShellGet** aşağıdaki işletim sistemlerinden birini gerektirir:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** de .NET Framework 4.5 gerektirir veya üstü. .NET Framework 4.5 yükleyebilirsiniz ya da yukarıdaki gelen [burada](https://msdn.microsoft.com/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>Bir soru var mı? Geri bildirim var mı?

PowerShell Galerisi ve PowerShellGet hakkında daha fazla bilgi bulunabilir [Başlarken](psgallery/psgallery_gettingstarted.md) sayfası. Kullanarak geri bildirim ve rapor sorunlarını lütfen [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).

