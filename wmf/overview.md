---
ms.date: 04/19/2019
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854314"
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

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
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
