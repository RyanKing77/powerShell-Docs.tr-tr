---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma verilerini kullanma
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727213"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="78cc1-103">DSC yapılandırma verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="78cc1-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="78cc1-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="78cc1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="78cc1-105">Yerleşik DSC kullanarak **ConfigurationData** parametresi bir yapılandırması içinde kullanılabilir verileri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78cc1-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="78cc1-106">Bu farklı ortamlar için veya birden çok düğüm için kullanılabilecek tek bir yapılandırma oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="78cc1-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="78cc1-107">Örneğin, bir uygulama geliştiriyorsanız geliştirme ve üretim ortamları için bir yapılandırma kullanma ve yapılandırma verilerini, her ortam için verileri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="78cc1-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="78cc1-108">Bu konuda yapısını açıklayan **ConfigurationData** karma tablo.</span><span class="sxs-lookup"><span data-stu-id="78cc1-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="78cc1-109">Yapılandırma verilerini kullanma örnekleri için bkz. [yapılandırma ve ortam verilerini ayırma](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="78cc1-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="78cc1-110">ConfigurationData ortak parametresi</span><span class="sxs-lookup"><span data-stu-id="78cc1-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="78cc1-111">DSC yapılandırması ortak bir parametre alır **ConfigurationData**, yapılandırmayı derleme yaptığınızda belirtin.</span><span class="sxs-lookup"><span data-stu-id="78cc1-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="78cc1-112">Derleme yapılandırmaları hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="78cc1-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="78cc1-113">**ConfigurationData** parametredir adlı en az bir anahtar olması gerektiğini bir hashtable **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="78cc1-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="78cc1-114">Bir veya daha fazla diğer anahtarlar da olabilir.</span><span class="sxs-lookup"><span data-stu-id="78cc1-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="78cc1-115">Bu konudaki örnekler tek bir ek anahtar kullanır (adlandırılmış dışında **AllNodes** anahtarı) adlı `NonNodeData`, ancak herhangi bir sayıda ek anahtarlar eklemek ve bunları istediğiniz adı.</span><span class="sxs-lookup"><span data-stu-id="78cc1-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="78cc1-116">Değerini **AllNodes** dizi anahtardır.</span><span class="sxs-lookup"><span data-stu-id="78cc1-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="78cc1-117">Bu dizinin her öğesinin de en az bir anahtar adında gereken bir karma tablodur **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="78cc1-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="78cc1-118">Diğer anahtarlar her karma tablosu da ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="78cc1-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="78cc1-119">Bir özelliği tüm düğümlere uygulanacak bir üye oluşturabilirsiniz **AllNodes** sahip dizi bir **NodeName** , `*`.</span><span class="sxs-lookup"><span data-stu-id="78cc1-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="78cc1-120">Örneğin, her düğüm vermek için bir `LogPath` özelliği, bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="78cc1-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="78cc1-121">Bu özellik adıyla ekleme eşdeğerdir `LogPath` değeriyle `"C:\Logs"` her birine diğer bloklardan (`VM-1`, `VM-2`, ve `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="78cc1-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="78cc1-122">ConfigurationData hashtable tanımlama</span><span class="sxs-lookup"><span data-stu-id="78cc1-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="78cc1-123">Tanımlayabileceğiniz **ConfigurationData** olarak aynı betiği yapılandırması (olduğu gibi önceki örneklerimizde) içinde bir değişken veya ayrı bir `.psd1` dosya.</span><span class="sxs-lookup"><span data-stu-id="78cc1-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="78cc1-124">Tanımlamak için **ConfigurationData** içinde bir `.psd1` dosya, yapılandırma verilerini temsil eden karma tablosu içeren bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78cc1-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="78cc1-125">Örneğin, adında bir dosya oluşturabilirsiniz `MyData.psd1` aşağıdaki içeriklerle:</span><span class="sxs-lookup"><span data-stu-id="78cc1-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="78cc1-126">Yapılandırma verilerini içeren bir yapılandırma derleme</span><span class="sxs-lookup"><span data-stu-id="78cc1-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="78cc1-127">Yapılandırma verilerini, tanımladığınız bir yapılandırmayı derlemek için yapılandırma verilerini değeri olarak geçirirsiniz **ConfigurationData** parametresi.</span><span class="sxs-lookup"><span data-stu-id="78cc1-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="78cc1-128">Bu her giriş için bir MOF dosyası oluşturacak **AllNodes** dizisi.</span><span class="sxs-lookup"><span data-stu-id="78cc1-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="78cc1-129">Her bir MOF dosyası adında `NodeName` karşılık gelen bir dizi giriş özelliği.</span><span class="sxs-lookup"><span data-stu-id="78cc1-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="78cc1-130">Örneğin, yapılandırma verilerini olarak tanımlarsanız `MyData.psd1` yapılandırma derleme dosyası yukarıdaki oluşturulacak hem de `VM-1.mof` ve `VM-2.mof` dosyaları.</span><span class="sxs-lookup"><span data-stu-id="78cc1-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="78cc1-131">Bir değişken kullanarak yapılandırma verilerini bir yapılandırma derleme</span><span class="sxs-lookup"><span data-stu-id="78cc1-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="78cc1-132">Aynı bir değişken olarak tanımlanan yapılandırma verilerini kullanmak için `.ps1` dosya yapılandırma, değeri olarak değişken adını geçişi **ConfigurationData** yapılandırması derlenirken parametresi:</span><span class="sxs-lookup"><span data-stu-id="78cc1-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="78cc1-133">Bir veri dosyası kullanarak yapılandırma verilerini bir yapılandırma derleme</span><span class="sxs-lookup"><span data-stu-id="78cc1-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="78cc1-134">.Psd1 dosyasında tanımlanan yapılandırma verilerini kullanmak için bu dosyanın adını ve yolunu değeri olarak geçirdiğiniz **ConfigurationData** yapılandırması derlenirken parametresi:</span><span class="sxs-lookup"><span data-stu-id="78cc1-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="78cc1-135">Bir yapılandırmada ConfigurationData değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="78cc1-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="78cc1-136">DSC yapılandırma komut dosyasında kullanılabilen aşağıdaki özel değişkenler sağlar:</span><span class="sxs-lookup"><span data-stu-id="78cc1-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="78cc1-137">**$AllNodes** tüm koleksiyon içinde tanımlanan düğümlerinin başvurduğu **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="78cc1-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="78cc1-138">Filtre uygulayabilirsiniz **AllNodes** kullanarak koleksiyon **. Birlikte WHERE()** ve **. ForEach()** .</span><span class="sxs-lookup"><span data-stu-id="78cc1-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="78cc1-139">**ConfigurationData** bir yapılandırması derlenirken parametre olarak geçirilen tüm karma tablosuna başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="78cc1-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="78cc1-140">**MyTypeName** içeren [yapılandırma](configurations.md) adı değişkeni kullanılır.</span><span class="sxs-lookup"><span data-stu-id="78cc1-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="78cc1-141">Örneğin, yapılandırmada `MyDscConfiguration`, `$MyTypeName` değerine sahip `MyDscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="78cc1-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="78cc1-142">**Düğüm** belirli bir giriş başvurduğu **AllNodes** kullanarak filtrelenmiştir sonra koleksiyonu **. Birlikte WHERE()** veya **. ForEach()** .</span><span class="sxs-lookup"><span data-stu-id="78cc1-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="78cc1-143">Daha fazla bilgi bu yöntemleri hakkında [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span><span class="sxs-lookup"><span data-stu-id="78cc1-143">You can read more about these methods in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="78cc1-144">Düğümü olmayan verileri kullanma</span><span class="sxs-lookup"><span data-stu-id="78cc1-144">Using non-node data</span></span>

<span data-ttu-id="78cc1-145">Önceki örneklerde anlatıldığı gibi **ConfigurationData** hashtable ek olarak gerekli bir veya daha fazla anahtar sağlayabilirsiniz **AllNodes** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="78cc1-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="78cc1-146">Bu konudaki örneklerde, biz yalnızca tek bir ek düğüm kullanılan ve ona `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="78cc1-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="78cc1-147">Ancak, herhangi bir sayıda ek anahtarlar tanımlayın ve bunları istediğiniz adı.</span><span class="sxs-lookup"><span data-stu-id="78cc1-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="78cc1-148">Düğümü olmayan verileri kullanan bir örnek için bkz: [yapılandırma ve ortam verilerini ayırma](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="78cc1-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="78cc1-149">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="78cc1-149">See Also</span></span>

- [<span data-ttu-id="78cc1-150">Yapılandırma verilerinde kimlik bilgisi seçeneklerinden</span><span class="sxs-lookup"><span data-stu-id="78cc1-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="78cc1-151">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="78cc1-151">DSC Configurations</span></span>](configurations.md)