---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: Denetim ve JEA üzerinde raporlama
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188861"
---
# <a name="auditing-and-reporting-on-jea"></a>Denetim ve JEA üzerinde raporlama

> Uygulandığı öğe: Windows PowerShell 5.0

JEA dağıtıldıktan sonra düzenli olarak JEA yapılandırma denetim isteyeceksiniz.
Bu, doğru kişilerin JEA endpoint erişiminiz varsa ve atanan rollerinin hala uygun değilse değerlendirmenize yardımcı olur.

Bu konuda bir JEA uç noktası denetim çeşitli yolları açıklanmaktadır.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Bir makinede kayıtlı JEA oturumları Bul

Hangi JEA oturumlarının bir makinede kayıtlı denetlemek için kullanın [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Uç noktası için etkili haklar "İzni" özelliğinde listelenir.
Bu kullanıcılar JEA uç noktası, hangi rollerin ancak (ve uzantılarının, komutları) bağlanmak için izniniz "RoleDefinitions" alanına göre belirlenir için erişime sahip oldukları [oturum yapılandırma dosyası](session-configurations.md) kaydetmek için kullanıldı uç noktası.

Kayıtlı bir JEA uç noktası rolü eşlemelerin "RoleDefinitions" özelliği verilerde genişleterek değerlendirebilirsiniz.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Makinede kullanılabilir rol özelliklerini Bul

Geçerli bir PowerShell modülü içinde "RoleCapabilities" klasöründe depolanıyorsa Rol Yetenek dosyaları yalnızca JEA tarafından kullanılır.
Bir bilgisayarda kullanılabilen tüm rol özellikleri kullanılabilir modüllerin listesini arayarak bulabilirsiniz.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> Bu işlev sonuçlarından sırasını mutlaka birden çok rol özellikleri aynı adı paylaşan durumunda hangi rolü özellikleri seçilecektir sırası değildir.

## <a name="check-effective-rights-for-a-specific-user"></a>Belirli bir kullanıcı için etkin haklarını denetleme

JEA uç nokta ayarlamayı ayarladıktan sonra hangi komutların JEA oturumda belirli bir kullanıcı tarafından kullanılabilir denetlemek isteyebilirsiniz.
Kullanabileceğiniz [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) geçerli grup üyeliklerini JEA oturumu başlatmak için olsaydı bir kullanıcıya uygulanabilir komutların tümünü numaralandırılamıyor.
Çıktısını `Get-PSSessionCapability` çalıştıran belirtilen kullanıcı için aynı `Get-Command -CommandType All` JEA oturumunda.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Kullanıcılarınızın bunları ek JEA haklar gruplarını kalıcı üyesi değilseniz, bu cmdlet bu ek izinler yansıtmayabilir.
Bu genellikle yalnızca zaman ayrıcalıklı erişim yönetimi sistemleri geçici olarak bir güvenlik grubuna ait yapmalarına izin vermek için kullanırken durumdur.
Kullanıcıları rollere eşleme ve kullanıcılar yalnızca en az miktarda işlerini başarıyla yapmak için gerekli komutları erişimi aldıklarından emin olmak için her rolün içeriği her zaman dikkatlice değerlendirin.

## <a name="powershell-event-logs"></a>PowerShell olay günlükleri

Sistemde oturum modülü ve/veya betik bloğu etkinleştirilirse, bir kullanıcı kendi JEA oturumlarında çalışan her komut için Windows olay günlüklerini olayları bulmak kuramaz.
Bu olayları bulmak için Windows Olay Görüntüleyicisi'ni açın, gitmek **Microsoft-Windows-PowerShell/Operational** olay günlüğü ve olay kimliği olan olaylar için Görünüm **4104**.

Her olay günlüğü girişi komutu çalıştırıldı oturumu hakkında bilgi içerir.
JEA oturumları için bu önemli hakkında bilgiler içerir **ConnectedUser**, JEA oturum oluşturan gerçek kullanıcı olduğu yanı sıra **farklıkullanıcı** JEA için kullanılan hesabı tanımlayan komutu yürütün.
Uygulama olay günlükleri bu nedenle dökümleri sahip farklıkullanıcı tarafından yapılan değişiklikleri gösterir veya modül/komut dosyası günlüğü etkin bir kullanıcıya geri belirli komut çağırma izleme yapabilmek önemlidir.

## <a name="application-event-logs"></a>Uygulama olay günlükleri

Bir dış uygulama veya hizmet ile etkileşime giren JEA oturumda bir komut çalıştırdığınızda, bu uygulamaları kendi olay günlüklerini olayları oturum açabilir.
PowerShell günlükleri ve dökümleri, aksine diğer günlük mekanizmaları JEA oturumunun bağlı olan kullanıcı yakalamaz ve bunun yerine yalnızca Çalıştır sanal kullanıcı veya grup yönetilen hizmet hesabı oturum.
Kimin komutun çalıştığını belirlemek için başvurun gerekecektir bir [oturum dökümü](#session-transcripts) veya PowerShell olay günlüklerini saat ve uygulama olay günlüğünde gösterilen kullanıcı ile ilişkilendirilmesi.

Günlük ayrıca ilişkilendirmenize yardımcı olur WinRM bağlanan kullanıcı bir uygulama olay günlüğünde kullanıcılarla farklı çalıştır.
Olay Kimliği **193** içinde **Microsoft Windows Windows Uzaktan Yönetimi/Operational** günlük kayıtlarının güvenlik tanımlayıcısı (SID) ve hesap adı için bağlanan kullanıcı ve kullanıcı olarak her zaman bir JEA çalıştırın. oturum oluşturulur.

## <a name="session-transcripts"></a>Oturum dökümleri

Her bir kullanıcı oturumu için bir dökümü oluşturmak için JEA yapılandırdıysanız, her kullanıcının Eylemler metin kopyasına belirtilen klasörde depolanır.

Tüm dökümü dizinleri bulmak için aşağıdaki komutu bilgisayarda yönetici olarak çalıştır JEA ile yapılandırılmış:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Oturum, başlatıldığında oturumu ve hangi JEA kimlik atanmış bağlı hangi kullanıcı hakkında bilgi içeren her dökümü başlatır.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Dökümü gövdesinde kullanıcının çağrılan her komutu hakkında bilgileri günlüğe kaydedilir.
Yürütüldü etkili komutu hala belirleyebilir ancak kullanıcı çalıştırdı komut söz dizimi JEA oturumlarda komutları PowerShell uzaktan iletişim için dönüştürülen şekilde nedeniyle kullanılamıyor.
Bir örnek dökümü parçacığı çalıştıran bir kullanıcıdan aşağıdadır `Get-Service Dns` JEA oturumunda:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Bir kullanıcı çalıştıran her komut için bir "CommandInvocation" satır cmdlet açıklayan yazılır veya kullanıcının çağrılan işlev.
Her bir parametre ve komutu ile sağlanan değer hakkında bilgi için her CommandInvocation ParameterBindings izleyin.
Yukarıdaki örnekte, "adı" parametresi "Dns" değeri "Get-Service" cmdlet için sağlanan görebilirsiniz.

Her komut çıktısı ayrıca bir CommandInvocation genellikle dışarı varsayılan olarak tetikler.
Inputobject Out-Default komuttan döndürülen PowerShell nesnesidir.
Bu nesnenin ayrıntılarını yazdırılır altında hangi kullanıcı görülen yakından mimicking birkaç satır.

## <a name="see-also"></a>Ayrıca bkz:

- [JEA oturumunda denetim kullanıcı eylemleri](audit-and-report.md)
- [*PowerShell ♥ mavi takım* güvenlik blog gönderisi](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)