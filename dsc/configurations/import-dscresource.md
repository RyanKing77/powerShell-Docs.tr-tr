---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Import-DSCResource kullanma
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215412"
---
# <a name="using-import-dscresource"></a>Import-DSCResource kullanma

`Import-DScResource`yalnızca bir yapılandırma komut dosyası bloğunda kullanılabilen dinamik bir anahtar sözcüktür. Yapılandırmanızda gerekli olan tüm kaynakları içeri aktarma anahtarsözcüğü.`Import-DSCResource` Altındaki `$pshome` kaynaklar otomatik olarak içeri aktarılır, ancak [yapılandırmanızda](Configurations.md)kullanılan tüm kaynakları açıkça içeri aktarmak için en iyi yöntem hala kabul edilir.

Sözdizimi `Import-DSCResource` aşağıda gösterilmiştir.  Modülleri ada göre belirtirken, her bir yeni satıra listelemek bir gereksinimdir.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parametre  |Açıklama  |
|---------|---------|
|`-Name`|İçeri aktarmanız gereken DSC kaynak adları. Modül adı belirtilmişse, komut bu modül içinde bu DSC kaynaklarını arar; Aksi takdirde, komut DSC kaynaklarını tüm DSC kaynak yollarında arar. Joker karakterler desteklenir.|
|`-ModuleName`|Modül adı veya modül belirtimi.  Bir modülden içeri aktarılacak kaynakları belirtirseniz, komut yalnızca bu kaynakları içeri aktarmaya çalışır. Yalnızca modülü belirtirseniz, komut modüldeki tüm DSC kaynaklarını içeri aktarır.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Örnek: Bir yapılandırma içinde Import-DSCResource kullanın

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
> Aynı komutta kaynak adları ve modül adları için birden çok değer belirtilmesi desteklenmez. Bu, birden çok modülde aynı kaynak olması durumunda hangi modülün yükleneceğini belirten belirleyici olmayan davranışlara sahip olabilir. Aşağıdaki komut, derleme sırasında hataya neden olur.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Yalnızca ad parametresini kullanırken göz önünde bulundurmanız gerekenler:

- Makinede yüklü olan modül sayısına bağlı olarak Kaynak yoğunluklu bir işlemdir.
- Verilen adla bulunan ilk kaynağı yükler. Aynı ada sahip birden fazla kaynak yüklü olduğunda, yanlış kaynağı yükleyebilir.

Önerilen kullanım, aşağıda açıklandığı gibi `–ModuleName` `-Name` parametresiyle belirtilmelidir.

Bu kullanım aşağıdaki avantajlara sahiptir:

- Belirtilen kaynak için arama kapsamını sınırlayarak performans etkisini azaltır.
- Doğru kaynak yüklendiğinden emin olarak kaynağı tanımlayan modülü açıkça tanımlar.

> [!NOTE]
> PowerShell 5,0 ' de DSC kaynakları birden çok sürüme sahip olabilir ve sürümler bir bilgisayara yan yana yüklenebilir. Bu, aynı modül klasöründe yer alan bir kaynak modülünün birden çok sürümü ile uygulanır.
> Daha fazla bilgi için bkz. [birden çok sürümü olan kaynakları kullanma](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>Import-DSCResource ile IntelliSense

ISE 'de DSC yapılandırmasını yazarken, PowerShell kaynak ve kaynak özellikleri için Intellisence 'yi sağlar. `$pshome` Modül yolu altındaki kaynak tanımları otomatik olarak yüklenir. `Import-DSCResource` Anahtar sözcüğünü kullanarak kaynakları içeri aktardığınızda, belirtilen kaynak tanımları eklenir ve IntelliSense, içeri aktarılan kaynağın şemasını içerecek şekilde genişletilir.

![Kaynak IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> PowerShell 5,0 ' den başlayarak, DSC kaynakları ve bunların özelliklerine ilişkin sekme tamamlama, ıSE 'ye eklenmiştir. Daha fazla bilgi için bkz. [kaynaklar](../resources/resources.md).

Yapılandırma derlenirken, PowerShell, yapılandırmadaki tüm kaynak bloklarını doğrulamak için içeri aktarılan kaynak tanımlarını kullanır.
Her kaynak bloğu, aşağıdaki kurallar için kaynağın şema tanımı kullanılarak onaylanır.

- Yalnızca şemada tanımlanan özellikler kullanılır.
- Her bir özelliğin veri türleri doğrudur.
- Anahtarlar özellikleri belirtilmiştir.
- Salt okunurdur özelliği kullanılmaz.
- Değer eşlemeleri türlerinde doğrulama.

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

Bu yapılandırmanın derlenmesi bir hatayla sonuçlanır.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense ve şema doğrulama, ayrıştırma ve derleme sırasında daha fazla hata yakalamalı ve çalışma zamanında karmaşıklıkları önkullanmanıza imkan sağlar.

> [!NOTE]
> Her DSC kaynağı bir ada ve kaynağın şeması tarafından tanımlanan bir **FriendlyName** 'a sahip olabilir. Aşağıda "MSFT_ServiceResource. Shema. mof" öğesinin ilk iki satırı verilmiştir.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Bu kaynağı bir yapılandırmada kullanırken, **MSFT_ServiceResource** veya **Service**belirtebilirsiniz.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 ve v5 farklılıkları

PowerShell 4,0 ile yapılandırma yazma sırasında gördüğünüz birden çok fark vardır. PowerShell 5,0 ve üzeri. Bu bölümde, bu makaleyle ilgili gördüğünüz farklar vurgulanacaktır.

### <a name="multiple-resource-versions"></a>Birden çok kaynak sürümü

PowerShell 4,0 ' de yan yana kaynakların birden çok sürümünün yüklenmesi ve kullanılması desteklenmez. Yapılandırmanızda kaynakları içeri aktarma sorunları fark ederseniz, kaynağın yalnızca bir sürümünün yüklü olduğundan emin olun.

Aşağıdaki görüntüde, **Xpsdesiredstateconfiguration** modülünün iki sürümü yüklenir.

![Birden çok kaynak sürümü düzeltildi](../media/multiple-resource-versions-broken.png)

İstediğiniz modül sürümünüzün içeriğini modül dizininin en üst düzeyine kopyalayın.

![Birden çok kaynak sürümü düzeltildi](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>Kaynak konumu

Yapılandırma yazma ve derleme yaparken, kaynaklarınız [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)'niz tarafından belirtilen herhangi bir dizinde depolanabilir. PowerShell 4,0 ' de, LCM tüm DSC kaynak modüllerinin "program Files\WindowsPowerShell\Modules" veya `$pshome\Modules`altında depolanmasını gerektirir. PowerShell 5,0 ' den başlayarak bu gereksinim kaldırılmıştır ve kaynak modülleri tarafından `PSModulePath`belirtilen herhangi bir dizinde depolanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynaklar](../resources/resources.md)
