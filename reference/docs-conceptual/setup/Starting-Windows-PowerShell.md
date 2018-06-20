---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows Powershell Başlatma
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953132"
---
# <a name="starting-windows-powershell"></a>Windows Powershell Başlatma
Birden çok konaklarına katıştırılmış bir komut dosyası altyapısı dll powershell'dir.  Başlatır yaygın konak etkileşimli komut satırı PowerShell.exe ve etkileşimli komut dosyası ortamı PowerShell_ISE.exe verilmiştir.

Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 ve Windows 8 Windows PowerShell® başlatmak için bkz: [genel yönetim görevleri ve gezinme](http://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Windows'un önceki sürümlerinde Windows PowerShell'i başlatma

Bu bölümde, Windows PowerShell ve Windows PowerShell Tümleşik komut dosyası ortamı (ISE) Windows® 7, Windows Server® 2008 R2 ve Windows Server® 2008 Başlat açıklanmaktadır. Ayrıca, isteğe bağlı Windows PowerShell ISE Windows PowerShell 2.0 Windows Server® 2008 R2 ve Windows Server® 2008 için nasıl etkinleştirileceğini açıklar.

Windows PowerShell 3.0 ya da Windows PowerShell 4. 0'ın yüklü sürümü uygunsa başlatmak için aşağıdaki yöntemlerden birini kullanın.

#### <a name="from-the-start-menu"></a>Başlat menüsünden

- Tıklatın **Başlat**, türü **PowerShell**ve ardından **Windows PowerShell**.
- Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Komut isteminde

Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:

```
PowerShell
```

PowerShell.exe programın parametreleri, oturum özelleştirmek için de kullanabilirsiniz. Daha fazla bilgi için bkz: [PowerShell.exe komut satırı yardımcı](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları

Tıklatın **Başlat**, türü **PowerShell**, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Önceki Windows sürümlerinde Windows PowerShell ISE başlatma

Windows PowerShell ISE başlatmak için aşağıdaki yöntemlerden birini kullanın.

#### <a name="from-the-start-menu"></a>Başlat menüsünden

- Tıklatın **Başlat**, türü **işe**ve ardından **Windows PowerShell ISE**.
- Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>Komut isteminde

Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:

```
PowerShell_ISE
```

veya

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları

Tıklatın **Başlat**, türü **işe**, sağ **Windows PowerShell ISE**ve ardından **yönetici olarak çalıştır**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Windows'un önceki sürümlerinde Windows PowerShell ISE etkinleştirme

Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell ISE tüm Windows sürümlerinde varsayılan olarak etkindir. Zaten etkin değilse, Windows Management Framework 4.0 ya da Windows Management Framework 3.0 sağlar.

Windows PowerShell 2. 0 ', Windows PowerShell ISE, Windows 7 üzerinde varsayılan olarak etkindir. Ancak, Windows Server 2008 R2 ve Windows Server 2008 üzerinde isteğe bağlı bir özelliktir.

Windows PowerShell 2.0 Windows Server 2008 R2 veya Windows Server 2008, Windows PowerShell ISE etkinleştirmek için aşağıdaki yordamı kullanın.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Tümleşik komut dosyası ortamı (ISE) etkinleştirmek için

1. Sunucu Yöneticisi'ni başlatın.
2. Tıklatın **özellikleri** ve ardından **Özellik Ekle**.
3. Özellikleri Windows PowerShell Tümleşik komut dosyası ortamı (ISE) tıklayın.

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Windows PowerShell 32-Bit sürümünü başlatılıyor

64-bit bir bilgisayarda, Windows PowerShell yüklediğinizde **Windows PowerShell (x86)**, Windows PowerShell 32-bit sürümünü yanı sıra 64-bit sürümü yüklü. Windows PowerShell çalıştırdığınızda, varsayılan olarak 64-bit sürümünü çalıştırır.

Ancak, bazen çalıştırmanız gerekebilir **Windows PowerShell (x86)** gibi bir Modülü'nü kullanırken 32-bit sürümünü gerektirir veya, bir 32 bit bilgisayara uzaktan bağlanıyorsanız olduğunda.

Windows PowerShell 32-bit sürümünü başlatmak için aşağıdaki yordamlardan birini kullanın.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**. Tıklatın **Windows PowerShell x86** döşeme.
- İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.
- Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Üzerinde **Başlat** ekranında, yazın **PowerShell** ve ardından **Windows PowerShell (x86)**.
- İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.
- Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

- Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**. Tıklatın **Windows PowerShell x86** döşeme.
- Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://go.microsoft.com/fwlink/?LinkID=304145) Windows 8.1 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü.
  Seçin **Windows PowerShell (x86)**.
- Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Üzerinde **Başlat** ekranında, imleci için sağ üst köşesindeki taşıma, tıklatın **ayarları**, tıklatın **döşeme**ve ardından taşıma **Yönetimsel Araçları Göster** kaydırıcı Evet. Ardından, yazın **PowerShell** tıklatıp **Windows PowerShell (x86)**.
- Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://www.microsoft.com/download/details.aspx?id=28972) Windows 8 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü. Seçin **Windows PowerShell (x86)**.
- Üzerinde **Başlat** ekran veya yazın, Masaüstü **PowerShell (x86)** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`