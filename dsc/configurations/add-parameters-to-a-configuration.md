---
ms.date: 12/12/2018
keywords: DSC, PowerShell, kaynak, Galeri, kurulum
title: Yapılandırmalara Parametre Ekleme
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386323"
---
# <a name="add-parameters-to-a-configuration"></a>Yapılandırmalara Parametre Ekleme

LIKE Işlevleri, kullanıcı girişine göre daha dinamik yapılandırmalara izin vermek için [yapılandırma](configurations.md) parametrelenebilir. Adımlar, [parametrelere sahip işlevlerde](/powershell/module/microsoft.powershell.core/about/about_functions)açıklananlara benzerdir.

Bu örnek, "biriktirici" hizmetini "çalışıyor" olarak yapılandıran temel bir yapılandırmayla başlar.

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Yerleşik yapılandırma parametreleri

Ancak, bir Işlevden farklı olarak, [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) özniteliği hiçbir işlev ekler. [Sık kullanılan parametrelere](/powershell/module/microsoft.powershell.core/about/about_commonparameters)ek olarak, konfigürasyonlar, bunları tanımlamanıza gerek kalmadan, aşağıdaki yerleşik parametreleri de kullanabilir.

|Parametre  |Açıklama  |
|---------|---------|
|`-InstanceName`|[Bileşik yapılandırmaların](compositeconfigs.md) tanımlanması için kullanılır|
|`-DependsOn`|[Bileşik yapılandırmaların](compositeconfigs.md) tanımlanması için kullanılır|
|`-PSDSCRunAsCredential`|[Bileşik yapılandırmaların](compositeconfigs.md) tanımlanması için kullanılır|
|`-ConfigurationData`|Yapılandırmada kullanılmak üzere yapılandırılmış [yapılandırma verilerini](configData.md) geçirmek için kullanılır.|
|`-OutputPath`|"\<ComputerName\>. mof" dosyanızın derlenebileceği yeri belirtmek için kullanılır|

## <a name="adding-your-own-parameters-to-configurations"></a>Yapılandırmalara kendi parametrelerinizi ekleme

Yerleşik parametrelere ek olarak, kendi parametrelerinizi de yapılandırmalara ekleyebilirsiniz. Parametre bloğu, doğrudan yapılandırma bildiriminin içinde, tıpkı bir Işlev gibi gider. Bir yapılandırma parametresi bloğunun herhangi bir **düğüm** bildiriminin dışında ve *içeri aktarma* deyimlerinin üzerinde olması gerekir. Parametreleri ekleyerek, yapılandırmalarınızın daha sağlam ve dinamik olmasını sağlayabilirsiniz.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>ComputerName parametresi Ekle

Ekleyebileceğiniz ilk parametre, yapılandırmanıza geçirdiğiniz bir " `-Computername` . mof" dosyasını dinamik olarak derleyebilmeniz `-Computername` için bir parametredir. Ayrıca, örneğin, kullanıcının bir değer geçirmezse bir varsayılan değer de tanımlayabilirsiniz.`-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Yapılandırmanızın içinde, düğüm bloğunu tanımlarken `-ComputerName` parametresini belirtebilirsiniz.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Yapılandırma parametrelerini çağırma

Yapılandırmanıza parametreler ekledikten sonra, bunları bir cmdlet 'le yaptığınız gibi kullanabilirsiniz.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Birden çok. mof dosyası derleme

Düğüm bloğu Ayrıca, virgülle ayrılmış bir bilgisayar adları listesi kabul edebilir ve her biri için ". mof" dosyaları oluşturur. `-ComputerName` Parametreye geçirilen tüm bilgisayarlar için ". mof" dosyaları oluşturmak için aşağıdaki örneği çalıştırabilirsiniz.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Yapılandırmalarda Gelişmiş parametreler

Bir `-ComputerName` parametreye ek olarak, hizmet adı ve eyalet için parametreler ekleyebiliriz. Aşağıdaki örnek, parametresi ile `-ServiceName` bir parametre bloğu ekler ve **hizmet** kaynak bloğunu dinamik olarak tanımlamak için kullanır. Ayrıca, **hizmet** kaynak `-State` bloğunda **durumu** dinamik olarak tanımlamak için bir parametre ekler.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> Daha fazla işlem senaryosunda, dinamik verilerinizi yapılandırılmış bir [yapılandırma verilerine](configData.md)taşımak daha mantıklı olabilir.

Örnek yapılandırma artık dinamik `$ServiceName`bir şekilde sürer, ancak belirtilmemişse bir hata oluşur. Bu örneğe benzer bir varsayılan değer ekleyebilirsiniz.

```powershell
[String]
$ServiceName="Spooler"
```

Bu örnekte, kullanıcının `$ServiceName` parametre için bir değer belirtmesini zorlamak için de daha anlamlı hale gelir. Özniteliği `parameter` , yapılandırmanızın parametrelerine daha fazla doğrulama ve işlem hattı desteği eklemenizi sağlar.

Herhangi bir parametre bildiriminde, aşağıdaki örnekte `parameter` olduğu gibi öznitelik bloğunu ekleyin.

```powershell
[parameter()]
[String]
$ServiceName
```

Tanımlı parametrenin yönlerini denetlemek için her `parameter` bir özniteliğin bağımsız değişkenlerini belirtebilirsiniz. Aşağıdaki örnek `$ServiceName` **zorunlu** bir parametre oluşturur.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Parametresi için, kullanıcının önceden tanımlanmış bir küme dışında (çalışıyor, durduruldu gibi `ValidationSet*`) değerler belirtmesini engellemek istiyoruz. öznitelik, kullanıcının önceden tanımlanmış bir küme dışında değerler belirtmesini önler (örneğin, `$State` Durduruldu). Aşağıdaki örnek, `ValidationSet` `$State` parametresine özniteliğini ekler. `$State` Parametresini **zorunlu**hale getirmek istemediğimiz için, bunun için varsayılan bir değer eklememiz gerekir.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Özniteliği kullanırken bir `parameter` öznitelik belirtmeniz gerekmez. `validation`

`parameter` [About_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters)' de ve doğrulama öznitelikleri hakkında daha fazla bilgi edinebilirsiniz.

## <a name="fully-parameterized-configuration"></a>Tam parametreli yapılandırma

Artık, kullanıcıyı bir `-InstanceName`, `-ServiceName`, ve `-State` parametresini doğrulama işlemini zorlayan parametreli bir yapılandırmadır.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [DSC yapılandırması için yardım yazma](configHelp.md)
- [Dinamik yapılandırma](flow-control-in-configurations.md)
- [Yapılandırmalarınızın yapılandırma verilerini kullanma](configData.md)
- [Yapılandırma ve ortam verilerini ayır](separatingEnvData.md)
