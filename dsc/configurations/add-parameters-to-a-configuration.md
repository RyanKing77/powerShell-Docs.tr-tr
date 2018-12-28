---
ms.date: 12/12/2018
keywords: DSC, powershell, kaynak, Galeri, Kurulum
title: İçin yapılandırma parametreleri Ekle
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405771"
---
# <a name="add-parameters-to-a-configuration"></a>İçin yapılandırma parametreleri Ekle

İşlevler, ister [yapılandırmaları](configurations.md) kullanıcı girişini temel alarak daha dinamik yapılandırmaları izin vermek için parametreli olabilir. İçinde açıklananlara benzer adımlarla [parametreleri olan işlevlere](/powershell/module/microsoft.powershell.core/about/about_functions).

Bu örnek, "" "Biriktirici" hizmetinin çalışmasını yapılandırır bir temel yapılandırmayla başlatır.

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

Bir işlev aksine, [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) öznitelik hiçbir işlevsellik ekler. Ek olarak [ortak parametreleri](/powershell/module/microsoft.powershell.core/about/about_commonparameters), yapılandırmaları, aşağıdaki parametreleri olarak tanımlamak gerek kalmadan yerleşik olarak da kullanabilirsiniz.

|Parametre  |Açıklama  |
|---------|---------|
|`-InstanceName`|Tanımlamak için kullanılan [bileşik yapılandırmaları](compositeconfigs.md)|
|`-DependsOn`|Tanımlamak için kullanılan [bileşik yapılandırmaları](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Tanımlamak için kullanılan [bileşik yapılandırmaları](compositeconfigs.md)|
|`-ConfigurationData`|Geçirmek için kullanılan içinde yapılandırılmış [yapılandırma verilerini](configData.md) kullanılmak üzere yapılandırma.|
|`-OutputPath`|Yeri belirtmek için kullanılan, "\<computername\>.mof" dosya derlenecek|

## <a name="adding-your-own-parameters-to-configurations"></a>Kendi parametre yapılandırmalarına ekleme

Yerleşik parametrelerin yanı sıra, kendi parametreleri yapılandırmalarınız için de ekleyebilirsiniz. Doğrudan bir işlev gibi yapılandırma bildirimi içinde parametre bloğu gider. Dışında herhangi bir yapılandırma parametresi blok olmalıdır **düğüm** bildirimleri ve yukarıda herhangi *alma* deyimleri. Parametreler ekleyerek, daha sağlam ve dinamik yapılandırmalarınızı yapabilirsiniz.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>ComputerName parametresi Ekle

Eklediğiniz ilk parametre bir `-Computername` , dinamik olarak bir ".mof" dosyası için derleyebilirsiniz için parametre `-Computername` yapılandırmanıza geçirin. Kullanıcı için bir değer geçirmez durumunda işlevleri gibi da varsayılan bir değer tanımlayabilirsiniz `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Yapılandırmanızı içinde sonra belirtebilirsiniz, `-ComputerName` düğüm engellemeniz tanımlarken parametresi.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Yapılandırmanızı parametrelerle çağırılıyor

İçin yapılandırma parametreleri ekledikten sonra cmdlet ile olduğu gibi bunları kullanabilirsiniz.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Birden çok .mof dosyaları derleme

Düğümü blok, bilgisayar adlarının virgülle ayrılmış bir listesini de kabul edebilir ve her biri için ".mof" dosyaları oluşturur. Geçirilen tüm bilgisayarların için ".mof" dosyaları oluşturmak için aşağıdaki örneği çalıştırabileceğiniz `-ComputerName` parametresi.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a>Gelişmiş parametre yapılandırmaları

Ek olarak bir `-ComputerName` parametresi, hizmet adı ve durum parametrelerini ekleyebiliriz. Aşağıdaki örnek, bir parametre bloğu ile ekler. bir `-ServiceName` parametresi ve dinamik olarak tanımlamak için kullandığı **hizmet** kaynak blok. Ayrıca ekler bir `-State` dinamik olarak tanımlamak için parametre **durumu** içinde **hizmet** kaynak blok.

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

    # It is best practice to implicitly import any required resources or modules.
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
> Daha fazla advacned senaryolarda dinamik verilerinizi yapılandırılmış taşımak için daha anlamlı yapabileceğiniz [yapılandırma verilerini](configData.md).

Örnek yapılandırma şimdi dinamik bir alan `$ServiceName`, ancak bir ad belirtilmezse hatayla sonuçlanır derleme. Bu örnekte olduğu gibi varsayılan bir değer ekleyebilirsiniz.

```powershell
[String]
$ServiceName="Spooler"
```

Bu örnekte, kullanıcı için bir değer belirtmek için yalnızca zorlamak için daha fazla mantıklıdır `$ServiceName` parametresi. `parameter` Özniteliği, daha fazla doğrulama ve işlem hattı desteği, yapılandırmasının parametreleri eklemenize olanak sağlar.

Herhangi bir parametre bildiriminin üstüne ekleyin `parameter` öznitelik bloğuna aşağıdaki örnekte olduğu gibi.

```powershell
[parameter()]
[String]
$ServiceName
```

Her bağımsız değişken belirtebilirsiniz `parameter` tanımlanan parametre denetimi yönleri için özniteliği. Aşağıdaki örnekte `$ServiceName` bir **zorunlu** parametresi.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

İçin `$State` parametresi, biz istediğiniz kullanıcı dışında bir önceden tanımlanmış değerler belirtmelerini engelleyin (gibi çalışıyor, durduruldu) `ValidationSet*`özniteliği engelleyebilir kullanıcı belirtmelerini dışında (örneğin, çalışan bir önceden tanımlanmış değerler Durduruldu). Aşağıdaki örnek ekler `ValidationSet` özniteliğini `$State` parametresi. Biz yapmak istemediğiniz beri `$State` parametre **zorunlu**, biz de varsayılan bir değer eklemeniz gerekir.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Belirtmenize gerek olmayan bir `parameter` özniteliği kullanırken bir `validation` özniteliği.

Daha fazla bilgi edinebilirsiniz `parameter` ve doğrulama öznitelikleri [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Tam olarak parametreli yapılandırma

Artık belirtmesini zorlar parametreli bir yapılandırma sunuyoruz bir `-InstanceName`, `-ServiceName`ve doğrulama `-State` parametresi.

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

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırmaları için Yardım yazma](configHelp.md)
- [Dinamik yapılandırmaları](flow-control-in-configurations.md)
- [Yapılandırma verileri, yapılandırmaları kullanın](configData.md)
- [Ayrı yapılandırma ve ortam verilerini](separatingEnvData.md)
