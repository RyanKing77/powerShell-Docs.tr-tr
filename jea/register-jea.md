---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea, powershell, güvenlik
title: JEA yapılandırmaları kaydetme
ms.openlocfilehash: 7b0a3f0bac26bf62989fecdf60388bbebd6fa756
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="registering-jea-configurations"></a>JEA yapılandırmaları kaydetme

> Uygulandığı öğe: Windows PowerShell 5.0

Son adım bulduktan sonra JEA kullanmadan önce [rol özellikleri](role-capabilities.md) ve [oturum yapılandırma dosyası](session-configurations.md) JEA uç noktasını kaydetmek için oluşturulmuştur.
Bu işlem için sistem oturum yapılandırma bilgilerini uygular ve uç nokta kullanıcıları ve Otomasyon motorları tarafından kullanılabilir hale getirir.

## <a name="single-machine-configuration"></a>Tek makine yapılandırması

Küçük ortamlarda oturum yapılandırma dosyası kullanarak kaydederek JEA dağıtabilirsiniz [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet'i.

Başlamadan önce aşağıdaki önkoşulların karşılandığından emin olun:
- Bir veya daha fazla rol oluşturulur ve geçerli bir PowerShell Modülü 'RoleCapabilities' klasörüne yerleştirilir.
- Bir oturum yapılandırma dosyası oluşturulur ve test.
- JEA yapılandırması kaydediliyor kullanıcının sistemleri üzerinde yönetici haklarına sahip.

JEA uç noktanız için bir ad seçmek gerekir.
Kullanıcıların JEA kullanarak sisteme bağlanmak istediğinizde JEA uç noktanın adı gerekli olacaktır.
Kullanabileceğiniz [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'ini sistemde mevcut uç nokta adlarını denetleyin.
'Microsoft' ile başlayan uç noktaları genellikle Windows ile birlikte gönderilir.
'Microsoft.powershell' uç noktası bir uzak PowerShell bitiş noktasına bağlanırken kullanılan varsayılan uç noktadır.

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
> Yukarıdaki komut sistem üzerindeki WinRM hizmeti yeniden başlatılır.
> Bu, devam eden tüm DSC yapılandırmaları yanı sıra tüm PowerShell uzaktan iletişim oturumları sonlandırılacak.
> İş işlemlerini kesintiye önlemek için komutu çalıştırmadan önce tüm üretim makinelerinin çevrimdışı olması önerilir.

Kayıt başarılı olursa hazırsınız [JEA kullanmak](using-jea.md).
Oturum yapılandırma dosyası herhangi bir anda silebilir; kayıttan sonra kullanılmaz.

## <a name="multi-machine-configuration-with-dsc"></a>DSC ile çoklu makine yapılandırması

Birden çok makineye JEA dağıtıyorsanız, basit dağıtım modeli JEA kullanmaktır [istenen durum Yapılandırması](https://msdn.microsoft.com/en-us/powershell/dsc/overview) hızlı ve tutarlı bir şekilde JEA her makine dağıtmak için kaynak.

JEA DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olmak gerekir:
- Bir veya daha fazla rol özellikleri yazılan ve geçerli bir PowerShell modülü eklenir.
- Rolleri içeren PowerShell Modülü (salt okunur) erişilebilen bir dosya paylaşımı her makine tarafından depolanır.
- Oturum yapılandırması ayarlarını belirlediniz. JEA DSC kaynağı kullanırken oturum yapılandırma dosyası oluşturmak gerekmez.
- Her makinede yönetici eylemleri gerçekleştirmenize izin veren veya makineleri yönetmek için kullanılan bir DSC çekme sunucusuna erişimi olan kimlik bilgilerine sahip.
- Yüklediğiniz [JEA DSC kaynağı](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Bir hedef makine (veya çekme sunucu birini kullanıyorsanız), JEA uç noktanız için bir DSC yapılandırmasını oluşturun.
Bu yapılandırmada, oturum yapılandırma dosyasını ayarlamaya JustEnoughAdministration DSC kaynağı ve rol yetenekler dosya paylaşımından kopyalamak için dosya kaynağı kullanır.

Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:
- Rol tanımları
- Sanal hesap grupları
- Grup yönetilen hizmet hesabı adı
- Dökümü dizini
- Kullanıcı sürücü
- Koşullu erişim kuralları
- JEA oturumu için başlangıç betiklerini

DSC yapılandırması bu özelliklerin her biri için söz dizimi PowerShell oturumu yapılandırma dosyası ile tutarlıdır.

Genel sunucu bakım modülü için örnek bir DSC yapılandırma aşağıdadır.

Rol özellikleri 'RoleCapabilities' bir alt klasör içeren geçerli bir PowerShell modülü bulunan varsayar '\\\\myfileshare\\JEA' dosya paylaşımı.


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

Bu yapılandırmayı daha sonra bir sistemde tarafından uygulanabilir [yerel Configuration Manager doğrudan çağırma](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) veya güncelleştirme [çekme sunucu yapılandırması](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).

DSC kaynağı varsayılan Microsoft.PowerShell uzak uç değiştirmenizi sağlar.
Bunu yaparsanız, kaynak "WinRM (Uzak Yönetim kullanıcıları ve yerel Yöneticiler grubu üyeleri erişmek izin vererek) ACL varsayılan olan Microsoft.PowerShell.Restricted" adlı bir yedekleme unconstrainted uç noktası otomatik olarak kaydeder.

## <a name="unregistering-jea-configurations"></a>Kaydı siliniyor JEA yapılandırmaları

Bir sistem JEA noktadaki kaldırmak için kullanın [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet'i.
JEA endpoint kaydını yeni kullanıcıların sistemde yeni JEA oturumlar oluşturmaktan engel olur.
Ayrıca, aynı uç nokta adı kullanarak güncelleştirilmiş oturum yapılandırma dosyası yeniden kaydederek JEA yapılandırmasını güncelleştirmenizi sağlar.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Bir JEA kaydını yeniden başlatmak WinRM Hizmeti uç noktası neden olur.
> Bu, devam eden diğer PowerShell oturumları, WMI çağrılarını ve bazı yönetim araçları dahil olmak üzere, çoğu uzak yönetim işlemlerini kesintiye uğratır.
> Yalnızca PowerShell uç noktaları planlı bakım pencerelerini kaydını silin.

## <a name="next-steps"></a>Sonraki adımlar

- [JEA endpoint test](using-jea.md)