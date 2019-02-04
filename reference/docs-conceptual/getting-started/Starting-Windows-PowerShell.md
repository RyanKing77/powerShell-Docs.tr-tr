---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows Powershell Başlatma
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688325"
---
# <a name="starting-windows-powershell"></a>Windows Powershell Başlatma
Birden çok konaklarına katıştırılmış bir komut dosyası altyapısı dll powershell'dir.  En yaygın konak, başlar, etkileşimli komut satırı PowerShell.exe ve etkileşimli betik ortamı PowerShell_ISE.exe verilmiştir.

Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 ve Windows 8 üzerinde Windows PowerShell® başlatmak için bkz: [genel yönetim görevleri ve gezinme](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Önceki Windows sürümlerinde Windows PowerShell'i başlatma

Bu bölümde, Windows® 7, Windows Server® 2008 R2 ve Windows Server® 2008 Windows PowerShell ve Windows PowerShell Tümleşik komut dosyası ortamı (ISE) başlatın açıklanmaktadır. Ayrıca, isteğe bağlı Windows PowerShell 2.0, Windows Server® 2008 R2 ve Windows Server® 2008'de Windows PowerShell ISE için nasıl etkinleştirileceğini açıklar.

Uygunsa, Windows PowerShell 3.0 veya Windows PowerShell 4. 0'ın yüklü sürümü başlatmak için aşağıdaki yöntemlerden birini kullanın.

#### <a name="from-the-start-menu"></a>Başlat Menüsü'nden

- Tıklayın **Başlat**, türü **PowerShell**ve ardından **Windows PowerShell**.
- Gelen **Başlat** menüsünde tıklayın **Başlat**, tıklayın **tüm programlar**, tıklayın **Donatılar**, tıklayın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Komut isteminde

Windows PowerShell'i başlatmak için cmd.exe, Windows PowerShell veya Windows PowerShell ISE'yi yazın:

```
PowerShell
```

PowerShell.exe program parametreleri oturum özelleştirmek için kullanabilirsiniz. Daha fazla bilgi için [PowerShell.exe komut satırı yardımcı](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları

Tıklayın **Başlat**, türü **PowerShell**, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Önceki Windows sürümlerinde Windows PowerShell ISE'yi başlatma

Windows PowerShell ISE'yi başlatmak için aşağıdaki yöntemlerden birini kullanın.

#### <a name="from-the-start-menu"></a>Başlat Menüsü'nden

- Tıklayın **Başlat**, türü **ISE**ve ardından **Windows PowerShell ISE**.
- Gelen **Başlat** menüsünde tıklayın **Başlat**, tıklayın **tüm programlar**, tıklayın **Donatılar**, tıklayın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>Komut isteminde

Windows PowerShell'i başlatmak için cmd.exe, Windows PowerShell veya Windows PowerShell ISE'yi yazın:

```
PowerShell_ISE
```

veya

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları

Tıklayın **Başlat**, türü **ISE**, sağ **Windows PowerShell ISE**ve ardından **yönetici olarak çalıştır**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Önceki Windows sürümlerinde bulunan Windows PowerShell ISE etkinleştirme

Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell ISE tüm Windows sürümlerinde varsayılan olarak etkindir. Zaten etkin değilse, Windows Management Framework 4.0 ya da Windows Management Framework 3.0 sağlar.

Windows PowerShell 2. 0 ', Windows PowerShell ISE, Windows 7 varsayılan olarak etkindir. Ancak, Windows Server 2008 R2 ve Windows Server 2008 üzerinde isteğe bağlı bir özelliktir.

Windows Server 2008 R2 veya Windows Server 2008'de Windows PowerShell 2.0 Windows PowerShell ISE'de etkinleştirmek için aşağıdaki yordamı kullanın.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Tümleşik komut dosyası ortamı (ISE) etkinleştirmek için

1. Sunucu Yöneticisi'ni başlatın.
2. Tıklayın **özellikleri** ve ardından **Özellik Ekle**.
3. Özellikleri, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) tıklayın.

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Windows PowerShell 32 Bit sürümünü başlatma

Bir 64 bit bilgisayarda, Windows PowerShell yüklediğinizde **Windows PowerShell (x86)**, Windows PowerShell 32 bit sürümünü yanı sıra 64-bit sürümü yüklü. Windows PowerShell çalıştırdığınızda, 64-bit sürümünü çalıştırır.

Ancak, bazen çalıştırmak ihtiyacınız olabilecek **Windows PowerShell (x86)**, 32 bit sürümü gerektiren bir modülünü kullanıyorsanız, gibi veya bir 32 bit bilgisayar için uzaktan bağlantı kurduğunuzda.

Windows PowerShell 32 bit sürümünü başlatmak için aşağıdaki yordamlardan birini kullanın.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**. Tıklayın **Windows PowerShell x86** Döşe.
- İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde **Windows PowerShell (x86)**.
- İmleç bölmenin sağ üst köşedeki için masaüstünde **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Üzerinde **Başlat** ekranında, yazın **PowerShell** ve ardından **Windows PowerShell (x86)**.
- İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde **Windows PowerShell (x86)**.
- İmleç bölmenin sağ üst köşedeki için masaüstünde **arama**, türü **PowerShell** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>8.1 Windows® içinde

- Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**. Tıklayın **Windows PowerShell x86** Döşe.
- Çalıştırıyorsanız [Uzak Sunucu Yönetim Araçları](https://go.microsoft.com/fwlink/?LinkID=304145) Windows 8.1 için Windows Powershell'den x86 da açabilirsiniz **sunucu ManagerTools** menüsü.
  Seçin **Windows PowerShell (x86)**.
- İmleç bölmenin sağ üst köşedeki için masaüstünde **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>8 Windows® içinde

- Üzerinde **Başlat** ekranında, sağ üst köşedeki imleç, tıklayın **ayarları**, tıklayın **kutucukları**ve ardından taşıma **Yönetimsel Araçları Göster** kaydırıcı Evet. Ardından yazın **PowerShell** tıklatıp **Windows PowerShell (x86)**.
- Çalıştırıyorsanız [Uzak Sunucu Yönetim Araçları](https://www.microsoft.com/download/details.aspx?id=28972) Windows 8 için Windows Powershell'den x86 da açabilirsiniz **sunucu ManagerTools** menüsü. Seçin **Windows PowerShell (x86)**.
- Üzerinde **Başlat** ekran veya yazın, Masaüstü **PowerShell (x86)** ve ardından **Windows PowerShell (x86)**.
- Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`