---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kur
title: Import-DSCResource kullanma
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265510"
---
# <a name="using-import-dscresource"></a>Import-DSCResource kullanma

`Import-DScResource` yalnızca bir yapılandırma komut dosyası bloğunun içine kullanılabilir dinamik bir anahtar sözcüktür. `Import-DSCResource` Yapılandırmanızda gereken herhangi bir kaynağa alınacak anahtar. Kaynaklarınıza `$phsome` otomatik olarak alınır ancak hala açık olarak kullanılan tüm kaynakları içeri aktarmak için en iyi yöntem kabul edilir, [yapılandırma](Configurations.md).

Sözdizimi `Import-DSCResource` aşağıda gösterilmiştir.  Modülleri adıyla belirtirken, her yeni bir satıra listelemek için gerekli değildir.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parametre  |Açıklama  |
|---------|---------|
|`-Name`|İçeri aktarmanız gerekir DSC kaynak adları. Modül adı belirtilmezse, komut bu DSC kaynakları bu modül içinde arar; Aksi takdirde komut tüm DSC kaynağı yollarında DSC kaynakları arar. Joker karakterleri desteklenir.|
|`-ModuleName`|Modül adı veya modülü belirtimi.  Bir modülü içeri aktarmak için kaynakları belirtirseniz, komutun yalnızca kaynakları alma dener. Modül yalnızca belirtirseniz, komut modülündeki tüm DSC kaynakları alır.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Örnek: İçinde bir yapılandırma alma DSCResource kullanın

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
> Aynı komutta kaynak adları ve modülleri adları için birden fazla değer belirten desteklenmez. Birden çok modüllerde aynı kaynak mevcut durumda hangi modülünden yüklemek için hangi kaynak hakkında belirleyici olmayan davranış olabilir. Aşağıdaki komutunu derleme sırasında hataya neden olur.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Name parametresi kullanırken dikkat edilmesi gerekenler:

- Bu, makinede yüklü modülleri sayısına bağlı olarak kaynak yoğunluklu bir işlemdir.
- Verilen ada sahip bulunan ilk kaynak yükler. Durumda yüklü aynı ada sahip birden fazla kaynak burada yanlış kaynak yüklemek.

Önerilen kullanım belirtmektir `–ModuleName` ile `-Name` aşağıda açıklandığı gibi parametre.

Bu kullanım aşağıdaki faydaları vardır:

- Performans etkisi belirtilen kaynak için arama kapsamını sınırlayarak azaltır.
- Açıkça, doğru kaynak yüklenen sağlama kaynak tanımlama modülü tanımlar.

> [!NOTE]
> PowerShell 5. 0'da, DSC kaynakları birden çok sürümü olabilir ve bir bilgisayar yan yana üzerinde sürümleri yüklenebilir. Bu, aynı modülü klasörde yer alan birden çok kaynak Modül sürümü sağlayarak uygulanır.
> Daha fazla bilgi için bkz: [birden çok sürümü ile kaynakları kullanarak](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>İçeri aktarma DSCResource IntelliSense

İşe DSC yapılandırması yazılırken PowerShell IntelliSence kaynaklar ve kaynak özellikleri sağlar. Kaynak tanımları altında `$pshome` modül yolu otomatik olarak yüklenir. Kullanarak kaynakları aktardığınızda `Import-DSCResource` anahtar sözcüğü, belirtilen kaynak tanımları eklenir ve IntelliSense içeri aktarılan kaynağın şema içerecek şekilde genişletilmiştir.

![Kaynak IntelliSense](/media/resource-intellisense.png)

> [!NOTE]
> PowerShell 5. 0'den itibaren sekme tamamlama DSC kaynakları ve bunların özelliklerini için işe eklendi. Daha fazla bilgi için bkz: [kaynakları](../resources/resources.md).

Yapılandırma derlerken PowerShell alınan kaynak tanımları yapılandırmasında tüm kaynak blokları doğrulamak için kullanır.
Her kaynak bloğu kaynağın şema tanımı için aşağıdaki kurallar kullanılarak doğrulanır.

- Şemada tanımlanan özellikler kullanılır.
- Veri türleri her bir özellik için doğru.
- Anahtarları özellikler belirtilir.
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

IntelliSense ve şema doğrulama zorluklar çalışma zamanında önleme ayrıştırma ve derleme süre boyunca, daha fazla hatalarını yakalama olanak tanır.

> [!NOTE]
> Her DSC kaynağı bir ad olabilir ve bir **FriendlyName** kaynağın şema tarafından tanımlanan. "MSFT_ServiceResource.shema.mof" ilk iki satır aşağıda verilmiştir.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Bu kaynak bir yapılandırmada kullanırken belirtebilirsiniz **MSFT_ServiceResource** veya **hizmet**.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 ve v5 farklılıkları

Yapılandırmalar PowerShell 4.0 vs yazarken gördüğünüz birden çok farklılıklar vardır. PowerShell 5.0 ve sonraki sürümleri. Bu bölümde farklar vurgular ilgili bu makaleye bakın.

### <a name="multiple-resource-versions"></a>Birden çok kaynak sürümü

Yükleme ve kaynakları yan yana birden fazla sürümünü kullanarak PowerShell 4. 0'desteklenmiyor. Kaynakları yapılandırmanızı alma sorunları fark ederseniz, yalnızca bir sürümü yüklü kaynak olduğundan emin olun.

Aşağıda, iki sürümü görüntüsündeki **xPSDesiredStateConfiguration** modülü yüklenir.

![Sabit birden çok kaynak sürümü](/media/multiple-resource-versions-broken.md)

İstenen modülü sürümünüzü içeriğini modülü dizininin en üst düzeye kopyalayın.

![Sabit birden çok kaynak sürümü](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Kaynak konumu

Geliştirme ve yapılandırmaları derleme, kaynaklarınızın tarafından belirtilen herhangi bir dizini depolanabilir, [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). PowerShell 4. 0'da, tüm DSC kaynağı modülleri "Altında Program Files\WindowsPowerShell\Modules" depolanması için LCM'yi gerektirir veya `$pshome\Modules`. PowerShell 5. 0'den itibaren bu gereksinimi kaldırıldı ve kaynak modülleri tarafından belirtilen herhangi bir dizini depolanabilir `PSModulePath`.

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynaklar](../resources/resources.md)
