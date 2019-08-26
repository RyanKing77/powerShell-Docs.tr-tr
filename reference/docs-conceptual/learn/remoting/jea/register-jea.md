---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA yapılandırmalarının kaydı yapılıyor
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017870"
---
# <a name="registering-jea-configurations"></a>JEA yapılandırmalarının kaydı yapılıyor

[Rol olanaklarınız](role-capabilities.md) ve [oturum yapılandırma dosyanız](session-configurations.md) oluşturulduktan sonra, son adım Jea uç noktasını kaydetmek olur. JEA uç noktasının sistemle kaydı, uç noktanın kullanıcılar ve otomasyon motorları tarafından kullanılabilmesini sağlar.

## <a name="single-machine-configuration"></a>Tek makineli yapılandırma

Küçük ortamlarda, oturum yapılandırma dosyasını [register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet 'ini kullanarak kaydederek Jea 'yı dağıtabilirsiniz.

Başlamadan önce, aşağıdaki önkoşulların karşılandığından emin olun:

- Bir veya daha fazla rol oluşturulup bir PowerShell modülünün **Rolecapabilities** klasörüne yerleştirildi.
- Bir oturum yapılandırma dosyası oluşturuldu ve test edildi.
- JEA yapılandırmasını kaydeden Kullanıcı sistemde yönetici haklarına sahiptir.
- JEA uç noktanız için bir ad seçtiniz.

Kullanıcılar JEA kullanarak sisteme bağlandıklarında JEA uç noktasının adı gereklidir. [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 'i bir sistemdeki uç noktaların adlarını listeler. İle `microsoft` başlayan uç noktalar genellikle Windows ile birlikte gönderilir. `microsoft.powershell` Uç nokta, uzak bir PowerShell uç noktasına bağlanırken kullanılan varsayılan uç noktadır.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Uç noktasını kaydetmek için aşağıdaki komutu çalıştırın.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Önceki komut, sistem üzerindeki WinRM hizmetini yeniden başlatır. Bu, tüm PowerShell uzaktan iletişim oturumlarını ve devam eden DSC yapılandırmasını sonlandırır. İş operasyonlarının kesintiye uğramaması için komutunu çalıştırmadan önce üretim makinelerinizi çevrimdışına almanız önerilir.

Kayıttan sonra, [JEA kullanmaya](using-jea.md)hazırsınız demektir. Oturum yapılandırma dosyasını dilediğiniz zaman silebilirsiniz. Yapılandırma dosyası uç nokta kaydettirildikten sonra kullanılmıyor.

## <a name="multi-machine-configuration-with-dsc"></a>DSC ile çok makineli yapılandırma

JEA 'yı birden çok makineye dağıtırken, en basit dağıtım modeli JEA [Istenen durum yapılandırması (DSC)](/powershell/dsc/overview) kaynağını her makinede hızlı ve tutarlı bir şekilde dağıtmak için kullanır.

JEA 'yı DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olun:

- Bir veya daha fazla rol özelliği yazıldı ve bir PowerShell modülüne eklendi.
- Rolleri içeren PowerShell modülü, her makine tarafından erişilebilen bir (salt okunurdur) dosya paylaşımında depolanır.
- Oturum yapılandırması ayarları belirlendi. JEA DSC kaynağını kullanırken bir oturum yapılandırma dosyası oluşturmanız gerekmez.
- Her makinede yönetim eylemlerine izin veren veya makineleri yönetmek için kullanılan DSC çekme sunucusuna erişim sağlayan kimlik bilgileri vardır.
- [Jea DSC kaynağını](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)indirdiniz.

Hedef makinede veya çekme sunucusunda JEA uç noktanız için bir DSC yapılandırması oluşturun. Bu yapılandırmada, **Ditenoughadministration** DSC kaynağı, oturum yapılandırma dosyasını tanımlar ve **Dosya** kaynağı rol yeteneklerini dosya paylaşımından kopyalar.

Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:

- Rol tanımları
- Sanal hesap grupları
- Grup tarafından yönetilen hizmet hesabı adı
- Döküm dizini
- Kullanıcı sürücüsü
- Koşullu erişim kuralları
- JEA oturumu için başlatma betikleri

Bir DSC yapılandırmasındaki bu özelliklerin her biri için sözdizimi, PowerShell oturum yapılandırma dosyası ile tutarlıdır.

Genel sunucu bakım modülünün örnek DSC yapılandırması aşağıda verilmiştir. Rol özelliklerini `\\myfileshare\JEA` içeren geçerli bir PowerShell modülünün dosya paylaşımında bulunduğunu varsayar.

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Daha sonra, yapılandırma doğrudan [yerel Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) çağırarak veya [çekme sunucusu yapılandırması](/powershell/dsc/pull-server/pullServer)güncelleştirilerek bir sisteme uygulanır.

DSC kaynağı, varsayılan **Microsoft. PowerShell** uç noktasını değiştirmenize de olanak tanır. Değiştirildiğinde kaynak, **Microsoft. PowerShell. Restricted**adlı bir yedekleme uç noktasını otomatik olarak kaydeder. Yedekleme uç noktası, uzaktan yönetim kullanıcılarına ve yerel Yöneticiler grubu üyelerine erişmesine izin veren varsayılan WinRM ACL 'sine sahiptir.

## <a name="unregistering-jea-configurations"></a>JEA yapılandırmalarının kaydı siliniyor

[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet 'ı BIR Jea uç noktasını kaldırır. JEA uç noktasının kaydını silme, yeni kullanıcıların sistemde yeni JEA oturumları oluşturmasını engeller. Aynı zamanda aynı uç nokta adını kullanarak güncelleştirilmiş bir oturum yapılandırma dosyasını yeniden kaydederek bir JEA yapılandırmasını güncelleştirmenize olanak tanır.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> JEA uç noktasının kaydının kaydı, WinRM hizmetinin yeniden başlatılmasına neden olur. Bu, diğer PowerShell oturumları, WMI etkinleştirmeleri ve bazı yönetim araçları da dahil olmak üzere birçok uzaktan yönetim işlemini keser. Yalnızca planlanan bakım pencereleri sırasında PowerShell uç noktalarının kaydını silin.

## <a name="next-steps"></a>Sonraki adımlar

[JEA uç noktasını test etme](using-jea.md)
