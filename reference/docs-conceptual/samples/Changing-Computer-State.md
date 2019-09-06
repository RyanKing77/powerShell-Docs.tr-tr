---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Bilgisayar Durumunu Değiştirme
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386281"
---
# <a name="changing-computer-state"></a>Bilgisayar Durumunu Değiştirme

Windows PowerShell 'de bir bilgisayarı sıfırlamak için, standart bir komut satırı aracı, WMI veya CıM sınıfı kullanın. Yalnızca aracı çalıştırmak için Windows PowerShell kullanıyor olsanız da, Windows PowerShell 'de bilgisayarın güç durumunu değiştirme hakkında bilgi edinmek için Windows PowerShell 'de dış araçlarla çalışma hakkındaki önemli ayrıntıların bazıları gösterilir.

## <a name="locking-a-computer"></a>Bilgisayarı kilitleme

Bir bilgisayarı doğrudan standart kullanılabilir araçlarla kilitlemeye yönelik tek yol, **User32. dll**' de **LockWorkstation ()** işlevini çağırmanız durumunda:

```
rundll32.exe user32.dll,LockWorkStation
```

Bu komut, iş istasyonunu hemen kilitler. Windows yönetim işlevlerinin bir kitaplığı olan User32. dll dosyasını çalıştırmak için Windows dll 'Leri çalıştıran *Rundll32. exe*' yi (ve bunları yinelenen kullanım için kaydeder) kullanır.

Windows XP gibi Hızlı Kullanıcı geçişi etkinken bir iş istasyonunu kilitlerseniz, bilgisayar geçerli kullanıcının ekran koruyucuyu başlatmak yerine Kullanıcı oturum açma ekranını görüntüler.

Bir terminal sunucusundaki belirli oturumları kapatmak için **Tsshutdn. exe** komut satırı aracını kullanın.

## <a name="logging-off-the-current-session"></a>Geçerli oturumun oturumu kapatılıyor

Yerel sistemdeki bir oturum oturumunu kapatmak için birkaç farklı teknik kullanabilirsiniz. En basit yol, Uzak Masaüstü/Terminal Hizmetleri komut satırı aracı olan **logoff. exe** ' yi kullanmaktır (Ayrıntılar Için Windows PowerShell isteminde, **logoff/?** yazın). Geçerli etkin oturumu kapatmak için bağımsız değişken olmadan **logoff** yazın.

**Kapatma. exe** aracını, oturum kapatma seçeneğiyle de kullanabilirsiniz:

```
shutdown.exe -l
```

Başka bir seçenek de WMI kullanmaktır. Win32_OperatingSystem sınıfında bir Win32Shutdown yöntemi vardır. Yöntemi 0 bayrağıyla çağırmak oturumu kapatmayı başlatır:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Daha fazla bilgi edinmek ve Win32Shutdown yönteminin diğer özelliklerini bulmak için MSDN 'de "Win32_OperatingSystem sınıfının Win32Shutdown yöntemi" başlığına bakın.

Son olarak, WMI yönteminde yukarıda açıklanan şekilde aynı Win32_OperatingSystem sınıfıyla CıM kullanabilirsiniz.

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Bilgisayarı kapatma veya yeniden başlatma

Bilgisayarları kapatmak ve yeniden başlatmak genellikle aynı türde görevdir. Bir bilgisayarı kapatmakta olan araçlar, genellikle da yeniden başlatılır ve tam tersi de geçerlidir. Windows PowerShell 'den bir bilgisayarı yeniden başlatmak için iki basit seçenek vardır. TSShutdn. exe veya kapatılmasını. exe ' yi uygun bağımsız değişkenlerle kullanın. **Tsshutdn. exe/?** adresinden ayrıntılı kullanım bilgileri alabilirsiniz. veya **kapatılacak. exe/?** .

Ayrıca, doğrudan Windows PowerShell 'den de kapalı ve yeniden başlatma işlemleri gerçekleştirebilirsiniz.

Bilgisayarı kapatmak için, dur-Computer komutunu kullanın

```powershell
Stop-Computer
```

İşletim sistemini yeniden başlatmak için yeniden Başlat-bilgisayar komutunu kullanın

```powershell
Restart-Computer
```

Bilgisayarın hemen yeniden başlatılmasını zorlamak için-zorlama parametresini kullanın.

```powershell
Restart-Computer -Force
```
