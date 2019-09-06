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
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="9a6c8-103">Yapılandırmalara Parametre Ekleme</span><span class="sxs-lookup"><span data-stu-id="9a6c8-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="9a6c8-104">LIKE Işlevleri, kullanıcı girişine göre daha dinamik yapılandırmalara izin vermek için [yapılandırma](configurations.md) parametrelenebilir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="9a6c8-105">Adımlar, [parametrelere sahip işlevlerde](/powershell/module/microsoft.powershell.core/about/about_functions)açıklananlara benzerdir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="9a6c8-106">Bu örnek, "biriktirici" hizmetini "çalışıyor" olarak yapılandıran temel bir yapılandırmayla başlar.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="9a6c8-107">Yerleşik yapılandırma parametreleri</span><span class="sxs-lookup"><span data-stu-id="9a6c8-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="9a6c8-108">Ancak, bir Işlevden farklı olarak, [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) özniteliği hiçbir işlev ekler.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="9a6c8-109">[Sık kullanılan parametrelere](/powershell/module/microsoft.powershell.core/about/about_commonparameters)ek olarak, konfigürasyonlar, bunları tanımlamanıza gerek kalmadan, aşağıdaki yerleşik parametreleri de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="9a6c8-110">Parametre</span><span class="sxs-lookup"><span data-stu-id="9a6c8-110">Parameter</span></span>  |<span data-ttu-id="9a6c8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a6c8-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="9a6c8-112">[Bileşik yapılandırmaların](compositeconfigs.md) tanımlanması için kullanılır</span><span class="sxs-lookup"><span data-stu-id="9a6c8-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="9a6c8-113">[Bileşik yapılandırmaların](compositeconfigs.md) tanımlanması için kullanılır</span><span class="sxs-lookup"><span data-stu-id="9a6c8-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="9a6c8-114">[Bileşik yapılandırmaların](compositeconfigs.md) tanımlanması için kullanılır</span><span class="sxs-lookup"><span data-stu-id="9a6c8-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="9a6c8-115">Yapılandırmada kullanılmak üzere yapılandırılmış [yapılandırma verilerini](configData.md) geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="9a6c8-116">"\<ComputerName\>. mof" dosyanızın derlenebileceği yeri belirtmek için kullanılır</span><span class="sxs-lookup"><span data-stu-id="9a6c8-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="9a6c8-117">Yapılandırmalara kendi parametrelerinizi ekleme</span><span class="sxs-lookup"><span data-stu-id="9a6c8-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="9a6c8-118">Yerleşik parametrelere ek olarak, kendi parametrelerinizi de yapılandırmalara ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="9a6c8-119">Parametre bloğu, doğrudan yapılandırma bildiriminin içinde, tıpkı bir Işlev gibi gider.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="9a6c8-120">Bir yapılandırma parametresi bloğunun herhangi bir **düğüm** bildiriminin dışında ve *içeri aktarma* deyimlerinin üzerinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="9a6c8-121">Parametreleri ekleyerek, yapılandırmalarınızın daha sağlam ve dinamik olmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="9a6c8-122">ComputerName parametresi Ekle</span><span class="sxs-lookup"><span data-stu-id="9a6c8-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="9a6c8-123">Ekleyebileceğiniz ilk parametre, yapılandırmanıza geçirdiğiniz bir " `-Computername` . mof" dosyasını dinamik olarak derleyebilmeniz `-Computername` için bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="9a6c8-124">Ayrıca, örneğin, kullanıcının bir değer geçirmezse bir varsayılan değer de tanımlayabilirsiniz.`-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="9a6c8-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="9a6c8-125">Yapılandırmanızın içinde, düğüm bloğunu tanımlarken `-ComputerName` parametresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="9a6c8-126">Yapılandırma parametrelerini çağırma</span><span class="sxs-lookup"><span data-stu-id="9a6c8-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="9a6c8-127">Yapılandırmanıza parametreler ekledikten sonra, bunları bir cmdlet 'le yaptığınız gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="9a6c8-128">Birden çok. mof dosyası derleme</span><span class="sxs-lookup"><span data-stu-id="9a6c8-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="9a6c8-129">Düğüm bloğu Ayrıca, virgülle ayrılmış bir bilgisayar adları listesi kabul edebilir ve her biri için ". mof" dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="9a6c8-130">`-ComputerName` Parametreye geçirilen tüm bilgisayarlar için ". mof" dosyaları oluşturmak için aşağıdaki örneği çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="9a6c8-131">Yapılandırmalarda Gelişmiş parametreler</span><span class="sxs-lookup"><span data-stu-id="9a6c8-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="9a6c8-132">Bir `-ComputerName` parametreye ek olarak, hizmet adı ve eyalet için parametreler ekleyebiliriz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="9a6c8-133">Aşağıdaki örnek, parametresi ile `-ServiceName` bir parametre bloğu ekler ve **hizmet** kaynak bloğunu dinamik olarak tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="9a6c8-134">Ayrıca, **hizmet** kaynak `-State` bloğunda **durumu** dinamik olarak tanımlamak için bir parametre ekler.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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
> <span data-ttu-id="9a6c8-135">Daha fazla işlem senaryosunda, dinamik verilerinizi yapılandırılmış bir [yapılandırma verilerine](configData.md)taşımak daha mantıklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="9a6c8-136">Örnek yapılandırma artık dinamik `$ServiceName`bir şekilde sürer, ancak belirtilmemişse bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="9a6c8-137">Bu örneğe benzer bir varsayılan değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="9a6c8-138">Bu örnekte, kullanıcının `$ServiceName` parametre için bir değer belirtmesini zorlamak için de daha anlamlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="9a6c8-139">Özniteliği `parameter` , yapılandırmanızın parametrelerine daha fazla doğrulama ve işlem hattı desteği eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="9a6c8-140">Herhangi bir parametre bildiriminde, aşağıdaki örnekte `parameter` olduğu gibi öznitelik bloğunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="9a6c8-141">Tanımlı parametrenin yönlerini denetlemek için her `parameter` bir özniteliğin bağımsız değişkenlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="9a6c8-142">Aşağıdaki örnek `$ServiceName` **zorunlu** bir parametre oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="9a6c8-143">Parametresi için, kullanıcının önceden tanımlanmış bir küme dışında (çalışıyor, durduruldu gibi `ValidationSet*`) değerler belirtmesini engellemek istiyoruz. öznitelik, kullanıcının önceden tanımlanmış bir küme dışında değerler belirtmesini önler (örneğin, `$State` Durduruldu).</span><span class="sxs-lookup"><span data-stu-id="9a6c8-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="9a6c8-144">Aşağıdaki örnek, `ValidationSet` `$State` parametresine özniteliğini ekler.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="9a6c8-145">`$State` Parametresini **zorunlu**hale getirmek istemediğimiz için, bunun için varsayılan bir değer eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="9a6c8-146">Özniteliği kullanırken bir `parameter` öznitelik belirtmeniz gerekmez. `validation`</span><span class="sxs-lookup"><span data-stu-id="9a6c8-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="9a6c8-147">`parameter` [About_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters)' de ve doğrulama öznitelikleri hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="9a6c8-148">Tam parametreli yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9a6c8-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="9a6c8-149">Artık, kullanıcıyı bir `-InstanceName`, `-ServiceName`, ve `-State` parametresini doğrulama işlemini zorlayan parametreli bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9a6c8-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a6c8-150">See also</span></span>

- [<span data-ttu-id="9a6c8-151">DSC yapılandırması için yardım yazma</span><span class="sxs-lookup"><span data-stu-id="9a6c8-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="9a6c8-152">Dinamik yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9a6c8-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="9a6c8-153">Yapılandırmalarınızın yapılandırma verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="9a6c8-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="9a6c8-154">Yapılandırma ve ortam verilerini ayır</span><span class="sxs-lookup"><span data-stu-id="9a6c8-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
