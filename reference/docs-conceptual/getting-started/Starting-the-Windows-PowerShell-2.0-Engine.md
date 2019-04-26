---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell 2.0 Altyapısını Başlatma
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: f5dd01cd93095fe15cc7e57f97f4b2920e580c22
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086519"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 Altyapısını Başlatma

Bu bölümde Windows 8.1, Windows Server 2012 R2, Windows 8 ve Windows Server 2012, Windows PowerShell 2.0 altyapısını içeren ve diğer sistemlerde hangi Windows PowerShell 2.0, Windows PowerShell, Windows PowerShell 2.0 altyapısını başlatma açıklanmaktadır. 3.0 ve Windows PowerShell 4.0 yüklenir.

Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell 2.0 ile geriye dönük olarak uyumlu olacak şekilde tasarlanmıştır. Windows PowerShell 3.0 ve Windows PowerShell 4.0 ile değişmeden cmdlet'leri, sağlayıcıları, ek bileşenler, modülleri ve Windows PowerShell 2.0 için yazılan betikler çalıştırın. Microsoft .NET Framework 4 çalışma zamanı etkinleştirme ilkesini bir değişiklikten dolayı Windows gerektirmeden ancak Windows PowerShell ana bilgisayar Windows PowerShell 2.0 için yazılmış ve ortak dil çalışma zamanı (CLR ile) 2.0 derlenmiş bir program çalıştırılamıyor PowerShell 3.0 veya CLR 4.0 ile derlenmiş Windows PowerShell 4.0. Mevcut bir komut dosyasının yaparken kullanılmak üzere Windows PowerShell 2.0 altyapısını amaçlanmamıştır veya Windows PowerShell 4.0, Windows PowerShell 3.0 veya Microsoft .NET Framework 4 ile uyumsuz olduğundan ana program çalıştırılamıyor. Böyle durumlarda, nadir olmaları beklenir.

Windows PowerShell 2.0 altyapısı gerektiren birçok programlar otomatik olarak başlatın. Bu yönergeler, altyapıyı el ile başlatmak gereken bazı nadir durumlar için dahil edilir.

## <a name="installing-and-enabling-required-programs"></a>Yükleme ve etkinleştirme gerekli programlar

Windows PowerShell 2.0 altyapısını başlamadan önce Microsoft .NET Framework 3.5 Service Pack 1 ve Windows PowerShell 2.0 altyapısını etkinleştirin. Yönergeler için [Windows PowerShell'i yükleme](../install/Installing-Windows-PowerShell.md).

Sistemleri sahip tüm gerekli bileşenleri üzerinde hangi Windows Management Framework 4.0 ya da Windows Management Framework 3.0 yüklenir. Ek yapılandırma gerekli değildir. Yükleme hakkında daha fazla bilgi için [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) veya bkz. Windows Management Framework 3.0 [Windows PowerShell'i yükleme](../install/Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 altyapısını başlatma

Windows PowerShell'i başlatın varsayılan olarak en yeni sürümü başlatılır. Windows PowerShell ile Windows PowerShell 2.0 altyapısını başlatmak için PowerShell.exe sürüm parametresini kullanın. Komut Windows PowerShell ve Cmd.exe dahil olmak üzere tüm isteminde komutu çalıştırabilirsiniz.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Uzak oturumu ile Windows PowerShell 2.0 altyapısını başlatma

Uzak bir oturumda Windows PowerShell 2.0 altyapısını çalıştırmak için uzak bilgisayarda Windows PowerShell 2.0 altyapısını yükleyen bir oturum yapılandırması (olarak da bilinen bir "uç noktası") oluşturun. Oturum yapılandırması, uzak bilgisayarda kaydedilir ve Windows PowerShell 2.0 Altyapısı'nı kullanan oturumları oluşturmak için yetkili bir kullanıcı tarafından kullanılabilir.

Bu genellikle bir sistem yöneticisi tarafından gerçekleştirilen Gelişmiş bir görevdir.

Aşağıdaki yordam kullanır **PSVersion** parametresinin [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) Windows PowerShell 2.0 altyapısını kullanan bir oturum yapılandırması oluşturmak için cmdlet'i. Ayrıca **PowerShellVersion** parametresinin [yeni PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) yükleyen Windows PowerShell 2.0 altyapısını oturum için bir oturum yapılandırma dosyası oluşturmak için cmdlet'i ve kullanabileceğiniz **PSVersion** parametresinin [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) Windows PowerShell 2.0 altyapısı kullanmak için bir oturum yapılandırmasını değiştirmek için parametre.

Oturum yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Kurulum ve güvenlik dahil olmak üzere, oturum yapılandırmaları hakkında bilgi için bkz. [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Uzak bir Windows PowerShell 2.0 oturumu başlatmak için

1. Windows PowerShell 2.0 altyapısı gerektiren bir oturum yapılandırması oluşturmak için kullanın **PSVersion** parametresinin [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet'i "2.0" değerine sahip. "Sunucu tarafı" veya bağlantı alıcı sonunda bilgisayarda şu komutu çalıştırın.

   Aşağıdaki örnek komutta Server01 bilgisayar PS2 oturum yapılandırması oluşturur. Bu komutu çalıştırmak için Windows PowerShell 4.0 veya Windows PowerShell 3. 0'ile Başlat **yönetici olarak çalıştır** seçeneği.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. PS2 oturum yapılandırması kullanan Server01 bilgisayarda oturum oluşturmak için kullanın **ConfigurationName** gibi bir uzak oturumu oluşturma cmdlet'lerinin parametresine [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet'i.

   Oturum yapılandırması kullanan bir oturum başlatıldığında, Windows PowerShell 2.0 altyapısını oturuma otomatik olarak yüklenir.

   Aşağıdaki komut, PS2 oturum yapılandırması kullanan Server01 bilgisayarda oturum başlatır. Komutu, oturum $s değişkenine kaydeder.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Arka plan işi ile Windows PowerShell 2.0 altyapısını başlatma

Windows PowerShell 2.0 altyapısı ile arka plan işi başlatmak için kullanın **PSVersion** parametresinin [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet'i.

Aşağıdaki komut, bir arka plan işi ile Windows PowerShell 2.0 altyapısını başlatır.

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Arka plan işleri hakkında daha fazla bilgi için bkz: [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).