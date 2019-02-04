---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA'da raporlama ve denetleme
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688605"
---
# <a name="auditing-and-reporting-on-jea"></a>JEA'da raporlama ve denetleme

> Şunun için geçerlidir: Windows PowerShell 5.0

JEA dağıttıktan sonra düzenli olarak JEA yapılandırmayı denetlemek isteyebilirsiniz.
Bu, doğru kişilerin JEA uç noktasına erişebildiğinden ve atanan rollerinin hala uygun değerlendirmenize yardımcı olur.

Bu konu, bir JEA uç noktası denetleyebilirsiniz çeşitli yolları açıklar.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Bir makinede kayıtlı JEA oturumu bulun

Hangi JEA oturumlarının bir makinede kayıtlı denetlemek için kullanmak [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Uç noktası için etkin hakları "İzni" özelliğinde listelenir.
Bu kullanıcılar JEA uç noktası, ancak hangi rollerin (ve uzantısıyla komutları) bağlanma izniniz "RoleDefinitions" alanı tarafından belirlenir için erişime sahip oldukları [oturum yapılandırma dosyası](session-configurations.md) kaydetmek için kullanılan uç nokta.

Kayıtlı bir JEA uç noktası rolü eşlemelerin "RoleDefinitions" özelliğinde veri genişleterek değerlendirebilirsiniz.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Makinede kullanılabilir rol işlevleri Bul

Geçerli bir PowerShell modülü içinde bir "RoleCapabilities" klasöründe depolanıyorsa rol özellik dosyaları yalnızca JEA tarafından kullanılır.
Tüm rol özellikleri bir bilgisayarda kullanılabilir modüllerin listesini arayarak bulabilirsiniz.

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
> Bu işlev sonuçlardan sırasını mutlaka aynı adlı birden çok rol işlevleri paylaşırsanız, hangi rol işlevleri seçilir sırası değildir.

## <a name="check-effective-rights-for-a-specific-user"></a>Belirli bir kullanıcı için etkin haklarını denetleyin

Bir JEA uç noktası ayarladıktan sonra hangi komutları belirli bir kullanıcıya bir JEA oturumunda kullanılabilir denetlemek isteyebilirsiniz.
Kullanabileceğiniz [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) olsaydı ile geçerli grup üyeliklerini bir JEA oturumu başlatmak için bir kullanıcı için geçerli komutların tümü numaralandırılamadı.
Çıkışı `Get-PSSessionCapability` çalıştıran belirtilen kullanıcı için aynı `Get-Command -CommandType All` bir JEA oturumda.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Bu cmdlet, kullanıcılarınızın bunları JEA ek haklar verilir gruplarının kalıcı üyesi değilseniz, bu ek izinleri yansıtmayabilir.
Bu genellikle kullanıcıların geçici olarak bir güvenlik grubuna ait izin vermek için tam zamanında ayrıcalıklı erişim yönetimi sistemleri kullanılırken geçerlidir.
Rollere kullanıcı eşleme ve kullanıcılar yalnızca komutlar başarıyla işlerini yapmak için gereken en az miktarda erişim aldıklarından emin olmak için her rolün içeriğini her zaman dikkatli bir şekilde değerlendirin.

## <a name="powershell-event-logs"></a>PowerShell olay günlükleri

Sistemde oturum modülü ve/veya betik bloğu etkinleştirilirse, bir kullanıcı JEA oturumlarını çalıştırdığınız her komut için Windows olay günlüklerindeki olaylarını bulmak mümkün olacaktır.
Bu olayları bulmak için Windows Olay Görüntüleyicisi'ni açın, gitmek **Microsoft-Windows-PowerShell/Operational** olay günlüğü ve olay kimliği ile olayları arayın **4104**.

Her olay günlüğü girişi komutun çalıştırıldığı oturumu hakkında bilgi içerir.
JEA oturumları için bu önemli hakkında bilgiler içerir **ConnectedUser**, JEA oturumu oluşturan gerçek kullanıcı olduğu yanı sıra **farklıkullanıcı** JEA için kullanılan hesabı tanımlayan komutu yürütün.
Bu nedenle dökümleri sahip farklıkullanıcı tarafından yapılan değişiklikleri gösterir uygulama olay günlüklerini veya modül/komut dosyası ünlüğe kaydetme etkin bir özel komut çağırma geri kullanıcıya kadar izleyebiliyor olmanız önemlidir.

## <a name="application-event-logs"></a>Uygulama olay günlükleri

Bir dış uygulama veya hizmeti ile etkileşime giren bir JEA oturumda bir komut çalıştırdığınızda, söz konusu uygulamaların kendi olay günlüklerine olayları oturum açabilir.
PowerShell günlükleri ve dökümler, aksine diğer günlük mekanizmaları JEA oturumun bağlı olan kullanıcı yakalamaz ve bunun yerine yalnızca Çalıştır sanal kullanıcı veya grup yönetilen hizmet hesabı günlüğe kaydedecektir.
Kimin komutun çalıştığını belirlemek için başvurun gerekecektir bir [oturumu döküm](#session-transcripts) veya PowerShell olay günlükleri uygulama olay günlüğünde gösterilen kullanıcı ve saat ile ilişkilendirin.

Günlük da ilişkilendirmenize yardımcı olabilir WinRM uygulama olay günlüğüne kullanıcı bağlanan kullanıcı ile çalıştırın.
Olay Kimliği **193** içinde **Microsoft Windows Windows Uzaktan Yönetimi/Operational** günlük kayıtlarının güvenlik tanımlayıcısı (SID) ve hesap için bağlama kullanıcı adı ve kullanıcı olarak bir JEA her defasında Çalıştır oturum oluşturulur.

## <a name="session-transcripts"></a>Oturum dökümleri

Jea'yı her bir kullanıcı oturumu için bir döküm oluşturmak için yapılandırılmışsa, her kullanıcının eylemleri metin kopyasını belirtilen klasörde depolanır.

Tüm döküm dizinleri bulmak için aşağıdaki komutu bilgisayarda yönetici olarak çalıştırın JEA ile yapılandırılmış:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
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

Transkripti gövdesinde kullanıcının çağrılan her komut hakkında bilgileri günlüğe kaydedilir.
Yürütülen etkili komut hala belirleyebilirsiniz ancak kullanıcı çalıştırılan komut söz dizimi JEA oturumlarında komutları PowerShell uzaktan iletişim için dönüştürülme biçimini nedeniyle kullanılamıyor.
Çalıştıran bir kullanıcıdan bir örnek dökümü kod parçacığı aşağıda verilmiştir `Get-Service Dns` bir JEA oturumda:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Bir kullanıcı çalıştırır, her komut için "CommandInvocation" satır cmdlet açıklayan yazılır veya kullanıcının çağrılan işlev.
Her bir parametre ve komutu ile sağlanan değeri hakkında bilgi için her CommandInvocation ParameterBindings izleyin.
Yukarıdaki örnekte, "ad" parametresi ' % s'değeri "Dns" "Get-Service" cmdlet için sağlanan görebilirsiniz.

Her komutun çıktısı da bir CommandInvocation genellikle dışarı varsayılan tetikler.
Inputobject Out-Default, komuttan döndürülen PowerShell nesnedir.
Bu nesnenin ayrıntılarını yazdırılır aşağıda yakından kullanıcı gördünüz yakından taklit eden birkaç satır kod.

## <a name="see-also"></a>Ayrıca bkz.

- [*PowerShell mavi takımın ♥* güvenlik blog gönderisi](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
