---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows'un önceki sürümlerinde Windows PowerShell'i başlatma"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>Windows'un önceki sürümlerinde Windows PowerShell'i başlatma
Bu bölümde, Windows PowerShell ve Windows PowerShell Tümleşik komut dosyası ortamı (ISE) Windows® 7, Windows Server® 2008 R2 ve Windows Server® 2008 Başlat açıklanmaktadır. Ayrıca, isteğe bağlı Windows PowerShell ISE Windows PowerShell 2.0 Windows Server® 2008 R2 ve Windows Server® 2008 için nasıl etkinleştirileceğini açıklar.

Desteklenen sistemlerinde Windows PowerShell 4.0 sürümünü yüklemek için karşıdan yükleyip kurun [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Daha fazla bilgi için bkz: [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).

Windows PowerShell 3.0 desteklenen sistemlerinde yüklemek için karşıdan yükleyip kurun [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Daha fazla bilgi için bkz: [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Windows'un önceki sürümlerinde Windows PowerShell'i başlatma
Windows PowerShell 3.0 ya da Windows PowerShell 4. 0'ın yüklü sürümü uygunsa başlatmak için aşağıdaki yöntemlerden birini kullanın.

#### <a name="from-the-start-menu"></a>Başlat menüsünden

- Tıklatın **Başlat**, türü **PowerShell**ve ardından **Windows PowerShell**.

- Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Komut isteminde

- Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:

    ```
    PowerShell
    ```

    PowerShell.exe programın parametreleri, oturum özelleştirmek için de kullanabilirsiniz. Daha fazla bilgi için bkz: [PowerShell.exe komut satırı yardımcı](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları

1. Tıklatın **Başlat**, türü **PowerShell**, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Önceki Windows sürümlerinde Windows PowerShell ISE başlatma
Windows PowerShell ISE başlatmak için aşağıdaki yöntemlerden birini kullanın.

#### <a name="from-the-start-menu"></a>Başlat menüsünden

- Tıklatın **Başlat**, türü **işe**ve ardından **Windows PowerShell ISE**.

- Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>Komut isteminde

- Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:

    ```
    PowerShell_ISE
    ```

    veya

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları

1. Tıklatın **Başlat**, türü **işe**, sağ **Windows PowerShell ISE**ve ardından **yönetici olarak çalıştır**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Windows'un önceki sürümlerinde Windows PowerShell ISE etkinleştirme
Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell ISE tüm Windows sürümlerinde varsayılan olarak etkindir. Zaten etkin değilse, Windows Management Framework 4.0 ya da Windows Management Framework 3.0 sağlar.

Windows PowerShell 2. 0 ', Windows PowerShell ISE, Windows 7 üzerinde varsayılan olarak etkindir. Ancak, Windows Server 2008 R2 ve Windows Server 2008 üzerinde isteğe bağlı bir özelliktir.

Windows PowerShell 2.0 Windows Server 2008 R2 veya Windows Server 2008, Windows PowerShell ISE etkinleştirmek için aşağıdaki yordamı kullanın.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Tümleşik komut dosyası ortamı (ISE) etkinleştirmek için

1. Sunucu Yöneticisi'ni başlatın.

2. Tıklatın **özellikleri** ve ardından **Özellik Ekle**.

3. Özellikleri Windows PowerShell Tümleşik komut dosyası ortamı (ISE) tıklayın.

