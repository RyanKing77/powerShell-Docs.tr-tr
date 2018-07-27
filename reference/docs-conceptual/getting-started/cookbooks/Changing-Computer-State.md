---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bilgisayar Durumunu Değiştirme
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 4b5b4adb349dd8036117c364ed2ebb1ffaf8c88f
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267894"
---
# <a name="changing-computer-state"></a>Bilgisayar Durumunu Değiştirme

Bir bilgisayar Windows PowerShell'de sıfırlamak için standart bir komut satırı aracını veya WMI sınıfını kullanın. Yalnızca aracı çalıştırmak için Windows PowerShell kullanarak karşın, Windows PowerShell'de bir bilgisayarın güç durumu değiştirmek öğrenme Windows PowerShell'de dış araçları ile çalışma hakkında önemli ayrıntıları bazıları gösterilmektedir.

### <a name="locking-a-computer"></a>Bilgisayarı kilitleme

Standart kullanılabilir araçları ile doğrudan bir bilgisayarı kilitlemek için tek yolu çağırmaktır **LockWorkstation() işlevini** işlevi **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Bu komut, hemen iş istasyonu kilitler. Kullandığı *rundll32.exe*, hangi Windows DLL'leri çalışır (ve yinelemeli olarak kullanmak için kendi kitaplıkları kaydeder) user32.dll, Windows Yönetim işlevlerini içeren bir kitaplık çalıştırılacak.

Ne zaman hızlı kullanıcı değiştirme etkinken Windows XP'de geçerli kullanıcının ekran koruyucu başlangıç yerine kullanıcı oturum açma ekranında bilgisayarı görüntüler gibi bir iş istasyonu kilitleyin.

Belirli bir Terminal sunucusu oturumları kapatmak için kullanın **tsshutdn.exe** komut satırı aracı.

### <a name="logging-off-the-current-session"></a>Geçerli oturumu oturumunu kapatma

Yerel sistem hakkındaki oturumu oturumunu için birkaç farklı teknikleri kullanabilirsiniz. En basit yolu Uzak Masaüstü/Terminal Hizmetleri komut satırı aracını kullanmaktır **logoff.exe** (Ayrıntılar için Windows PowerShell komut isteminde yazın **kapatma /?**). Geçerli etkin oturumu için şunu yazın **kapatma** bağımsız değişken olmadan.

Ayrıca **shutdown.exe** aracı ile oturum kapatma seçeneği:

```
shutdown.exe -l
```

Üçüncü bir seçenek WMI kullanmaktır. Win32_OperatingSystem sınıfını Win32Shutdown yöntemi vardır. 0 bayrağıyla metodu çağrılırken, oturum kapatma başlatır:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Daha fazla bilgi almak ve diğer özellikleri Win32Shutdown yöntemin bulmak için "Win32Shutdown yöntemi, Win32_OperatingSystem sınıfını" MSDN'de bakın.

### <a name="shutting-down-or-restarting-a-computer"></a>Kapatma veya bir bilgisayar yeniden başlatma

Bilgisayarları yeniden başlatma ve kapatma genellikle aynı görevi türleridir. Bir bilgisayarı Araçlar genellikle yeniden başlatılacak, de- ve bunun tersi de geçerlidir. Windows powershell'den bilgisayarı yeniden başlatmak için iki basit seçenek vardır. Tsshutdn.exe ya da Shutdown.exe uygun bağımsız değişkenlerle birlikte kullanın. Ayrıntılı kullanım bilgilerini alabileceğiniz **tsshutdn.exe /?** veya **shutdown.exe /?**.

Kapatma gerçekleştirme ve işlemleri de Windows PowerShell üzerinden doğrudan yeniden başlatın.

Bilgisayarı kapatmak için stop-computer komutunu kullanın.

```powershell
stop-computer
```

İşletim sistemi yeniden başlatmak için bilgisayarı yeniden başlat komutu kullanın.

```powershell
restart-computer
```
