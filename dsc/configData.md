---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Yapılandırma verileri kullanma"
ms.openlocfilehash: b56a3f970b0b5121585dc4ed2f32da3243b980bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="efb75-103">DSC yapılandırma verileri kullanma</span><span class="sxs-lookup"><span data-stu-id="efb75-103">Using configuration data in DSC</span></span>

><span data-ttu-id="efb75-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="efb75-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="efb75-105">Yerleşik DSC kullanarak **ConfigurationData** parametresi, içinde bir yapılandırması kullanılabilir veri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efb75-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span> <span data-ttu-id="efb75-106">Bu, farklı ortamlar için veya birden çok düğüm için kullanılan tek bir yapılandırma oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="efb75-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span> <span data-ttu-id="efb75-107">Örneğin, bir uygulama geliştiriyorsanız, geliştirme ve üretim ortamları için bir yapılandırma kullanın ve yapılandırma verilerini her ortam için verileri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="efb75-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="efb75-108">Bu konuda yapısını açıklayan **ConfigurationData** hashtable.</span><span class="sxs-lookup"><span data-stu-id="efb75-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span> <span data-ttu-id="efb75-109">Yapılandırma verileri kullanma örnekleri için bkz: [yapılandırma ve ortam verilerin ayrılmasını](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="efb75-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="efb75-110">ConfigurationData ortak parametresi</span><span class="sxs-lookup"><span data-stu-id="efb75-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="efb75-111">DSC yapılandırması bir ortak parametresi alan **ConfigurationData**, yapılandırmayı derleme zaman belirtin.</span><span class="sxs-lookup"><span data-stu-id="efb75-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span> <span data-ttu-id="efb75-112">Derleme yapılandırmaları hakkında daha fazla bilgi için bkz: [DSC yapılandırmaları](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="efb75-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="efb75-113">**ConfigurationData** parametredir adlı en az bir anahtar olmalıdır hasthtable **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="efb75-113">The **ConfigurationData** parameter is a hasthtable that must have at least one key named **AllNodes**.</span></span> <span data-ttu-id="efb75-114">Bir veya daha fazla diğer anahtarlar da olabilir.</span><span class="sxs-lookup"><span data-stu-id="efb75-114">It can also have one or more other keys.</span></span>

><span data-ttu-id="efb75-115">**Not:** bu konudaki örnekler tek bir ek anahtar kullanır (adlandırılmış dışında **AllNodes** anahtarı) adlı `NonNodeData`, ancak herhangi bir ek anahtar içerir ve bunları istediğiniz ad.</span><span class="sxs-lookup"><span data-stu-id="efb75-115">**Note:** The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

<span data-ttu-id="efb75-116">Değeri **AllNodes** bir dizi bir anahtardır.</span><span class="sxs-lookup"><span data-stu-id="efb75-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="efb75-117">Her bu dizinin de adlı en az bir anahtar olmalıdır bir karma tablosu öğesidir **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="efb75-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

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

<span data-ttu-id="efb75-118">Diğer anahtarlar her karma tablosu da ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="efb75-118">You can add other keys to each hash table as well:</span></span>

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

<span data-ttu-id="efb75-119">Bir özelliği tüm düğümlere uygulanacak üyesi oluşturabilirsiniz **AllNodes** sahip dizi bir **NodeName** , `*`.</span><span class="sxs-lookup"><span data-stu-id="efb75-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span> <span data-ttu-id="efb75-120">Örneğin, her düğüme vermek için bir `LogPath` özelliği, bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="efb75-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

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

<span data-ttu-id="efb75-121">Bu özellik adıyla ekleme eşdeğerdir `LogPath` değerini `"C:\Logs"` her bir diğer blokları (`VM-1`, `VM-2`, ve `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="efb75-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="efb75-122">ConfigurationData hashtable tanımlama</span><span class="sxs-lookup"><span data-stu-id="efb75-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="efb75-123">Tanımlayabileceğiniz **ConfigurationData** herhangi bir yapılandırma (olduğu gibi önceki örneklerde) ile aynı betiği içinde bir değişken olarak veya ayrı bir `.psd1` dosyası.</span><span class="sxs-lookup"><span data-stu-id="efb75-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span> <span data-ttu-id="efb75-124">Tanımlamak için **ConfigurationData** içinde bir `.psd1` dosya, yapılandırma verilerini temsil eden hashtable içeren bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="efb75-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="efb75-125">Örneğin, adında bir dosya oluşturabilirsiniz `MyData.psd1` aşağıdaki içeriğe sahip:</span><span class="sxs-lookup"><span data-stu-id="efb75-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

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

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="efb75-126">Yapılandırma verilerini bir yapılandırmayla derleme</span><span class="sxs-lookup"><span data-stu-id="efb75-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="efb75-127">Değeri olarak yapılandırma verilerini geçirdiğiniz yapılandırma verileri için tanımladığınız bir yapılandırma derlemek için **ConfigurationData** parametresi.</span><span class="sxs-lookup"><span data-stu-id="efb75-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="efb75-128">Bu her giriş için bir MOF dosyası oluşturacak **AllNodes** dizi.</span><span class="sxs-lookup"><span data-stu-id="efb75-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="efb75-129">Her MOF dosyası adında `NodeName` karşılık gelen bir dizi girişi özelliği.</span><span class="sxs-lookup"><span data-stu-id="efb75-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="efb75-130">Örneğin, yapılandırma verilerini de tanımlarsanız `MyData.psd1` bir yapılandırma derleme dosyası yukarıdaki her ikisi de oluşturmak `VM-1.mof` ve `VM-2.mof` dosyaları.</span><span class="sxs-lookup"><span data-stu-id="efb75-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="efb75-131">Bir yapılandırma ile yapılandırma verilerini bir değişken kullanarak derleme</span><span class="sxs-lookup"><span data-stu-id="efb75-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="efb75-132">Aynı değişken olarak tanımlanan yapılandırma verilerini kullanmak için `.ps1` dosya yapılandırma değeri olarak değişken adını geçişi **ConfigurationData** yapılandırması derlenirken parametre:</span><span class="sxs-lookup"><span data-stu-id="efb75-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="efb75-133">Bir yapılandırma ile yapılandırma verilerini bir veri dosyası kullanarak derleme</span><span class="sxs-lookup"><span data-stu-id="efb75-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="efb75-134">.Psd1 dosyasında tanımlanan yapılandırma verilerini kullanmak için bu dosyanın adını ve yolunu değeri olarak geçirdiğiniz **ConfigurationData** yapılandırması derlenirken parametre:</span><span class="sxs-lookup"><span data-stu-id="efb75-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="efb75-135">Bir yapılandırmada ConfigurationData değişkenlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="efb75-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="efb75-136">DSC yapılandırma komut dosyasında kullanılan üç özel değişkenler sağlar: **$AllNodes**, **$Node**, ve **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="efb75-136">DSC provides three special variables that can be used in a configuration script: **$AllNodes**, **$Node**, and **$ConfigurationData**.</span></span>

- <span data-ttu-id="efb75-137">**$AllNodes** tanımlanan düğümlerinin tüm koleksiyon başvurduğu **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="efb75-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="efb75-138">Filtre uygulayabilirsiniz **AllNodes** kullanarak koleksiyon **. WHERE()** ve **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="efb75-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="efb75-139">**Düğüm** belirli bir giriş başvurduğu **AllNodes** kullanarak filtre sonra koleksiyon **. WHERE()** veya **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="efb75-139">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
- <span data-ttu-id="efb75-140">**ConfigurationData** bir yapılandırma derlerken parametre olarak geçirilen tüm karma tablosuna başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="efb75-140">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="efb75-141">Düğümü olmayan verileri kullanma</span><span class="sxs-lookup"><span data-stu-id="efb75-141">Using non-node data</span></span>

<span data-ttu-id="efb75-142">Önceki örneklerde anlatıldığı gibi **ConfigurationData** hashtable ek olarak gerekli bir veya daha fazla anahtarları olabilir **AllNodes** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="efb75-142">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="efb75-143">Bu konudaki örneklerde, biz yalnızca tek bir ek düğüm kullanılan ve onu adlı `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="efb75-143">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span> <span data-ttu-id="efb75-144">Ancak, herhangi bir ek anahtar sayısını tanımlayın ve bunları istediğiniz adı.</span><span class="sxs-lookup"><span data-stu-id="efb75-144">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="efb75-145">Düğümü olmayan verileri kullanarak bir örnek için bkz: [yapılandırma ve ortam verilerin ayrılmasını](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="efb75-145">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="efb75-146">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="efb75-146">See Also</span></span>
- [<span data-ttu-id="efb75-147">Yapılandırma verilerini seçeneklerinde kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="efb75-147">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="efb75-148">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="efb75-148">DSC Configurations</span></span>](configurations.md)

