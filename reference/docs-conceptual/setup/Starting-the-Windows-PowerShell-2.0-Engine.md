---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell 2.0 Altyapısını Başlatma
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: 618745ff4865dd046acf46487e87c3ca0e324f95
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="starting-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 Altyapısını Başlatma

Bu bölümde, Windows PowerShell 2.0 altyapısı Windows 8.1, Windows Server 2012 R2, Windows 8 ve Windows Server 2012'de, Windows PowerShell 2.0 altyapısı içeren ve diğer sistemlerde hangi Windows PowerShell 2.0, Windows PowerShell'i başlatmak açıklanmaktadır 3.0 ve Windows PowerShell 4.0 yüklenir.

Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell 2.0 ile geriye dönük olarak uyumlu olacak şekilde tasarlanmıştır. Cmdlet'leri, sağlayıcıları, ek bileşenler, modüller ve Windows PowerShell 2.0 için yazılan komut dosyaları Windows PowerShell 4.0 ve Windows PowerShell 3.0 değişmeden çalıştırın. Microsoft .NET Framework 4 çalışma zamanı etkinleştirme ilkede bir değişiklik nedeniyle Windows yapmadan olan Windows PowerShell 2.0 için yazılmış ve ortak dil çalışma zamanı (CLR ile) 2.0 derlenmiş Windows PowerShell konak programları ancak çalıştıramazsınız PowerShell 3.0 veya CLR 4.0 ile derlenen Windows PowerShell 4.0. Windows PowerShell 2.0 altyapısı varolan bir komut dosyasının kullanılması amaçlanmıştır veya Windows PowerShell 4.0, Windows PowerShell 3.0 veya Microsoft .NET Framework 4 ile uyumlu olmadığı için konak program çalıştırılamıyor. Bu gibi durumlarda nadir olması beklenir.

Windows PowerShell 2.0 altyapısı gerektiren birçok programlar otomatik olarak başlar. Bu yönergeleri altyapısı el ile başlatmak gereken nadir durumlarda dahil edilir.

## <a name="installing-and-enabling-required-programs"></a>Yükleme ve gereken tüm programları etkinleştirme

Windows PowerShell 2.0 altyapısı başlatmadan önce Microsoft .NET Framework 3.5 Service Pack 1 ve Windows PowerShell 2.0 altyapısı etkinleştirin. Yönergeler için bkz: [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).

Hangi sistemlerde [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ya da Windows Management Framework 3.0 yüklü tüm gerekli bileşenleri. Ek yapılandırma gerekli değildir. Yükleme hakkında bilgi için [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ya da Windows Management Framework 3.0, bkz: [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 altyapısı başlatma

Windows PowerShell başlattığınızda, en yeni sürümü varsayılan olarak başlatır. Windows PowerShell 2.0 altyapısı ile Windows PowerShell'i başlatmak için PowerShell.exe sürüm parametresini kullanın. Komut Windows PowerShell ve Cmd.exe dahil olmak üzere tüm isteminde komutu çalıştırabilirsiniz.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 altyapısı ile bir uzak oturum başlatma

Uzak bir oturumda Windows PowerShell 2.0 altyapısı çalıştırmak için Windows PowerShell 2.0 altyapısı yükler uzak bilgisayarda bir oturum yapılandırması (olarak da bilinen bir "uç nokta") oluşturun. Oturum yapılandırması, uzak bilgisayarda kaydedilir ve Windows PowerShell 2.0 Altyapısı'nı kullanan oturumları oluşturmak için yetkili bir kullanıcı tarafından kullanılabilir.

Bu genellikle bir sistem yöneticisi tarafından gerçekleştirilen Gelişmiş bir görevdir.

Aşağıdaki yordam kullanır **PSVersion** parametresinin [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) Windows PowerShell 2.0 altyapısı kullanan bir oturum yapılandırması oluşturmak için cmdlet'i. Aynı zamanda **PowerShellVersion** parametresinin [yeni PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) Windows PowerShell 2.0 altyapısı yükleyen oturum için bir oturum yapılandırma dosyası oluşturmak için cmdlet'i ve kullanabileceğiniz **PSVersion** parametresinin [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) Windows PowerShell 2.0 altyapısı kullanmak için bir oturum yapılandırmasını değiştirmek için parametre.

Oturum yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Kurulum ve güvenlik dahil olmak üzere oturum yapılandırmaları hakkında bilgi için bkz: [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Uzak bir Windows PowerShell 2.0 oturumu başlatmak için

1. Windows PowerShell 2.0 altyapısı gerektiren bir oturum yapılandırması oluşturmak için kullanın **PSVersion** parametresinin [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet "2.0" değerine sahip. Bu komut, "sunucu tarafı" veya bağlantı alıcı sonunda bilgisayarda çalıştırın.

   Aşağıdaki örnek komut Server01 bilgisayarda PS2 oturum yapılandırması oluşturur. Bu komutu çalıştırmak için Windows PowerShell 4.0 veya Windows PowerShell 3.0 ile başlangıç **yönetici olarak çalıştır** seçeneği.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. PS2 oturum yapılandırması kullanan Server01 bilgisayarda oturum oluşturmak için kullanmak **ConfigurationName** uzak bir oturum oluşturun cmdlet'leri parametresinin [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet'i.

   Oturum yapılandırması kullanan bir oturum başlatıldığında, Windows PowerShell 2.0 altyapısı oturuma otomatik olarak yüklenir.

   Aşağıdaki komut PS2 oturum yapılandırması kullanan Server01 bilgisayarda bir oturum başlatır. Komut oturum $s değişkenine kaydeder.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 altyapısı ile arka plan işi başlatma

Windows PowerShell 2.0 altyapısı ile bir arka plan işi başlatmak için kullanmak **PSVersion** parametresinin [başlangıç işi](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet'i.

Aşağıdaki komut bir arka plan işi Windows PowerShell 2.0 altyapısı ile başlatır.

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Arka plan işleri hakkında daha fazla bilgi için bkz: [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).