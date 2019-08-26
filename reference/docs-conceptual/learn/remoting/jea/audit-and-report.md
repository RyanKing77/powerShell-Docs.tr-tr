---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA 'da denetim ve raporlama
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017926"
---
# <a name="auditing-and-reporting-on-jea"></a>JEA 'da denetim ve raporlama

JEA 'yı dağıttıktan sonra, JEA yapılandırmasını düzenli olarak denetlemeniz gerekir. Denetim, doğru kişilerin JEA uç noktasına erişiminin olduğunu ve atanan rollerinin hala uygun olduğunu değerlendirmenize yardımcı olur.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Bir makinede kayıtlı JEA oturumlarını bulma

Bir makineye hangi JEA oturumlarının kaydedildiğini denetlemek için [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 'ini kullanın.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Uç nokta için geçerli haklar, **izin** özelliğinde listelenir. Bu kullanıcıların JEA uç noktasına bağlanma hakkı vardır. Ancak, erişimi olan roller ve komutlar, uç noktasını kaydetmek için kullanılan [oturum yapılandırma dosyasındaki](session-configurations.md) **roledefinitions** özelliği tarafından belirlenir. Kayıtlı bir JEA uç noktasındaki rol eşlemelerini değerlendirmek için **Roledefinitions** özelliğini genişletin.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Makinede kullanılabilir rol yeteneklerini bul

Jea, bir PowerShell modülü içindeki `.psrc` **rolecapabilities** klasöründe depolanan dosyalardan rol özellikleri alır. Aşağıdaki işlev bir bilgisayardaki kullanılabilir tüm rol yeteneklerini bulur.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> Bu işlevden sonuçların sırası, birden çok rol özelliği aynı adı paylaşıyorsa rol yeteneklerinin seçilme sırası olması gerekir.

## <a name="check-effective-rights-for-a-specific-user"></a>Belirli bir kullanıcı için geçerli hakları denetleme

[Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet 'i, BIR Jea uç noktasındaki kullanılabilir tüm komutları bir kullanıcının grup üyeliğine göre numaralandırır.
Çıkışı `Get-PSSessionCapability` , bir Jea oturumunda çalışan `Get-Command -CommandType All` belirtilen kullanıcı ile aynıdır.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Kullanıcılarınız, bunlara ek JEA hakları verecek grupların kalıcı üyeleri değilse, bu cmdlet bu ek izinleri yansıtmayabilir. Bu durum, kullanıcıların geçici olarak bir güvenlik grubuna ait olmasını sağlamak için tam zamanında ayrıcalıklı erişim yönetimi sistemleri kullanılırken meydana gelir. Kullanıcıların yalnızca işlerini başarılı bir şekilde yapması için gereken erişim düzeyini aldığından emin olmak için kullanıcıların rol ve yeteneklere eşlemesini dikkatle değerlendirin.

## <a name="powershell-event-logs"></a>PowerShell olay günlükleri

Sistemde modül veya betik bloğu günlüğünü etkinleştirdiyseniz, bir kullanıcının JEA oturumunda çalıştırdığı her komut için Windows olay günlüklerinde olayları görebilirsiniz. Bu olayları bulmak için **Microsoft-Windows-PowerShell/işletimsel** olay günlüğünü açın ve olay kimliği **4104**olan olayları arayın.

Her olay günlüğü girişi, komutun çalıştırıldığı oturum hakkındaki bilgileri içerir. JEA oturumlarında, olay **connecteduser** ve **RunAsUser**hakkındaki bilgileri içerir. **Connecteduser** , Jea oturumunu oluşturan gerçek Kullanıcı. **RunAsUser** , komutu yürütmek için kullanılan Jea hesabıdır.

Uygulama olay günlükleri, **RunAsUser**tarafından yapılan değişiklikleri gösterir. Bu nedenle, belirli bir komut çağrısını **Connecteduser**'a geri izlemek için modül ve betik günlüğü 'nün etkin olması gerekir.

## <a name="application-event-logs"></a>Uygulama olay günlükleri

Dış uygulamalarla veya hizmetlerle etkileşime geçen bir JEA oturumunda çalıştırılan komutlar, olayları kendi olay günlüklerine kaydeder. PowerShell günlüklerinin ve döküm dosyalarından farklı olarak, diğer oturum açma mekanizmaları JEA oturumunun bağlı kullanıcısını yakalamaz. Bunun yerine, bu uygulamalar yalnızca sanal farklı çalıştır kullanıcısını günlüğe kaydeder.
Komutu kimin çalıştırdığını öğrenmek için, bir [oturum döküm dosyasına](#session-transcripts) danışmanız veya PowerShell olay günlüklerinin uygulama olay günlüğünde gösterilen zaman ve kullanıcıyla ilişkilendirilmesi gerekir.

WinRM günlüğü aynı zamanda bir uygulama olay günlüğündeki bağlanan kullanıcıyla farklı çalıştır kullanıcılarını ilişkilendirmenize yardımcı olabilir. **Microsoft-Windows-Windows Uzaktan Yönetimi/işletimsel** GÜNLÜĞÜNDE olay kimliği **193** , hem bağlanan kullanıcı hem de her yeni Jea oturumunda Kullanıcı olarak Çalıştır ' ın güvenlik tanımlayıcısını (SID) ve hesap adını kaydeder.

## <a name="session-transcripts"></a>Oturum yazılı betikleri

JEA 'yı her Kullanıcı oturumu için bir döküm oluşturacak şekilde yapılandırdıysanız, her kullanıcının eylemlerinin bir metin kopyası belirtilen klasörde depolanır.

Aşağıdaki komut (yönetici olarak) tüm döküm dizinlerini bulur.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Her döküm, oturum başladığı saat, oturuma bağlanan kullanıcı ve kendisine hangi JEA kimliği atandığını belirten bilgilerle başlar.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Döküm gövdesi kullanıcının çağırılabilen her komutla ilgili bilgiler içerir. PowerShell uzaktan iletişim için, komutların dönüştürülebildiğinden, kullanılan komutun tam sözdizimi JEA oturumlarında kullanılamaz. Ancak, yürütülen etkin komutu yine de belirleyebilirsiniz. Aşağıda, bir Jea oturumunda çalışan `Get-Service Dns` kullanıcıdan bir örnek döküm kod parçacığı verilmiştir:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Bir kullanıcı tarafından çalıştırılan her komut için bir **Commandinvocation** satırı yazılır. **ParameterBindings** , komutuyla sağlanan her parametreyi ve değeri kaydeder. Önceki örnekte, parametre `Get-Service` **adının** cmdlet için değeri **DNS** ile birlikte sağlanmış olduğunu görebilirsiniz.

Her komutun çıktısı aynı zamanda bir **Commandinvocation**(genellikle olarak `Out-Default`) tetikler. **InputObject** `Out-Default` , komutundan döndürülen PowerShell nesnesidir. Bu nesnenin ayrıntıları aşağıda birkaç satır yazdırılır, bu da kullanıcının gördükiyle ilgili daha yakından bir şeydir.

## <a name="see-also"></a>Ayrıca bkz.

[Güvenlik *Için mavi ekip blog gönderisi ♥ PowerShell*](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
