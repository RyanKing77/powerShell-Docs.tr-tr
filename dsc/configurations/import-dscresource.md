---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Import-DSCResource kullanma
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803421"
---
# <a name="using-import-dscresource"></a>Import-DSCResource kullanma

`Import-DScResource` yalnızca bir yapılandırma komut dosyası bloğu içinde kullanılabilir dinamik bir anahtar sözcüktür. `Import-DSCResource` Yapılandırmanızda gerekli tüm kaynakları almak için anahtar sözcüğü. Kaynaklarınıza `$pshome` otomatik olarak alınır ancak bu, açıkça içinde kullanılan tüm kaynakları almak için en iyi varsayılır, [yapılandırma](Configurations.md).

Sözdizimi `Import-DSCResource` aşağıda gösterilmiştir.  Modül adıyla belirtirken, her yeni bir satıra listelemek için zorunludur.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parametre  |Açıklama  |
|---------|---------|
|`-Name`|İçeri aktarmalısınız DSC kaynak adları. Modül adı belirtilmezse, komut bu DSC kaynakları bu modül içinde arar; Aksi takdirde komut DSC kaynakları tüm DSC kaynak yollarını arar. Joker karakterleri desteklenir.|
|`-ModuleName`|Modül adı veya modül belirtimi.  Bir modülü içeri aktarmak için kaynakları belirtirseniz, yalnızca bu kaynakları almak komut deneyecek. Komut modülü yalnızca belirtirseniz, modüldeki tüm DSC kaynaklarını içeri aktarır.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Örnek: Import-DSCResource içine bir yapılandırmayı kullanın.

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Kaynak adları ve modülleri adları için birden çok değer aynı komutta belirtme desteklenmez. Bu durumda birden çok modül içinde aynı kaynak var. hangi modülü yüklemek için hangi kaynak hakkında kararlı olmayan davranışı olabilir. Komut, derleme sırasında hataya neden olur.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Name parametresi kullanırken dikkat edilmesi gerekenler:

- Bu, makinede yüklü modülleri sayısına bağlı olarak kaynak yoğunluklu bir işlemdir.
- Verilen ada sahip bulunan ilk kaynak yüklemek. Örnekte yüklü aynı ada sahip birden fazla kaynak olduğunda, yanlış kaynak yükleyebilir.

Önerilen kullanım belirlemektir `–ModuleName` ile `-Name` aşağıda açıklandığı gibi parametre.

Bu kullanım aşağıdaki faydaları sağlar:

- Belirtilen kaynak için arama kapsamını sınırlayarak, performans etkisini azaltır.
- Doğru kaynak yüklenen sağlama kaynak tanımlama modülü açıkça tanımlar.

> [!NOTE]
> PowerShell 5.0, DSC kaynaklarını birden çok sürümü olabilir ve sürümleri bir bilgisayarda yan yana üzerinde yüklenebilir. Bu, bir kaynak modülü aynı modül klasöründe bulunan birden çok sürümünü sağlayarak uygulanır.
> Daha fazla bilgi için [birden çok sürümü olan kaynakları kullanma](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>Import-DSCResource ile IntelliSense

DSC yapılandırması ıse'de yazarken, PowerShell IntelliSence kaynakları ve kaynak özellikleri sağlar. Kaynak tanımları altında `$pshome` modül yolu otomatik olarak yüklenir. Kullanarak kaynakları aktardığınızda `Import-DSCResource` anahtar sözcüğü, belirtilen kaynak tanımları eklenir ve IntelliSense, içeri aktarılan kaynak şemayı içerecek şekilde genişletilir.

![Kaynak IntelliSense](/media/resource-intellisense.png)

> [!NOTE]
> PowerShell 5. 0'den itibaren sekme tamamlamayı ISE DSC kaynakları ve bunların özelliklerini için eklendi. Daha fazla bilgi için [kaynakları](../resources/resources.md).

PowerShell içeri aktarılan kaynak tanımları yapılandırması derlenirken tüm kaynak bloklar yapılandırmasında doğrulamak için kullanır.
Her kaynak blok kaynağın şema tanımı için aşağıdaki kurallar kullanılarak doğrulanır.

- Şemada tanımlanan özellikler kullanılır.
- Veri türleri her bir özellik için doğrudur.
- Anahtar özellikler belirtilmedi.
- Salt okunur bir özellik kullanılır.
- Doğrulama değeri türleri eşler.

Aşağıdaki yapılandırmayı göz önünde bulundurun:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Bu yapılandırma sonuçları hata derleniyor.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense ve şema doğrulama daha fazla hata ayrıştırma ve derleme zamanında çalışma zamanında zorluklar önleme catch olanak tanır.

> [!NOTE]
> Her DSC kaynağı bir ad olabilir ve bir **FriendlyName** kaynağın şeması tarafından tanımlanır. İlk iki satırını "MSFT_ServiceResource.shema.mof" aşağıda verilmiştir.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Bu kaynak bir yapılandırmada kullanılırken, belirtebileceğiniz **MSFT_ServiceResource** veya **hizmet**.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 ve v5 farklılıkları

Yapılandırmalar PowerShell 4.0 vs'de yazarken gördüğünüz birden çok fark yoktur. PowerShell 5.0 ve üzeri. Bu bölümde farklar vurgular ilgili bu makaleye bakın.

### <a name="multiple-resource-versions"></a>Birden çok kaynak sürümü

Yükleme ve birden çok sürümünü yan yana kaynakları kullanarak PowerShell 4. 0'desteklenmiyor. Kaynakları yapılandırmanızı içeri aktarmayla ilgili sorunları fark ederseniz, bir sürümü yüklü kaynak yalnızca olduğundan emin olun.

İki sürümü aşağıda resimde **xPSDesiredStateConfiguration** Modülü yüklü.

![Sabit birden çok kaynak sürümü](/media/multiple-resource-versions-broken.md)

Modül dizinini, en üst düzeye istenen modülün sürümünüzü içeriğini kopyalayın.

![Sabit birden çok kaynak sürümü](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Kaynak konumu

Geliştirme ve yapılandırmaları derleme kaynaklarınızı tarafından belirtilen herhangi bir dizinini depolanabilir, [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). PowerShell 4. 0'da, "Program Files\WindowsPowerShell\Modules" altında depolanan tüm DSC kaynak modülleri LCM gerektirir veya `$pshome\Modules`. PowerShell 5. 0'den itibaren bu gereksinimi kaldırıldı ve kaynak modülleri tarafından belirtilen herhangi bir dizinini depolanabilir `PSModulePath`.

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynaklar](../resources/resources.md)
