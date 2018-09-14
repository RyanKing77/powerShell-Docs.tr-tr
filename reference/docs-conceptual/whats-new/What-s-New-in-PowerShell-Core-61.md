---
title: PowerShell Core 6.1 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6.1 yayımlanan değişiklikleri
ms.date: 09/13/2018
ms.openlocfilehash: 27e7e846e9ba6ab34d83a084c2589b67a9d5cba9
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557326"
---
# <a name="whats-new-in-powershell-core-61"></a>PowerShell Core 6.1 yenilikler nelerdir?

Seçimi önemli yeni özellikler ve içinde PowerShell Core 6.1 sürümünde değişiklikleri bazıları aşağıdadır.

Ayrıca **ton** boyunca "daha hızlı ve daha kararlı (Ayrıca, birçok ve çok sayıda hata düzeltmesi) PowerShell olun bence olarak"!
Değişikliklerin tam listesi için kullanıma sunduğumuz [github'da changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Ve bazı adları diyoruz sırasında kullandığınız için teşekkür ederiz [tüm topluluğa katkıda bulunanlar](https://github.com/PowerShell/PowerShell/graphs/contributors) yapılması bu sürümde mümkün.

## <a name="net-core-21"></a>.NET core 2.1

PowerShell Core 6.1, sonra .NET Core 2.1 için taşınabilir [Mayıs ayında yayımlanan](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), sonuçta elde edilen çok sayıda PowerShell iyileştirmeleri dahil olmak üzere:

- performans geliştirmeleri (bkz [aşağıda](#performance-improvements))
- Alpine Linux desteği (Önizleme)
- [.NET genel araç desteği](/dotnet/core/tools/global-tools) - PowerShell için Yakında sunulacak
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows Uyumluluk Paketi .NET Core için

Windows üzerinde .NET ekibi sevk [Windows Uyumluluk Paketi .NET Core için](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), bir dizi ekleyen bir derleme kümesi geri Windows üzerinde .NET Core için API kaldırıldı.

Böylece bunlar üzerinde kullanılabilir olan tüm modülleri veya bu API'leri kullanan betikler güvenebilirsiniz PowerShell Core 6.1 sürümüne Windows Uyumluluk Paketi ekledik.

Windows Uyumluluk Paketi kullanmak PowerShell Core sağlayan **ile Windows 10 Ekim 2018 sevk 1900'den fazla cmdlet Update ve Windows Server 2019**.

## <a name="performance-improvements"></a>Performans iyileştirmeleri

PowerShell Core 6.0 bazı önemli performans geliştirmeleri yaptık.
PowerShell Core 6.1 belirli işlemleri hızını geliştirmeye devam ediyor.

Örneğin, `Group-Object` 66 oranında hatalarının çözümünü hızlandırdı:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Süre (sn)   | 25.178                 | 19.653              | 6.641               |
| Hız yükselmesi (%) | YOK                    | %21,9               | %66.2               |

Benzer şekilde, bunun gibi sıralama senaryoları % 15'den fazla geliştirildi:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Süre (sn)   | 12.170                 | 8.493               | 7.08                |
| Hız yükselmesi (%) | YOK                    | %30.2               | %16.6               |

`Import-Csv` Ayrıca önemli ölçüde sonra bir gerileme Windows Powershell'den hatalarının çözümünü hızlandırdı.
Aşağıdaki örnek, bir test CSV 26,616 satırlar ve sütunlarla altı kullanır:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Süre (sn)   | 0.441                  | 1.069               | 0,268                  |
| Hız yükselmesi (%) | YOK                    | -%142.4             | %74.9 (WPS %39.2) |

Son olarak, JSON'a dönüştürme `PSObject` % 50'den itibaren Windows PowerShell hatalarının çözümünü hızlandırdı.
Aşağıdaki örnek, yaklaşık 2 MB test JSON dosyasını kullanır:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Süre (sn)   | 0.259                  | 0.577               | 0,125                  |
| Hız yükselmesi (%) | YOK                    | -%122.8             | %78.3 (WPS %51.7) |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a>Denetleme `system32` Windows üzerinde uyumlu gelen modüller için

Windows 10 1809 güncelleştirmesi ve Windows Server 2019, gelen PowerShell modülleri bunları PowerShell Core ile uyumlu olarak işaretlemek için bir dizi güncelleştirdik.

PowerShell Core 6.1 başlatıldığında otomatik olarak içerecektir `$windir\System32` parçası olarak `PSModulePath` ortam değişkeni.
Ancak, yalnızca modüllerle kullanıma sunduğu `Get-Module` ve `Import-Module` varsa kendi `CompatiblePSEdition` ile uyumlu olarak işaretlenmiş `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Hangi rollerin ve özelliklerin yüklü bağlı olarak farklı kullanılabilir modüllerin görebilirsiniz.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Kullanarak tüm modülleri göstermek için bu davranışı geçersiz kılabilirsiniz `-SkipEditionCheck` parametresi geçin.
Ayrıca ekledik bir `PSEdition` için tablo çıkışına özelliği.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Bu davranışı hakkında daha fazla bilgi için kullanıma [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/2-Draft-Accepted/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Markdown cmdlet'leri ve işleme

Markdown temel biçimlendirme ile okunabilir düz metin belgeleri oluşturmak için standart bir HTML'e işlenebilecek ' dir.

Bazı cmdlet'ler konsolunda, Markdown belgeleri işlemek ve dönüştürmek izin 6.1 ekledik dahil olmak üzere:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Örneğin, `Show-Markdown` konsolunda bir Markdown dosyası oluşturur:

![Örnek Markdown Göster](./images/markdown_example.png)

Bu cmdlet'ler nasıl çalıştığı hakkında daha fazla bilgi için kullanıma [bu RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Deneysel özellik bayrakları

Deneysel özellik bayraklarını sonlandırılan henüz özelliklerini etkinleştirme olanağı verir.
Bu Deneysel özelliklerin desteklenmez ve hatalar içerebilir.

' Deki bu özellik hakkında daha fazla bilgi [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Web cmdlet'i geliştirmeleri

Performanstan @markekraus, bizim web cmdlet'leri için tam bir slew geliştirmeler yapıldı: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
ve [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [Çekme isteği #6109](https://github.com/PowerShell/PowerShell/pull/6109) -UTF-8 için kodlama kümesi varsayılan `application-json` yanıtları
- [Çekme isteği # 6018 oluşturun](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` izin vermek için parametre `Content-Type` standartlarıyla uyumlu olmayan üst bilgileri
- [Çekme isteği #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` desteklemek için parametre Basitleştirilmiş `multipart/form-data` desteği
- [Çekme isteği #6338](https://github.com/PowerShell/PowerShell/pull/6338) - uyumlu, büyük küçük harf duyarsız ilişkisi anahtarlarını işleme
- [Çekme isteği #6447](https://github.com/PowerShell/PowerShell/pull/6447) -ekleme `-Resume` web cmdlet'leri için parametre

## <a name="remoting-improvements"></a>Uzaktan iletişimini geliştirmeleri

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a>PowerShell Direct PowerShell Core kullanmayı dener

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) PowerShell ve bir Hyper-V VM ağ bağlantısı olmayan veya diğer uzaktan yönetim hizmetlere bağlanmasına olanak sağlayan Hyper-V özelliğidir.

Geçmişte, PowerShell Direct VM'ye gelen Windows PowerShell örneğini kullanarak bağlı.
Şimdi, PowerShell Direct önce herhangi bir kullanılabilir kullanarak bağlanmayı dener `pwsh.exe` üzerinde `PATH` ortam değişkeni.
Varsa `pwsh.exe` değilse kullanılabilir, PowerShell Direct geri kullanmaya döner `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` Şimdi Önizleme sürümleri için ayrı bir uzak uç noktası oluşturur

`Enable-PSRemoting` Şimdi iki uzaktan oturum yapılandırmaları oluşturur:

- Bir PowerShell ana sürümü. Örneğin,`PowerShell.6`. Bağlı "Sistem genelinde" PowerShell 6 oturum yapılandırması alt sürüm güncelleştirmeleri arasında yararlandı bu endpoint
- Örneğin bir sürüme özgü oturum yapılandırması: `PowerShell.6.1.0`

Bu davranış, aynı makinede birden çok PowerShell 6 sürümlerinin yüklendiğini ve erişilebilir olmasını istiyorsanız kullanışlıdır.

Ayrıca, Önizleme sürümlerini PowerShell artık kendi uzaktan iletişim oturum yapılandırmaları çalıştırdıktan sonra elde `Enable-PSRemoting` cmdlet:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

Çıkış önce WinRM ayarlamadıysanız farklı olabilir.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Ardından Önizleme ayrı PowerShell oturum yapılandırmaları görebilir ve PowerShell 6'ın ve her belirli bir sürümü için kararlı oluşturur.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>`user@host:port` SSH için desteklenen söz dizimleri

SSH istemcileri genellikle bir bağlantı dizesi şu biçimde desteklemek `user@host:port`.
' Nın eklenmesiyle SSH bir protokol olarak PowerShell uzaktan iletişim için bağlantı dizesinin bu biçimi desteği ekledik:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Üzerinde Windows Gezgini Kabuk bağlam menüsü eklemeye MSI seçeneği

Performanstan @bergmeisterartık Windows bağlam menüsünden etkinleştirebilirsiniz. Artık sistem genelinde yüklemenizin PowerShell 6.1, Windows Gezgini'nde herhangi bir klasörden açabilirsiniz:

![PowerShell 6 Kabuk bağlam menüsü](./images/shell_context_menu.png)

## <a name="goodies"></a>İlgi çekici Özellikler

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Windows kısayol atlama listesinde yönetici olarak çalıştır"

Performanstan @bergmeister, PowerShell Core kısayolun atlama listesi artık "Yönetici olarak çalıştır" içerir:

![PowerShell 6 atlama listesinde yönetici olarak çalıştırın](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` Önceki dizinine döndürür

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Ya da Linux üzerinde:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Ayrıca, `cd --` değişikliklerini `$HOME`.

### `Test-Connection`

Performanstan @iSazonov, [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet'i, PowerShell Core için unity'nin.

### <a name="update-help-as-non-admin"></a>`Update-Help` Yönetici olmayan

Popüler isteğe bağlı olarak `Update-Help` artık yönetici olarak çalıştırılması gerekir.
`Update-Help` artık bir kullanıcı kapsamlı klasöre Yardım kaydetmek için varsayılan olarak.

### <a name="new-methodsproperties-on-pscustomobject"></a>Yeni yöntemler/özellikler hakkında `PSCustomObject`

Performanstan @iSazonov, yeni yöntemleri ve özellikleri ekledik `PSCustomObject`.
`PSCustomObject` artık bir `Count` / `Length` öğe sayısını veren özellik.

Bu örneklerin ikisi de `2` sayısı arttıkça `PSCustomObjects` koleksiyondaki.

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

Bu iş yöntemlerine `ForEach` ve `Where` çalıştırmak ve filtrelemek olanak sağlayan yöntemleri `PSCustomObject` öğeleri:

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

Performanstan @SimonWahlin, ekledik `-Not` parametresi `Where-Object`.
Artık bir nesnede bir işlem hattı olmayan-bulunup bulunmadığını bir özelliği ya da null veya boş özellik değeri filtreleyebilirsiniz.

Örneğin, bu komut, tanımlanan tüm bağımlı hizmetlerin olmayan tüm hizmetleri döndürür:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` BOM daha az UTF-8 belgesi oluşturur

Güncelleştirdik BOM daha az UTF-8'PowerShell 6. 0'de alındığında, `New-ModuleManifest` yerine UTF-16 bir BOM daha az UTF-8 belge oluşturmak için cmdlet'i.

### <a name="conversions-from-psmethod-to-delegate"></a>Temsilci PSMethod öğesinden dönüştürme

Performanstan @powercode, artık dönüştürülmesi destekliyoruz bir `PSMethod` içinde bir temsilci.
Bu sayede geçirme gibi şeyleri `PSMethod` `[M]::DoubleStrLen` olarak bir temsilci değerde `[M]::AggregateString`:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Bu değişiklikle ilgili daha fazla bilgi için kullanıma [çekme isteği #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Standart sapma `Measure-Object`

Performanstan @CloudyDino, ekledik bir `StandardDeviation` özelliğini `Measure-Object`:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Performanstan @maybe-hello-world, `Get-PfxCertificate` artık `Password` alan parametresi bir `SecureString`. Bu, etkileşimli olmayan kullanmanıza olanak sağlar:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Kaldırılmasını `more` işlevi

Geçmişte, bir işlev üzerinde adlı Windows PowerShell sevk `more` kaydırılan `more.com`.
Bu işlev artık kaldırılmıştır.

Ayrıca `help` işlevi değiştirilen kullanılacak `more.com` Windows ya da sistemin varsayılan çağrı tarafından belirtilen `$env:PAGER` Windows dışı platformlarda.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` artık bu sürücüye geçerli çalışma dizininde kullanıcıları döndürür

Daha önce kullanarak `Set-Location` veya `cd` kullanıcılar söz konusu sürücünün varsayılan konuma gönderilen bir PSDrive penceresine dönün.

Performanstan @mcbobke, kullanıcıların son bilinen geçerli çalışma dizini için artık bu oturum için gönderilir.

### <a name="windows-powershell-type-accelerators"></a>Windows PowerShell türü Hızlandırıcılar

Windows PowerShell'de, iş ile ilgili kendi türleri daha kolay hale getirmek için aşağıdaki türü Hızlandırıcılar ekledik:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Bu tür Hızlandırıcıları PowerShell 6'da bulunmayan, ancak Windows üzerinde çalışan PowerShell 6.1 eklenmiştir.

Bu tür AD kolayca oluşturulmasında yararlı olan ve WMI nesneleri.

Örneğin, LDAP kullanarak sorgulayabilirsiniz:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

Bu örneklerin her ikisi Win32_OperatingSystem CIM nesnesi oluşturun:

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp` diğer tüm `-LiteralPath` parametreleri

Performanstan @kvprasoon, artık bir parametre diğer adını sahibiz `-lp` sahip tüm yerleşik PowerShell cmdlet'lerinin bir `-LiteralPath` parametresi.

## <a name="breaking-changes"></a>Bozucu değişiklikler

### <a name="msi-based-installation-paths-on-windows"></a>Windows MSI tabanlı yükleme yollarında

Windows üzerinde MSI paketi artık aşağıdaki yola yüklenir:

- `$env:ProgramFiles\PowerShell\6\` 6.x kararlı yüklemek için
- `$env:ProgramFiles\PowerShell\6-preview\` 6.x Önizleme yüklemek için

Bu değişiklik, PowerShell Core Microsoft Update tarafından güncelleştirilmiş/hizmet sağlar.

Daha fazla bilgi için kullanıma [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Telemetri yalnızca bir ortam değişkeni ile devre dışı bırakılabilir

PowerShell Core başlatıldığında temel telemetri verilerini Microsoft'a gönderir. Veriler, işletim sistemi adı, işletim sistemi sürümü ve PowerShell sürümünü içerir. Bu veriler nerede PowerShell kullanılır ve yeni özellikler ve düzeltmeler öncelik sağlıyor ortamları daha iyi anlamak sağlıyor.

Çevirme bu telemetri için ortam değişkenini ayarlamak `POWERSHELL_TELEMETRY_OPTOUT` için `true`, `yes`, veya `1`. Dosya silme işlemi artık desteklemiyoruz `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` telemetri devre dışı bırakmak için.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Temel kimlik doğrulaması üzerinden PowerShell uzaktan iletişimini HTTP UNIX platformlarda izin verilmiyor

Şifrelenmemiş trafik kullanımını önlemek için PowerShell uzaktan iletişimini Unix platformlarında NTLM/anlaşma ya da HTTPS kullanımını gerektirir.

Bu değişiklikler hakkında daha fazla bilgi için kullanıma [çekme isteği #6799](https://github.com/PowerShell/PowerShell/pull/6799).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Kaldırılan `VisualBasic` desteklenen dilde Add-Type olarak

Geçmişte, Visual Basic kod kullanarak derleme `Add-Type` cmdlet'i.
Visual Basic ile kullanılan nadiren `Add-Type`. PowerShell boyutunu azaltmak için bu özelliği kaldırdık.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Kullanımları temizlendi `CommandTypes.Workflow` ve `WorkflowInfoCleaned`

Bu değişiklikler hakkında daha fazla bilgi için kullanıma [çekme isteği #6708](https://github.com/PowerShell/PowerShell/pull/6708).