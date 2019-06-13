---
ms.date: 08/14/2018
keywords: PowerShell cmdlet'i
title: Uzak Komut Çalıştırma
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030321"
---
# <a name="running-remote-commands"></a>Uzak Komut Çalıştırma

Bir ya da tek bir PowerShell komutu bilgisayarlarla yüzlerce komutları çalıştırabilirsiniz. Windows PowerShell, WMI, RPC ve WS-Yönetimi dahil olmak üzere çeşitli teknolojiler kullanarak uzak bilgisayar destekler.

PowerShell Core destekler, WMI, WS-Management ve SSH uzaktan iletişim. RPC artık desteklenmiyor.

Uzak PowerShell core'da hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [SSH PowerShell core'da uzaktan iletişim][ssh-remoting]
- [PowerShell core'da WSMan uzaktan iletişim][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Windows PowerShell uzaktan iletişimini yapılandırma olmadan

Birçok Windows PowerShell cmdlet'lerini sağlar, veri toplamak ve bir veya daha fazla uzak bilgisayar ayarlarını değiştirmek ComputerName parametresine sahip. Bu cmdlet'ler, farklı iletişim protokolleri kullanın ve özel bir yapılandırma olmadan tüm Windows işletim sistemlerinde çalışır.

Şu cmdlet'leri içerir:

- [Bilgisayarı yeniden Başlat](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [EventLog Temizle](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Hizmet belirleme](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

Genellikle, özel bir yapılandırma olmadan uzaktan iletişimini destekleyen cmdlet'ler ComputerName parametresine sahip ve oturum parametresi yok. Bu cmdlet'ler oturumunuzda bulmak için şunu yazın:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell uzaktan iletişimi

WS-Management protokolü kullanarak, Windows PowerShell uzaktan iletişimini, bir veya daha fazla uzak bilgisayar üzerinde herhangi bir Windows PowerShell komutunu çalıştırmak olanak tanır. Kalıcı bağlantılar kurmanın, etkileşimli bir oturum başlatın ve uzak bilgisayarlarda betikleri çalıştırın.

Windows PowerShell uzaktan iletişimini kullanmak için uzak bilgisayara uzaktan yönetim için yapılandırılmalıdır.
Yönergeleri de dahil daha fazla bilgi için bkz. [uzak gereksinimlerin](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Windows PowerShell uzaktan iletişimini yapılandırdıktan sonra birçok remoting stratejileri sizin için kullanılabilir.
Bu makalede, yalnızca birkaç tanesi listelenmektedir. Daha fazla bilgi için [hakkında uzak](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Etkileşimli bir oturum Başlat

Tek bir uzak bilgisayar ile etkileşimli bir oturum başlatmak için kullanın [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet'i.
Örneğin, Server01 uzak bilgisayarla etkileşimli bir oturum başlatmak için şunu yazın:

```powershell
Enter-PSSession Server01
```

Uzak bilgisayarın adını görüntülemek için komut istemi değişiklikler. Uzak bilgisayarda herhangi bir komut isteminde çalıştırın ve sonuçları yerel bilgisayarda görüntülenir.

Etkileşimli oturumu sona erdirmek için şunu yazın:

```powershell
Exit-PSSession
```

Enter-PSSession ve çıkış-PSSession cmdlet'ler hakkında daha fazla bilgi için bkz:

- [PSSession girin](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Çıkış-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Uzak komut çalıştırma

Bir veya daha çok bilgisayarda bir komut çalıştırmak için kullanın [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet'i. Örneğin, çalıştırılacak bir [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) komutunu Server01 ve Server02 uzak bilgisayarlarda, türü:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Çıkış bilgisayarınıza döndürülür.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Betik çalıştırma

Bir veya birden çok uzak bilgisayarda bir betik çalıştırmak için FilePath parametresini kullanın. `Invoke-Command` cmdlet'i. Betik veya yerel bilgisayarınıza erişilebilir olmalıdır. Sonuçları, yerel bilgisayarınıza döndürülür.

Örneğin, aşağıdaki komutu, uzak bilgisayarlarda, Server01 ve Server02 DiskCollect.ps1 betiği çalıştırır.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Kalıcı bir bağlantı kurun

Kullanım `New-PSSession` kalıcı oturum uzak bir bilgisayar oluşturmak için cmdlet'i. Aşağıdaki örnek, Uzak Oturumlar Server01 ve Server02 oluşturur. Oturum nesneleri depolanan `$s` değişkeni.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Oturumları kurulur, bunları herhangi bir komutu çalıştırabilirsiniz. Ve oturumları kalıcı olduğundan, bir komuttan toplayabilir ve başka bir komutta kullanın.

Örneğin, oturumlarında $s değişkenine Get-HotFix komutu şu komutu çalıştırır ve sonuçları $h değişkeninde kaydeder. $H değişken her $s oturumlarda oluşturulur, ancak yerel oturumu yok.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Veriler artık `$h` aynı oturumda diğer komutlarla değişken. Sonuçlar, yerel bilgisayarda görüntülenir. Örneğin:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Gelişmiş uzaktan iletişim

Windows PowerShell uzaktan yönetimi yalnızca burada başlar. Windows PowerShell ile yüklenen cmdlet'ler kullanarak oluşturmak ve Uzak Oturumlar yerel ve uzak uç çalıştırdığı komutları uzak oturum bağlantısını almak için kullanıcıların izin özelleştirilmiş ve kısıtlı oturumları oluşturma örtük uzak oturum uzak oturumu ve daha fazlasını güvenliğini yapılandırın.

Windows PowerShell WSMan sağlayıcısı içerir. Sağlayıcı oluşturur bir `WSMAN:` bir hiyerarşi yapılandırma ayarlarını yerel bilgisayarda ve uzak bilgisayarlar arasında gezinmek sağlayan sürücü.

WSMan sağlayıcısı hakkında daha fazla bilgi için bkz. [WSMan sağlayıcısı](https://technet.microsoft.com/library/dd819476.aspx) ve [WS-Management cmdlet'leri hakkında](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), veya Windows PowerShell konsolunda `Get-Help wsman`.

Daha fazla bilgi için bkz.:

- [Uzak SSS hakkında](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Uzaktan iletişimini hatalarla ilgili Yardım için bkz. [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Ayrıca bkz:

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [Yeni-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan sağlayıcısı](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
