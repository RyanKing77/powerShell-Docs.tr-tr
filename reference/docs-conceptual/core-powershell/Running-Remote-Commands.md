---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Uzak komutları çalıştırma"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 5cf9690b8fe4549a99186f172cb6f0de156a4dea
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="running-remote-commands"></a>Uzak komutları çalıştırma
Bir ya da tek bir Windows PowerShell komut bilgisayarlarla yüzlerce komutları çalıştırabilirsiniz. Windows PowerShell, WMI, RPC ve WS-Management gibi çeşitli teknolojiler kullanılarak bir uzak bilgisayar destekler.

## <a name="remoting-without-configuration"></a>Yapılandırma olmadan uzaktan iletişim
Birçok Windows PowerShell cmdlet'leri veri toplamak ve bir veya daha fazla uzak bilgisayarlarda ayarlarını değiştirmenizi sağlar ComputerName parametresi vardır. Tüm Windows işletim sistemlerinde özel bir yapılandırma Windows PowerShell destekleyen çeşitli iletişimi teknolojileri ve birçok iş kullanırlar.

Şu cmdlet'leri içerir:
* [Bilgisayarı yeniden Başlat](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Bağlantıyı Sına](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Olay günlüğünü Temizle](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-olay günlüğü](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-düzeltme](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Hizmet belirleme](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

Genellikle, özel bir yapılandırma olmadan remoting destekleyen cmdlet'ler ComputerName parametresi varsa ve oturum parametresi yok. Bu cmdlet'ler oturumunuzda bulmak için şunu yazın:

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell uzaktan iletişim
Bir veya daha çok uzak bilgisayarlarda herhangi bir Windows PowerShell komutunu çalıştırın WS-Management protokolü kullanır, Windows PowerShell uzaktan iletişim sağlar. Kalıcı bağlantılar kurmak, 1:1 etkileşimli oturumlarını başlatmak ve komut dosyaları birden çok bilgisayarda çalışacak olanak sağlar.

Windows PowerShell uzaktan iletişim kullanmak için uzak bilgisayara uzaktan yönetim için yapılandırılmalıdır. Yönergeleri dahil daha fazla bilgi için bkz: [hakkında uzaktan gereksinimleri](https://technet.microsoft.com/en-us/library/dd315349.aspx).

Windows PowerShell uzaktan iletişimini yapılandırdıktan sonra birçok remoting strateji size kullanılabilir. Bu belgenin geri kalanında birkaçı bunları listeler. Daha fazla bilgi için bkz: [hakkında uzak](https://technet.microsoft.com/en-us/library/dd347744.aspx) ve [hakkında uzak SSS](https://technet.microsoft.com/en-us/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Etkileşimli oturum Başlat
Tek bir uzak bilgisayarla bir etkileşimli oturum başlatmak için kullanmak [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet'i.
Örneğin, Server01 uzak bilgisayarla bir etkileşimli oturum başlatmak için şunu yazın:

```
Enter-PSSession Server01
```

Bağlı olduğunuz bilgisayar adını görüntülemek için komut istemi değişiklikler. Daha sonra uzak bilgisayarda komut istemine yazın herhangi bir komut çalıştırmak ve sonuçları yerel bilgisayarda görüntülenir.

Etkileşimli oturum sonlandırmak için aşağıdakini yazın:

```
Exit-PSSession
```

Enter-PSSession ve çıkış-PSSession cmdlet'leri hakkında daha fazla bilgi için bkz: [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) ve [çıkış-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Uzak bir komutu çalıştırın
Bir veya daha çok uzak bilgisayarlarda herhangi bir komut çalıştırmak için kullandığınız [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet'i.
Örneğin, çalıştırmak için bir [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) komutunu Server01 ve Server02 uzak bilgisayarlarda, türü:

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Çıktı bilgisayarınıza döndürülür.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
Invoke-Command cmdlet'i hakkında daha fazla bilgi için bkz: [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Bir komut dosyasını çalıştır
Bir veya daha çok uzak bilgisayarda bir komut dosyasını çalıştırmak için Invoke-Command cmdlet'i FilePath parametresini kullanın. Komut dosyası ya da yerel bilgisayarınıza erişilebilir olması gerekir. Sonuçlar, yerel bilgisayarınıza döndürülür.

Örneğin, aşağıdaki komutu DiskCollect.ps1 betik Server01 ve Server02 uzak bilgisayarlarda çalışır.

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Invoke-Command cmdlet'i hakkında daha fazla bilgi için bkz: [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Kalıcı bağlantı kurun
Bir dizi veri paylaşımı ilgili komutları çalıştırmak için uzak bilgisayarda bir oturumu oluşturmak ve oluşturduğunuz oturumunda komutları çalıştırmak için Invoke-Command cmdlet'ini kullanın. Uzak oturum oluşturmak için New-PSSession cmdlet'i kullanın.

Örneğin, aşağıdaki komutu Server02 bilgisayarda bir uzak oturum Server01 bilgisayarda ve başka bir uzak oturum oluşturur. Bu oturum nesneleri $s değişkenine kaydeder.

```
$s = New-PSSession -ComputerName Server01, Server02
```

Oturum oluşturulur, bunları herhangi komutu çalıştırabilirsiniz. Ve oturumları kalıcı olduğundan, bir komut verileri toplamak ve bir sonraki komutunu kullanın.

Örneğin, aşağıdaki komutu oturumlarda $s değişkeninde bir Get-düzeltme komut çalıştırır ve sonuçları $h değişkenine kaydeder. Her $s oturumlarında $h değişkeni oluşturuldu, ancak yerel oturumunda yok.

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

Artık aşağıdaki biri gibi sonraki komutlarda $h değişkeninde verileri kullanabilirsiniz. Sonuçlar yerel bilgisayarda görüntülenir.

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Gelişmiş uzaktan iletişim
Windows PowerShell uzaktan yönetimi yalnızca burada başlar. Yüklü Windows PowerShell cmdlet'lerini kullanarak oluşturmak ve Uzak Oturumlar yapılandırma yerel ve uzak uç gerçekte Çalıştır komutları uzak oturumdan içeri aktarmak için kullanıcıların izin özelleştirilmiş ve kısıtlı oturumları oluşturma örtük olarak uzak oturum bir uzak oturum ve daha fazlasını güvenliğini yapılandırın.

Uzak yapılandırmasını kolaylaştırmak için Windows PowerShell WSMan sağlayıcısı içerir. WSMAN: sağlayıcısı oluşturur sürücü yapılandırma ayarları yerel bilgisayarda ve uzak bilgisayarlarda hiyerarşisini gezinmek olanak sağlar.
WSMan sağlayıcısı hakkında daha fazla bilgi için bkz: [WSMan sağlayıcısı](https://technet.microsoft.com/en-us/library/dd819476.aspx) ve [WS-Management cmdlet'leri hakkında](https://technet.microsoft.com/en-us/library/dd819481.aspx), veya Windows PowerShell konsolunda "Get-Help wsman" yazın.

Daha fazla bilgi için bkz.:
- [Uzak SSS hakkında](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Remoting hatalarla ilgili Yardım için bkz: [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).

## <a name="see-also"></a>Ayrıca bkz:
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [Yeni PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan sağlayıcısı](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
