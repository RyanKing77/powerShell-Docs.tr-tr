---
ms.date: 12/12/2018
keywords: DSC, powershell, kaynak, Galeri, Kurulum
title: Yapılandırmalara Parametre Ekleme
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080269"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="4f2d4-103">Yapılandırmalara Parametre Ekleme</span><span class="sxs-lookup"><span data-stu-id="4f2d4-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="4f2d4-104">İşlevler, ister [yapılandırmaları](configurations.md) kullanıcı girişini temel alarak daha dinamik yapılandırmaları izin vermek için parametreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="4f2d4-105">İçinde açıklananlara benzer adımlarla [parametreleri olan işlevlere](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="4f2d4-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="4f2d4-106">Bu örnek, "" "Biriktirici" hizmetinin çalışmasını yapılandırır bir temel yapılandırmayla başlatır.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="4f2d4-107">Yerleşik yapılandırma parametreleri</span><span class="sxs-lookup"><span data-stu-id="4f2d4-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="4f2d4-108">Bir işlev aksine, [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) öznitelik hiçbir işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="4f2d4-109">Ek olarak [ortak parametreleri](/powershell/module/microsoft.powershell.core/about/about_commonparameters), yapılandırmaları, aşağıdaki parametreleri olarak tanımlamak gerek kalmadan yerleşik olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="4f2d4-110">Parametre</span><span class="sxs-lookup"><span data-stu-id="4f2d4-110">Parameter</span></span>  |<span data-ttu-id="4f2d4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f2d4-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="4f2d4-112">Tanımlamak için kullanılan [bileşik yapılandırmaları](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="4f2d4-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="4f2d4-113">Tanımlamak için kullanılan [bileşik yapılandırmaları](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="4f2d4-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="4f2d4-114">Tanımlamak için kullanılan [bileşik yapılandırmaları](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="4f2d4-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="4f2d4-115">Geçirmek için kullanılan içinde yapılandırılmış [yapılandırma verilerini](configData.md) kullanılmak üzere yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="4f2d4-116">Yeri belirtmek için kullanılan, "\<computername\>.mof" dosya derlenecek</span><span class="sxs-lookup"><span data-stu-id="4f2d4-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="4f2d4-117">Kendi parametre yapılandırmalarına ekleme</span><span class="sxs-lookup"><span data-stu-id="4f2d4-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="4f2d4-118">Yerleşik parametrelerin yanı sıra, kendi parametreleri yapılandırmalarınız için de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="4f2d4-119">Doğrudan bir işlev gibi yapılandırma bildirimi içinde parametre bloğu gider.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="4f2d4-120">Dışında herhangi bir yapılandırma parametresi blok olmalıdır **düğüm** bildirimleri ve yukarıda herhangi *alma* deyimleri.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="4f2d4-121">Parametreler ekleyerek, daha sağlam ve dinamik yapılandırmalarınızı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="4f2d4-122">ComputerName parametresi Ekle</span><span class="sxs-lookup"><span data-stu-id="4f2d4-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="4f2d4-123">Eklediğiniz ilk parametre bir `-Computername` , dinamik olarak bir ".mof" dosyası için derleyebilirsiniz için parametre `-Computername` yapılandırmanıza geçirin.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="4f2d4-124">Kullanıcı için bir değer geçirmez durumunda işlevleri gibi da varsayılan bir değer tanımlayabilirsiniz `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="4f2d4-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="4f2d4-125">Yapılandırmanızı içinde sonra belirtebilirsiniz, `-ComputerName` düğüm engellemeniz tanımlarken parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="4f2d4-126">Yapılandırmanızı parametrelerle çağırılıyor</span><span class="sxs-lookup"><span data-stu-id="4f2d4-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="4f2d4-127">İçin yapılandırma parametreleri ekledikten sonra cmdlet ile olduğu gibi bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="4f2d4-128">Birden çok .mof dosyaları derleme</span><span class="sxs-lookup"><span data-stu-id="4f2d4-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="4f2d4-129">Düğümü blok, bilgisayar adlarının virgülle ayrılmış bir listesini de kabul edebilir ve her biri için ".mof" dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="4f2d4-130">Geçirilen tüm bilgisayarların için ".mof" dosyaları oluşturmak için aşağıdaki örneği çalıştırabileceğiniz `-ComputerName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="4f2d4-131">Gelişmiş parametre yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="4f2d4-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="4f2d4-132">Ek olarak bir `-ComputerName` parametresi, hizmet adı ve durum parametrelerini ekleyebiliriz.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="4f2d4-133">Aşağıdaki örnek, bir parametre bloğu ile ekler. bir `-ServiceName` parametresi ve dinamik olarak tanımlamak için kullandığı **hizmet** kaynak blok.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="4f2d4-134">Ayrıca ekler bir `-State` dinamik olarak tanımlamak için parametre **durumu** içinde **hizmet** kaynak blok.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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
> <span data-ttu-id="4f2d4-135">Daha fazla advacned senaryolarda dinamik verilerinizi yapılandırılmış taşımak için daha anlamlı yapabileceğiniz [yapılandırma verilerini](configData.md).</span><span class="sxs-lookup"><span data-stu-id="4f2d4-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="4f2d4-136">Örnek yapılandırma şimdi dinamik bir alan `$ServiceName`, ancak bir ad belirtilmezse hatayla sonuçlanır derleme.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="4f2d4-137">Bu örnekte olduğu gibi varsayılan bir değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="4f2d4-138">Bu örnekte, kullanıcı için bir değer belirtmek için yalnızca zorlamak için daha fazla mantıklıdır `$ServiceName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="4f2d4-139">`parameter` Özniteliği, daha fazla doğrulama ve işlem hattı desteği, yapılandırmasının parametreleri eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="4f2d4-140">Herhangi bir parametre bildiriminin üstüne ekleyin `parameter` öznitelik bloğuna aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="4f2d4-141">Her bağımsız değişken belirtebilirsiniz `parameter` tanımlanan parametre denetimi yönleri için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="4f2d4-142">Aşağıdaki örnekte `$ServiceName` bir **zorunlu** parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="4f2d4-143">İçin `$State` parametresi, biz istediğiniz kullanıcı dışında bir önceden tanımlanmış değerler belirtmelerini engelleyin (gibi çalışıyor, durduruldu) `ValidationSet*`özniteliği engelleyebilir kullanıcı belirtmelerini dışında (örneğin, çalışan bir önceden tanımlanmış değerler Durduruldu).</span><span class="sxs-lookup"><span data-stu-id="4f2d4-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="4f2d4-144">Aşağıdaki örnek ekler `ValidationSet` özniteliğini `$State` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="4f2d4-145">Biz yapmak istemediğiniz beri `$State` parametre **zorunlu**, biz de varsayılan bir değer eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="4f2d4-146">Belirtmenize gerek olmayan bir `parameter` özniteliği kullanırken bir `validation` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="4f2d4-147">Daha fazla bilgi edinebilirsiniz `parameter` ve doğrulama öznitelikleri [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4f2d4-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="4f2d4-148">Tam olarak parametreli yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4f2d4-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="4f2d4-149">Artık belirtmesini zorlar parametreli bir yapılandırma sunuyoruz bir `-InstanceName`, `-ServiceName`ve doğrulama `-State` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4f2d4-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f2d4-150">See also</span></span>

- [<span data-ttu-id="4f2d4-151">DSC yapılandırmaları için Yardım yazma</span><span class="sxs-lookup"><span data-stu-id="4f2d4-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="4f2d4-152">Dinamik yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="4f2d4-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="4f2d4-153">Yapılandırma verileri, yapılandırmaları kullanın</span><span class="sxs-lookup"><span data-stu-id="4f2d4-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="4f2d4-154">Ayrı yapılandırma ve ortam verilerini</span><span class="sxs-lookup"><span data-stu-id="4f2d4-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
