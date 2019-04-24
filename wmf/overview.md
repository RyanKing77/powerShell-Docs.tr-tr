---
ms.date: 04/19/2019
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: 6d25b4025bbc86f6be0e5c74db9f1fbe6705d816
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984330"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) Windows için bir tutarlı yönetim arabirimidir. WMF sorunsuz Windows istemcisi ve Windows Server çeşitli sürümlerini yönetmenize olanak sağlar. WMF yükleyici paket Yönetimi işlevselliği için güncelleştirmeleri içerir ve eski Windows sürümleri için kullanılabilir.

WMF yükleme ekler ve/veya aşağıdaki özellikleri güncelleştirir:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell Tümleşik komut dosyası ortamı (ISE)
- Windows Uzaktan Yönetim (WinRM)
- Windows Yönetim Araçları (WMI)
- Windows PowerShell Web Hizmetleri (Management OData IIS uzantısı)
- Yazılım Envanter Günlüğü (SIL)
- Sunucu Yöneticisi'ni CIM sağlayıcısı

## <a name="wmf-release-notes"></a>WMF sürüm notları

PowerShell ve diğer bileşenleri verilen WMF çeşitli iyileştirmeler hakkında bilgi edinmek için aşağıdaki bağlantıları sürüm notlarını gözden geçirmek için bkz:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Windows işletim sistemleri içinde WMF kullanılabilirliği

|        İşletim Sistemi Sürümü         | [WMF 5.1][]  | WMF 5.0<br>*Destek kapsamı dışında* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Yerleşik verilir |                             |              |              |              |
| Windows Server 2016                     | Yerleşik verilir |                             |              |              |              |
| Windows 10                              | Yerleşik verilir | Yerleşik verilir                |              |              |              |
| Windows Server 2012 R2                  | Evet          | Evet                         | Yerleşik verilir |              |              |
| Windows 8.1                             | Evet          | Evet                         | Yerleşik verilir |              |              |
| Windows Server 2012                     | Evet          | Evet                         | Evet          | Yerleşik verilir |              |
| Windows 8<br>*Destek kapsamı dışında*           |              |                             |              | Yerleşik verilir |              |
| Windows Server 2008 R2 SP1              | Evet          | Evet                         | Evet          | Evet          | Yerleşik verilir |
| Windows 7 SP1                           | Evet          | Evet                         | Evet          | Evet          | Yerleşik verilir |
| Windows Server 2008 SP2                 |              |                             |              | Evet          | Evet          |
| Windows Vista<br>*Destek kapsamı dışında*       |              |                             |              |              | Evet          |
| Windows Server 2003<br>*Destek kapsamı dışında* |              |                             |              |              | Evet          |
| Windows XP<br>*Destek kapsamı dışında*          |              |                             |              | Evet          | Evet          |

- **Gelen Kutusu**: Belirtilen WMF sürümünü özelliklerinin belirtilen Windows istemci veya Windows Server sürümünde geldiği.
- **Destek dışında**: Bu ürünler artık Microsoft tarafından desteklenir. Desteklenen yeni bir sürüme yükseltmeniz gerekir. Daha fazla bilgi için [Microsoft Destek Ömrü İlkesi][] sayfası.

> [!NOTE]
> WMF 5.0 yükleyici artık desteklenen veya kullanılabilir değil. WMF 5.1 tarafından değiştirilmiştir.

[Microsoft Destek Ömrü İlkesi]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
