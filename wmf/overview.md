---
ms.date: 06/12/2018
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940397"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF), Windows için bir tutarlı yönetim arabirimini sağlar. WMF çeşitli Windows istemcisi ve Windows Server sürümlerini yönetmek için sorunsuz bir yol sağlar. WMF Installer paketleri yönetim işlevselliği için güncelleştirmeleri içerir ve daha eski Windows sürümleri için kullanılabilir.

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

|İşletim sistemi sürümü  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2016       |Yerleşik gelir|            |            |             |            |
|Windows 10                |Yerleşik gelir|Yerleşik gelir|            |             |            |
|Windows Server 2012 R2    |Evet         |Evet         |Yerleşik gelir|             |            |
|Windows 8.1               |Evet         |Evet         |Yerleşik gelir|             |            |
|Windows Server 2012       |Evet         |Evet         |Evet         |Yerleşik gelir |            |
|Windows 8                 |            |            |            |Yerleşik gelir |            |
|Windows Server 2008 R2 SP1|Evet         |Evet         |Evet         |Evet          |Yerleşik gelir|
|Windows 7 SP1             |Evet         |Evet         |Evet         |Evet          |Yerleşik gelir|
|Windows Server 2008 SP2   |            |            |            |Evet          |Evet         |
|Windows Vista             |            |            |            |             |Evet         |
|Windows Server 2003       |            |            |            |             |Evet         |
|Windows XP                |            |            |            |Evet          |            |

**Gelen Kutusu**: WMF belirtilen sürümünü özelliklerini belirtilen Windows istemci veya Windows Server sürümünde geldiği.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
