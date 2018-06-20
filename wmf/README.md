---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: ae50e8d1495d7075163714ed873940d2d1d19b8e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221876"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) Windows ve Windows Server çeşitli özellikleri arasında tutarlı yönetim arabirimi sağlayan teslim mekanizmadır.
WMF yükleme ile müşterileri arasında İşletim Sistemleri'ni bileşimleri ortamlarında çalışmasını sorunsuz bir şekilde alın.
WMF güncelleştirmeleri Windows ve Windows Server, verilen sürümündeki Yönetim işlevselliği için daha düşük sürümleri (genellikle 2 düşük sürümler) Windows ve Windows Server yükleme için kullanılabilir hale getirir.

WMF yüklemesi ekler ve/veya aşağıdaki özellikleri güncelleştirir:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell Tümleşik komut dosyası ortamı (ISE)
- Windows Uzaktan Yönetim (WinRM)
- Windows Yönetim Araçları (WMI)
- Windows PowerShell Web Hizmetleri (Yönetim OData IIS uzantısı)
- Yazılım Envanter Günlüğü (SIL)
- Sunucu Yöneticisi'ni CIM sağlayıcısı

## <a name="wmf-release-notes"></a>WMF sürüm notları

PowerShell ve diğer bileşenleri verilen WMF çeşitli iyileştirmeleri hakkında bilgi edinmek için aşağıdaki bağlantılardan sürüm notlarını gözden geçirmek için lütfen:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Windows işletim sistemleri içinde WMF kullanılabilirliği

| İşletim sistemi sürümü | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Yerleşik gelir |  |  |  |  |
| Windows 10 | Yerleşik gelir | Yerleşik gelir  | | | |
| Windows Server 2012 R2| Evet | Evet | Yerleşik gelir |  |  |
| Windows 8.1 | Evet | Evet |  Yerleşik gelir |  |  |
| Windows Server 2012 | Evet | Evet | Evet |  Yerleşik gelir | |
| Windows 8 |  |  |  | Yerleşik gelir | |
| Windows Server 2008 R2 SP1 | Evet | Evet | Evet |  Evet| Yerleşik gelir |
| Windows 7 SP1  | Evet | Evet | Evet | Evet | Yerleşik gelir |
| Windows Server 2008 SP2 | | | | Evet | Evet |
| Windows Vista | | | | | Evet |
| Windows Server 2003| | | |  | Evet |
| Windows XP | | | |  | Evet |

**"Gelen kutusu"**: özelliklerini `specified WMF` belirtilen Windows ve Windows Server sürümünde geldiği.
Bu nedenle, `specified WMF` belirtilen işletim sistemi sürümlerinde yüklü olması gerekmez.
