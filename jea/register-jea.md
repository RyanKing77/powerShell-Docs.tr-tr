---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA yapılandırmaları kaydediliyor
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726617"
---
# <a name="registering-jea-configurations"></a>JEA yapılandırmaları kaydediliyor

Sonra [rol işlevleri](role-capabilities.md) ve [oturum yapılandırma dosyası](session-configurations.md) , son adım JEA uç noktasını kaydetmek için oluşturulmuştur. Sistemiyle JEA uç noktası kaydediliyor uç nokta kullanıcılar ve Otomasyon motoru tarafından kullanılabilir hale getirir.

## <a name="single-machine-configuration"></a>Tek makine yapılandırması

Küçük ortamlarda oturum yapılandırma dosyası kullanarak kaydederek JEA dağıtabilirsiniz [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet'i.

Başlamadan önce aşağıdaki önkoşulları karşıladığınızdan emin olun:

- Bir veya daha fazla rol oluşturuldu ve bulundukları **RoleCapabilities** bir PowerShell modülü klasörü.
- Bir oturum yapılandırma dosyası oluşturulur ve test.
- Jea'yı yapılandırma kaydetme kullanıcı sistem üzerinde yönetici haklarına sahip.
- JEA uç noktanız için bir ad seçtiniz.

Kullanıcılar JEA kullanarak sisteme bağlanmak için JEA uç nokta adı gereklidir. [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i uç noktaları bir sistemde adlarını listeler. İle başlayan uç noktaları `microsoft` genellikle Windows ile gönderilir. `microsoft.powershell` Uç noktası olan bir uzak PowerShell uç noktasına bağlanırken kullanılan varsayılan uç nokta.

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

Uç nokta kaydetmek için aşağıdaki komutu çalıştırın.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Önceki komut, sistem üzerindeki WinRM hizmetini yeniden başlatır. Bu, tüm PowerShell uzaktan iletişimini oturumları ve devam eden herhangi bir DSC yapılandırması sonlandırır. İşle ilgili işlemlerin kesintiye önlemek için komutu çalıştırmadan önce üretim makineleri çevrimdışına almanız önerilir.

Kayıt sonrasında hazır [JEA kullanın](using-jea.md). Dilediğiniz zaman oturum yapılandırma dosyasını silebilirsiniz. Yapılandırma dosyası, uç nokta kayıt sonrasında kullanılmaz.

## <a name="multi-machine-configuration-with-dsc"></a>DSC ile çok makineli yapılandırma

JEA birden fazla makinede dağıtım yaparken, JEA en basit dağıtım modelini kullanan [Desired State Configuration ' nı (DSC)](/powershell/dsc/overview) hızlı ve tutarlı bir şekilde JEA her makineye dağıtmak için kaynak.

JEA DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olun:

- Bir veya daha fazla rol işlevleri yazılmış ve bir PowerShell modülüne eklendi.
- Rolleri içeren PowerShell modülünü (salt okunur) erişilebilen bir dosya paylaşımı her makine tarafından depolanır.
- Oturum yapılandırması ayarlarını belirlediniz. JEA DSC kaynağı kullanılırken bir oturum yapılandırma dosyası oluşturmanız gerekmez.
- Yönetim eylemlerini her makinede veya makineleri yönetmek için kullanılan DSC çekme sunucusuna erişim sağlayan kimlik bilgileri var.
- İndirdiğiniz [JEA DSC kaynak](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Bir hedef makine ya da çekme sunucusunda JEA uç noktanız için bir DSC yapılandırması oluşturun. Bu yapılandırmada, **JustEnoughAdministration** DSC kaynağı oturum yapılandırma dosyasını tanımlar ve **dosya** kaynak dosya paylaşımından rol özellikleri kopyalar.

Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:

- Rol tanımları
- Sanal hesap grupları
- Grup yönetilen hizmet hesabı adı
- Transkript dizini
- Kullanıcı sürücü
- Koşullu erişim kuralları
- JEA oturumu için başlangıç betikleri

DSC yapılandırması bu özelliklerden her biri için söz dizimi PowerShell oturumu yapılandırma dosyası ile tutarlıdır.

Genel sunucu bakım modülü için örnek DSC yapılandırması aşağıda verilmiştir. Rol işlevleri içeren geçerli bir PowerShell modülü bulunan varsayar `\\myfileshare\JEA` dosya paylaşımı.

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

Ardından, yapılandırmanın bir sistemde doğrudan çağırarak uygulanması [yerel Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) veya güncelleştirme [çekme sunucusu yapılandırmasını](/powershell/dsc/pull-server/pullServer).

DSC kaynağı da varsayılan çoğaltmanıza imkan tanır **Microsoft.PowerShell** uç noktası. Değiştirildiğinde, kaynak adlı bir yedekleme uç noktası otomatik olarak kaydeder. **Microsoft.PowerShell.Restricted**. WinRM ACL, uzak yönetim kullanıcıları ve yerel Yöneticiler grup üyelerine erişim sağlar. varsayılan yedekleme uç nokta vardır.

## <a name="unregistering-jea-configurations"></a>JEA yapılandırmaları kaydı siliniyor

[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet'i bir JEA uç noktası kaldırır. Bir JEA uç noktası kaydı, yeni kullanıcıların sistemde yeni JEA oturumları oluşturmasını engeller. Ayrıca, aynı uç nokta adı kullanarak güncelleştirilmiş oturum yapılandırma dosyası yeniden kaydederek bir JEA yapılandırmasını güncelleştirmek sağlar.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Bir JEA kaydını yeniden başlatmak WinRM Hizmeti uç noktası neden olur. Bu, devam eden diğer PowerShell oturumları, WMI çağrıları ve bazı yönetim araçları dahil olmak üzere, en uzak yönetim işlemlerini kesintiye uğratır. Yalnızca PowerShell uç noktaları, planlı bakım pencereleri sırasında kaydını silin.

## <a name="next-steps"></a>Sonraki adımlar

[JEA uç test etme](using-jea.md)
