---
ms.date: 12/12/2018
keywords: DSC, powershell, kaynak, Galeri, Kurulum
title: Ek DSC kaynakları yükleme
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405859"
---
# <a name="install-additional-dsc-resources"></a>Ek DSC kaynakları yükleme

PowerShell Desired State Configuration (DSC) için çeşitli kullanıma hazır kaynaklar içerir. **Da PSDesiredStateConfiguration** modülü PowerShell belirli örneğinde kullanılabilir tüm OOB DSC kaynakları içerir.

Bu kaynağın özellikleri açıklaması ve PowerShell 4.0 sürümünü de dahil OOB kaynakların listesidir.

> [!NOTE]
> OOB kaynak sayısı her PowerShell sürümüyle büyümüştür gibi eksik bir listesini budur.

|Kaynak  |Açıklama  |
|---------|---------|
|**Dosya**|Dosyalar ve dizinler durumunu denetler. Dosyaları kopyalayan bir **kaynak** için bir **hedef** ve bunları güncelleştiren olduğunda **kaynak** tarihler, sağlama ve karma değerlerini karşılaştırarak değişiklikler.|
|**Arşiv**|Arşivler ve belirli bir konuma ayıklar. Belirtilen bir arşivlerle doğrular **sağlama toplamı**.|
|**Ortam**|Ortam değişkenlerini yönetir.|
|**Grup**|Yerel gruplar yönetir ve grup üyeliği denetler.|
|**Günlük**|İleti yazar `Microsoft-Windows-Desired State Configuration/Analytic` olay günlüğü.|
|**Paket**|Yükler veya kaldırır kullanarak paketleri **bağımsız değişkenleri**, **LogPath**, **ReturnCode**, diğer ayarları.|
|**kayıt defteri**|Kayıt defteri anahtarları ve değerleri yönetir.|
|**Komut dosyası**|Tasarlamak, kendi sağlar [get sınama kümesi](../resources/get-test-set.md) betik bloğu.|
|**Hizmet**|Windows Hizmetleri yapılandırır.|
|**Kullanıcı** |Yerel Kullanıcılar ve öznitelikleri yönetir.|
|**WindowsFeature**|Rol ve özellik yönetir.|
|**WindowsProcess**|Windows işlemleri yapılandırır.|

OOB kaynakları sık kullanılan işlemler için iyi bir başlangıç noktası sağlar. OOB kaynakları gereksinimlerinizi karşılamıyorsa, kendi yazabileceğiniz [özel kaynak](../resources/authoringResource.md). Sorununuzu çözmek için özel bir kaynak yazmadan önce hem Microsoft hem de PowerShell topluluğu tarafından zaten oluşturulmuş DSC kaynakları geniş sayısı üzerinden görünmelidir.

DSC kaynakları hem de bulabilirsiniz [PowerShell Galerisi](https://www.powershellgallery.com/) ve [GitHub](https://github.com/). PowerShell Konsolu kullanarak doğrudan gelen DSC kaynakları da yükleyebilirsiniz [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>PowerShellGet yükleme

Zaten varsa belirlemek için **PowerShell** alın veya yükleme Yardım almak için aşağıdaki Kılavuzu'na bakın: [PowerShellGet yükleme](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>PowerShellGet kullanarak DSC kaynakları bulma

Bir kez **PowerShellGet** yüklenir, sisteminizde bulmak ve barındırılan DSC kaynaklarını yüklemek [PowerShell Galerisi](https://www.powershellgallery.com/).

İlk olarak, [Bul-DSCResource](/powershell/module/powershellget/find-dscresource) DSC kaynakları bulmak için cmdlet'i. Çalıştırdığınızda `Find-DSCResource` ilk kez, "NuGet sağlayıcısı" yüklemek için aşağıdaki iletiyi görürsünüz.

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Tuşlarına basarak 'y', sonra "NuGet" sağlayıcının yüklü olduğundan, PowerShell Galerisi'nden yüklemek için kullanabileceğiniz DSC kaynakların bir listesini görürsünüz.

> [!NOTE]
> Çok büyük olduğundan listesinde gösterilmez.

Belirtebilirsiniz `-Name` parametresi joker karakterler kullanarak veya `-Filter` aramanızı daraltmak için joker karakter içermeyen bir parametre. Bu örnekte, joker karakterlerini kullanarak bir "Saat dilimi" DSC kaynağı bulmayı dener.

> [!IMPORTANT]
> Şu anda bir hata var. `Find-DSCResource` hem de joker karakter kullanılması engelleyen cmdlet'i `-Name` ve `-Filter` parametreleri. Kullanarak bir geçici çözüm aşağıdaki ikinci örnekte gösterilir `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

Ayrıca `Where-Object` daha ayrıntılı filtrelemeyle DSC kaynakları bulmak için. Bu yaklaşım, parametreleri filtreleme içinde yerleşik kullanmaktan daha yavaş olur.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Filtreleme hakkında daha fazla bilgi için bkz: [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>DSC kaynakları PowerShellGet kullanarak yükleme

DSC kaynak yüklemek için kullanın [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet modülünün altında gösterilen adı belirterek, **Modülü** arama sonuçlarındaki adı.

"Saat dilimi" kaynak "ComputerManagementDSC" modülünde, bu nedenle diğer bir deyişle bu örnek modülünü yükler var.

> [!NOTE]
> PowerShell Galerisi güvenilir değil, aşağıda onaylanmasını isteyen bir uyarı görürsünüz ve sonraki komut istemlerini önlemek nasıl söyleyen yükler.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Modülünü yüklemeye devam etmek için ' y' tuşuna basın. Yüklemeyi tamamladıktan sonra yeni kaynak kullanarak yüklü olduğunu doğrulayabilirsiniz [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Belirterek, yeni yüklenen modülde diğer kaynakları görüntüleyebilir `-ModuleName` parametresi.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Ayrıca bkz:

- [Kaynaklar nelerdir?](../resources/resources.md)
