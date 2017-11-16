---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Bilgisayar durumunu değiştirme"
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 636690c72b16bf19826b0a7e54ce00114ce30fb6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="changing-computer-state"></a>Bilgisayar durumunu değiştirme
Bir bilgisayarı Windows PowerShell'de sıfırlamak için standart bir komut satırı aracını veya WMI sınıfı kullanın. Yalnızca aracı çalıştırmak için Windows PowerShell kullanarak karşın, Windows PowerShell'de bilgisayarın güç durumunu değiştirmek öğrenme bazı Windows PowerShell'de dış araçları ile çalışma hakkında önemli ayrıntıları gösterir.

### <a name="locking-a-computer"></a>Bilgisayarı kilitleme
Standart mevcut araçlar ile doğrudan bilgisayarı kilitlemek için tek yolu çağırmaktır **LockWorkstation() işlevini** işlevi **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Bu komut, iş istasyonu hemen kilitler. Kullandığı *rundll32.exe*, hangi Windows DLL'leri çalışır (ve yinelemeli olarak kullanmak için kendi kitaplıkları kaydeder) user32.dll, bir kitaplık Windows Yönetim işlevlerini çalıştırmak için.

Ne zaman hızlı kullanıcı değiştirme etkinken Windows XP'de, geçerli kullanıcının koruyucu başlatmak yerine kullanıcı oturum açma ekranı bilgisayar görüntüler gibi bir iş istasyonu kilitleyin.

Terminal sunucusu üzerinde belirli oturumları kapatmak üzere kullanmak **tsshutdn.exe** komut satırı aracı.

### <a name="logging-off-the-current-session"></a>Oturumunu geçerli oturumu kapatma
Yerel sistemde oturum oturumunu için birçok farklı tekniği kullanabilirsiniz. En basit yolu Uzak Masaüstü/Terminal Hizmetleri komut satırı aracını kullanmaktır **logoff.exe** (Ayrıntılar için Windows PowerShell komut isteminde yazın **kapatma /?**). Geçerli etkin oturumu için şunu yazın **kapatma** bağımsız değişken içermeyen.

Aynı zamanda **shutdown.exe** , kapatma seçeneğini aracıyla:

```
shutdown.exe -l
```

WMI kullanan üçüncü bir seçenektir. Win32_OperatingSystem sınıfını Win32Shutdown yöntemi vardır. 0 bayrağı yönteminin çağrılması kapatma başlatır:

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Daha fazla bilgi için ve diğer özellikleri Win32Shutdown yönteminin bulmak için "Win32Shutdown yöntemi, Win32_OperatingSystem sınıfında" MSDN bakın.

### <a name="shutting-down-or-restarting-a-computer"></a>Kapatma veya bir bilgisayar yeniden başlatma
Kapatma ve bilgisayarları yeniden genellikle aynı görev türleridir. Bir bilgisayarı Araçlar genellikle yeniden onu da — tersi. Windows PowerShell bilgisayardan yeniden başlatmak için kolay iki seçenek vardır. Tsshutdn.exe veya Shutdown.exe uygun bağımsız değişkenlerle birlikte kullanın. Ayrıntılı kullanım bilgilerini alabilir **tsshutdn.exe /?** veya **shutdown.exe /?**.

Ayrıca kapatma gerçekleştirmek ve işlemlerini kullanarak yeniden **Win32_OperatingSystem** Windows PowerShell doğrudan.

Bilgisayarı kapatmak için Win32Shutdown yöntemiyle kullanmak **1** bayrağı.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

İşletim sistemi yeniden başlatmaya Win32Shutdown yöntemiyle kullanmak **2** bayrağı.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```

