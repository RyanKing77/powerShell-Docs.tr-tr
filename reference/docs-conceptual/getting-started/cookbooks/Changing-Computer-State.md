---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bilgisayar Durumunu Değiştirme
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251526"
---
# <a name="changing-computer-state"></a>Bilgisayar Durumunu Değiştirme

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

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Daha fazla bilgi için ve diğer özellikleri Win32Shutdown yönteminin bulmak için "Win32Shutdown yöntemi, Win32_OperatingSystem sınıfında" MSDN bakın.

### <a name="shutting-down-or-restarting-a-computer"></a>Kapatma veya bir bilgisayar yeniden başlatma

Kapatma ve bilgisayarları yeniden genellikle aynı görev türleridir. Bir bilgisayarı Araçlar genellikle yeniden onu da — tersi. Windows PowerShell bilgisayardan yeniden başlatmak için kolay iki seçenek vardır. Tsshutdn.exe veya Shutdown.exe uygun bağımsız değişkenlerle birlikte kullanın. Ayrıntılı kullanım bilgilerini alabilir **tsshutdn.exe /?** veya **shutdown.exe /?**.

Ayrıca, kapatma gerçekleştirmek ve Windows PowerShell doğrudan işlemlerinden yeniden başlatın.

Bilgisayarı kapatmak için bilgisayarı yeniden Başlat komutunu kullanın.

```powershell
stop-computer
```

İşletim sistemi yeniden başlatmak için bilgisayarı yeniden Başlat komutunu kullanın.

```powershell
restart-computer
```
