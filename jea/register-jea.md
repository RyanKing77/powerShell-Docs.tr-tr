---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA yapılandırmaları kaydediliyor
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059448"
---
# <a name="registering-jea-configurations"></a>JEA yapılandırmaları kaydediliyor

> Şunun için geçerlidir: Windows PowerShell 5.0

Sonra [rol işlevleri](role-capabilities.md) ve [oturum yapılandırma dosyası](session-configurations.md) , son adım JEA kullanabilmeniz için önce JEA uç noktasını kaydetmek için oluşturulmuştur.
Sistemiyle JEA uç noktası kaydediliyor uç nokta kullanıcılar ve Otomasyon motoru tarafından kullanılabilir hale getirir.

## <a name="single-machine-configuration"></a>Tek makine yapılandırması

Küçük ortamlarda oturum yapılandırma dosyası kullanarak kaydederek JEA dağıtabilirsiniz [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet'i.

Başlamadan önce aşağıdaki önkoşulları karşıladığınızdan emin olun:
- Bir veya daha fazla rol oluşturuldu ve geçerli bir PowerShell Modülü 'RoleCapabilities' klasörüne yerleştirilir.
- Bir oturum yapılandırma dosyası oluşturulur ve test.
- Jea'yı yapılandırma kaydetme kullanıcı sistemleri üzerinde yönetici haklarına sahip.

Ayrıca JEA uç noktanız için bir ad seçmeniz gerekir.
Jea'yı kullanarak sisteme bağlanmak kullanıcıların istediğinizde JEA uç nokta adı gereklidir.
Kullanabileceğiniz [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'ini sistemde mevcut uç nokta adları denetleyin.
'Microsoft' ile başlayan uç noktaları, genellikle Windows ile gönderilir.
'Microsoft.powershell' uç noktası bir uzak PowerShell uç noktasına bağlanırken kullanılan varsayılan uç noktadır.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

JEA uç noktanız için uygun bir ad belirlediğinizde uç noktasını kaydetmek için aşağıdaki komutu çalıştırın.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Yukarıdaki komut, sistem üzerindeki WinRM hizmetini yeniden başlatır.
> Bu, devam eden herhangi bir DSC yapılandırması yanı sıra tüm PowerShell uzaktan iletişimini oturumlarını sonlandırır.
> İşle ilgili işlemlerin kesintiye önlemek için komutu çalıştırmadan önce tüm üretim makinelerinden çevrimdışı olması önerilir.

Kayıt başarılı olursa, hazır olduğunuz [JEA kullanın](using-jea.md).
Dilediğiniz zaman oturum yapılandırma dosyasını silebilir; Kayıt uç noktasının sonrasında kullanılmaz.

## <a name="multi-machine-configuration-with-dsc"></a>DSC ile çok makineli yapılandırma

Birden fazla makinede JEA dağıtıyorsanız, en basit dağıtım modeli JEA kullanmaktır [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) hızlı ve tutarlı bir şekilde JEA her makineye dağıtmak için kaynak.

JEA DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olmanız gerekir:
- Bir veya daha fazla rol işlevleri yazılan ve geçerli bir PowerShell modülüne eklendi.
- Rolleri içeren PowerShell modülünü (salt okunur) erişilebilen bir dosya paylaşımı her makine tarafından depolanır.
- Oturum yapılandırması ayarlarını belirlediniz. JEA DSC kaynağı kullanan bir oturum yapılandırma dosyası oluşturduğunuzda gerekmez.
- Her makine üzerinde yönetimsel Eylemler gerçekleştirmenize olanak sağlayan kimlik bilgilerine sahip olması veya makineleri yönetmek için kullanılan bir DSC çekme sunucusuna erişimi vardır.
- Yüklediğiniz [JEA DSC kaynağı](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Bir hedef makine (veya çekme sunucusu birini kullanıyorsanız), bir JEA uç noktanız için DSC yapılandırması oluşturun.
Bu yapılandırmada JustEnoughAdministration DSC kaynağı oturum yapılandırma dosyası oluşturma ve rol işlevleri dosya paylaşımı kopyalamak için dosya kaynağı kullanın.

Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:
- Rol tanımları
- Sanal hesap grupları
- Grup yönetilen hizmet hesabı adı
- Transkript dizini
- Kullanıcı sürücü
- Koşullu erişim kuralları
- JEA oturumu için başlangıç betikleri

DSC yapılandırması bu özelliklerden her biri için söz dizimi PowerShell oturumu yapılandırma dosyası ile tutarlıdır.

Genel sunucu bakım modülü için örnek DSC yapılandırması aşağıda verilmiştir.

Rol işlevleri bir 'RoleCapabilities' alt içeren geçerli bir PowerShell modülü bulunan varsayar '\\\\myfileshare\\JEA' dosya paylaşımı.


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

Bu yapılandırma tarafından bir sistemde sonra uygulanabilir [doğrudan yerel Configuration Manager'ı çağırma](https://msdn.microsoft.com/powershell/dsc/metaconfig) veya güncelleştirme [çekme sunucusu yapılandırmasını](https://msdn.microsoft.com/powershell/dsc/pullserver).

DSC kaynağı da varsayılan Microsoft.PowerShell uzak uç nokta çoğaltmanıza imkan tanır.
Bunu yaparsanız, kaynak, "WinRM (Uzak Yönetim kullanıcıları ve yerel Yöneticiler grup üyelerine erişim verme) ACL varsayılan olan Microsoft.PowerShell.Restricted" adlı bir yedekleme sınırlandırılmamış uç noktası otomatik olarak kaydeder.

## <a name="unregistering-jea-configurations"></a>JEA yapılandırmaları kaydı siliniyor

Bir JEA uç noktası bir sistemde kaldırmak için [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet'i.
Bir JEA uç noktası kaydı, yeni kullanıcıların sistemde yeni JEA oturumları oluşturmasını engeller.
Ayrıca, aynı uç nokta adı kullanarak güncelleştirilmiş oturum yapılandırma dosyası yeniden kaydederek bir JEA yapılandırmasını güncelleştirmek sağlar.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Bir JEA kaydını yeniden başlatmak WinRM Hizmeti uç noktası neden olur.
> Bu, devam eden diğer PowerShell oturumları, WMI çağrıları ve bazı yönetim araçları dahil olmak üzere, en uzak yönetim işlemlerini kesintiye uğratır.
> Yalnızca PowerShell uç noktaları, planlı bakım pencereleri sırasında kaydını silin.

## <a name="next-steps"></a>Sonraki adımlar

- [JEA uç test etme](using-jea.md)
