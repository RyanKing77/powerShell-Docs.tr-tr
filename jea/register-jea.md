---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA yapılandırmaları kaydediliyor
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522863"
---
# <a name="registering-jea-configurations"></a>JEA yapılandırmaları kaydediliyor

> İçin geçerlidir: Windows PowerShell 5.0

Yapılandırmasını tamamladıktan JEA kullanabilmeniz için önce son adım, [rol işlevleri](role-capabilities.md) ve [oturum yapılandırma dosyası](session-configurations.md) JEA uç noktasını kaydetmek için oluşturulmuştur.
Bu işlem, oturum yapılandırma bilgilerini sistem için geçerlidir ve uç nokta kullanıcılar ve Otomasyon motoru tarafından kullanılabilir hale getirir.

## <a name="single-machine-configuration"></a>Tek makine yapılandırması

Küçük ortamlarda oturum yapılandırma dosyası kullanarak kaydederek JEA dağıtabilirsiniz [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet'i.

Başlamadan önce aşağıdaki önkoşulları karşıladığınızdan emin olun:
- Bir veya daha fazla rol oluşturuldu ve geçerli bir PowerShell Modülü 'RoleCapabilities' klasörüne yerleştirilir.
- Bir oturum yapılandırma dosyası oluşturulur ve test.
- Jea'yı yapılandırma kaydetme kullanıcı sistemleri üzerinde yönetici haklarına sahip.

JEA uç noktanız için bir ad seçin gerekecektir.
Jea'yı kullanarak sisteme bağlanmak kullanıcıların istediğinizde JEA uç noktası adı gerekli olacaktır.
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
> Yukarıdaki komut sistem üzerindeki WinRM hizmeti yeniden başlatılır.
> Devam eden herhangi bir DSC yapılandırması yanı sıra tüm PowerShell uzak oturum sona erer.
> İşle ilgili işlemlerin kesintiye önlemek için komutu çalıştırmadan önce tüm üretim makinelerinden çevrimdışı olması önerilir.

Kayıt başarılı olursa, hazır olduğunuz [JEA kullanın](using-jea.md).
Dilediğiniz zaman oturum yapılandırma dosyasını silebilir; kayıt sonrasında kullanılmaz.

## <a name="multi-machine-configuration-with-dsc"></a>DSC ile çok makineli yapılandırma

Birden fazla makinede JEA dağıtıyorsanız, en basit dağıtım modeli JEA kullanmaktır [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) hızlı ve tutarlı bir şekilde JEA her makineye dağıtmak için kaynak.

JEA DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olmanız gerekir:
- Bir veya daha fazla rol işlevleri yazılan ve geçerli bir PowerShell modülüne eklendi.
- Rolleri içeren PowerShell modülünü (salt okunur) erişilebilen bir dosya paylaşımı her makine tarafından depolanır.
- Oturum yapılandırması ayarlarını belirlediniz. JEA DSC kaynağı kullanan bir oturum yapılandırma dosyası oluşturduğunuzda gerekmez.
- Her makine üzerinde yönetimsel Eylemler gerçekleştirmenize olanak sağlayan veya makineleri yönetmek için kullanılan bir DSC çekme sunucusuna erişimi olan kimlik bilgileri var.
- Yüklediğiniz [JEA DSC kaynağı](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Bir hedef makine (veya çekme sunucusu birini kullanıyorsanız), bir JEA uç noktanız için DSC yapılandırması oluşturun.
Bu yapılandırmada, oturum yapılandırma dosyası oluşturma JustEnoughAdministration DSC kaynak rol işlevleri dosya paylaşımı kopyalamak için dosya kaynağı kullanır.

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
Bunu yaparsanız, kaynak "varsayılan WinRM (Uzak Yönetim kullanıcıları ve yerel Yöneticiler grup üyelerine erişim verme) ACL olan Microsoft.PowerShell.Restricted" adlı bir yedekleme unconstrainted uç noktası otomatik olarak kaydedilecek.

## <a name="unregistering-jea-configurations"></a>JEA yapılandırmaları kaydı siliniyor

Bir JEA uç noktası bir sistemde kaldırmak için [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet'i.
Bir JEA uç noktası kaydı yeni kullanıcıların sistemde yeni JEA oturumları oluşturmasını engeller.
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