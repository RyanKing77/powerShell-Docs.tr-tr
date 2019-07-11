---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA'da raporlama ve denetleme
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726746"
---
# <a name="auditing-and-reporting-on-jea"></a>JEA'da raporlama ve denetleme

JEA dağıttıktan sonra düzenli olarak bir JEA yapılandırma denetim gerekir. Yardımcı denetim doğru kişilerin JEA uç noktasına erişebildiğinden ve atanan rollerinin hala uygun değerlendirin.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Bir makinede kayıtlı JEA oturumu bulun

Hangi JEA oturumlarının bir makinede kayıtlı denetlemek için kullanmak [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.

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

Uç noktası için etkin hakları listelenen **izni** özelliği. Bu kullanıcılar JEA uç noktasını bağlamak hakkına sahiptir. Ancak, roller ve erişim sahibi oldukları komutları tarafından belirlenir **RoleDefinitions** özelliğinde [oturum yapılandırma dosyası](session-configurations.md) uç noktasını kaydetmek için kullanıldı. Genişletin **RoleDefinitions** kayıtlı bir JEA uç noktası rolü eşlemelerin değerlendirmek için özellik.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Makinede kullanılabilir rol işlevleri Bul

JEA alır rol özelliklerinden `.psrc` depolanan dosyaların **RoleCapabilities** klasörün içinde bir PowerShell modülü. Aşağıdaki işlev bir bilgisayar üzerinde kullanılabilen tüm rol özellikleri bulur.

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
> Bu işlev sonuçlardan sırasını mutlaka aynı adlı birden çok rol işlevleri paylaşırsanız, hangi rol işlevleri seçilir sırası değildir.

## <a name="check-effective-rights-for-a-specific-user"></a>Belirli bir kullanıcı için etkin haklarını denetleyin

[Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet'i, bir kullanıcının grup üyeliklerini temel alan bir JEA uç noktası kullanılabilir tüm komutları numaralandırır.
Çıkışı `Get-PSSessionCapability` çalıştıran belirtilen kullanıcı için aynı `Get-Command -CommandType All` bir JEA oturumda.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Bu cmdlet, kullanıcılarınızın bunları ek JEA hakkı grupların kalıcı üyesi değilseniz, bu ek izinleri yansıtmayabilir. Bu kullanırken, just-ın-time ayrıcalıklı erişim yönetimi sistemleri, kullanıcıların geçici olarak bir güvenlik grubuna ait olur. Rolleri ve özellikleri, kullanıcıların yalnızca kullanıcıların işlerini başarıyla yapmak için gereken erişim düzeyini aldığından emin olmak için kullanıcı eşleme dikkatlice değerlendirin.

## <a name="powershell-event-logs"></a>PowerShell olay günlükleri

Sistemde oturum modülü veya betik bloğu etkinleştirilirse, bir kullanıcı bir JEA oturumda çalışan her komut için Windows olay günlüğündeki olayları görebilirsiniz. Bu olayları bulmak için açın **Microsoft-Windows-PowerShell/Operational** olay günlüğü ve olay kimliği ile olayları arayın **4104**.

Her olay günlüğü girişi, komutun çalıştırıldığı oturumu hakkında bilgi içerir. JEA oturumlarında, olay hakkında bilgiler içerir **ConnectedUser** ve **farklıkullanıcı**. **ConnectedUser** JEA oturumu oluşturan gerçek kullanıcı. **Farklıkullanıcı** JEA komutu yürütmek için kullanılan hesaptır.

Uygulama olay günlüklerini göster tarafından yapılan değişiklikleri **farklıkullanıcı**. Modülü ve komut dosyası ünlüğe kaydetme etkin olan belirli bir komut çağrısı geri izleme için gerekli olacak şekilde **ConnectedUser**.

## <a name="application-event-logs"></a>Uygulama olay günlükleri

Dış uygulamalarla etkileşim kuran bir JEA oturumunda komutları çalıştırmak veya hizmetleri olayları kendi olay günlüklerine Kaydet. PowerShell günlükleri ve dökümler aksine, diğer günlük mekanizmaları JEA oturumun bağlı olan kullanıcı yakalamayın. Bunun yerine, bu uygulamalar, yalnızca sanal Çalıştır kullanıcı oturum.
Başvurun gerek kimin komutun çalıştığını belirlemek için bir [oturumu döküm](#session-transcripts) veya PowerShell olay günlükleri uygulama olay günlüğünde gösterilen kullanıcı ve saat ile ilişkilendirin.

WinRM günlük Çalıştır bağlanan kullanıcının bir uygulama olay günlüğüne kullanıcılara bağıntısını da yardımcı olabilir. Olay Kimliği **193** içinde **Microsoft Windows Windows Uzaktan Yönetimi/Operational** günlük her yeni JEA için güvenlik tanımlayıcısı (SID) ve hem bağlanan kullanıcı ve farklı çalıştır hesabı adını kullanıcı olarak kaydeder oturumu.

## <a name="session-transcripts"></a>Oturum dökümleri

Jea'yı her bir kullanıcı oturumu için bir döküm oluşturmak için yapılandırılmışsa, her kullanıcının eylemleri metin kopyasını belirtilen klasörde depolanır.

Aşağıdaki komutu (Yönetici) olarak tüm döküm dizinleri bulur.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Transkript her zaman oturum başlatıldığında, oturum ve JEA kimliği atanmış bağlı kullanıcı hakkında bilgi ile başlar.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Transkripti gövdesinin kullanıcı çağrılan her komut hakkında bilgi içerir. Kullanılan komut söz dizimi nedeniyle PowerShell uzaktan iletişim için komutları dönüştürülme biçimini JEA oturumlarda kullanılamıyor. Ancak, yine de yürütülen etkili komut belirleyebilirsiniz. Çalıştıran bir kullanıcıdan bir örnek dökümü kod parçacığı aşağıda verilmiştir `Get-Service Dns` bir JEA oturumda:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

A **CommandInvocation** satır, bir kullanıcının her komut için yazılır. **ParameterBindings** her parametresi ve değeri bu komutla birlikte kaydedin. Önceki örnekte görebileceğiniz gibi parametre **adı** sağlanan değerle **Dns** için `Get-Service` cmdlet'i.

Her çıkış komutunu da Tetikleyiciler bir **CommandInvocation**, genellikle `Out-Default`. **Inputobject** , `Out-Default` komuttan PowerShell nesne döndürülür. Bu nesnenin ayrıntılarını yazdırılır aşağıda yakından kullanıcı gördünüz yakından taklit eden birkaç satır kod.

## <a name="see-also"></a>Ayrıca bkz.

[*PowerShell mavi takımın ♥* güvenlik blog gönderisi](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
