---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell 32 Bit sürümü başlatılıyor"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>Windows PowerShell 32-Bit sürümünü başlatılıyor
64-bit bir bilgisayarda, Windows PowerShell yüklediğinizde **Windows PowerShell (x86)**, Windows PowerShell 32-bit sürümünü yanı sıra 64-bit sürümü yüklü. Windows PowerShell çalıştırdığınızda, varsayılan olarak 64-bit sürümünü çalıştırır.

Ancak, bazen çalıştırmanız gerekebilir **Windows PowerShell (x86)**gibi bir Modülü'nü kullanırken 32-bit sürümünü gerektirir veya, bir 32 bit bilgisayara uzaktan bağlanıyorsanız olduğunda.

Windows PowerShell 32-bit sürümünü başlatmak için aşağıdaki yordamlardan birini kullanın.

#### <a name="in-windows-server-2012-r2"></a>Windows Server® 2012 R2'de

- Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**. Tıklatın **Windows PowerShell x86** döşeme.

- İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.

- Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.

- Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>Windows Server® 2012

- Üzerinde **Başlat** ekranında, yazın **PowerShell** ve ardından **Windows PowerShell (x86)**.

- İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.

- Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell** ve ardından **Windows PowerShell (x86)**.

- Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>Windows® 8.1

- Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**. Tıklatın **Windows PowerShell x86** döşeme.

- Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://go.microsoft.com/fwlink/?LinkID=304145) Windows 8.1 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü. Seçin **Windows PowerShell (x86)**.

- Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.
   
- Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>Windows® 8

- Üzerinde **Başlat** ekranında, imleci için sağ üst köşesindeki taşıma, tıklatın **ayarları**, tıklatın **döşeme**ve ardından taşıma **Yönetimsel Araçları Göster** kaydırıcı Evet. Ardından, yazın **PowerShell** tıklatıp **Windows PowerShell (x86)**.

- Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://www.microsoft.com/download/details.aspx?id=28972) Windows 8 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü. Seçin **Windows PowerShell (x86)**.

- Üzerinde **Başlat** ekran veya yazın, Masaüstü **PowerShell (x86)** ve ardından **Windows PowerShell (x86)**.

- Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

