---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma ve ortam verilerini ayırma
ms.openlocfilehash: 24a92e5e4f15959498b57a1488a688d5548f3585
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405725"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="2f51f-103">Yapılandırma ve ortam verilerini ayırma</span><span class="sxs-lookup"><span data-stu-id="2f51f-103">Separating configuration and environment data</span></span>

><span data-ttu-id="2f51f-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2f51f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2f51f-105">Yapılandırma verilerini kullanarak yapılandırma DSC yapılandırmasından kullanılan verileri ayırmak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f51f-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="2f51f-106">Bunu yaparak, tek bir yapılandırma için birden çok ortamda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f51f-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="2f51f-107">Örneğin, bir uygulama geliştiriyorsanız geliştirme ve üretim ortamları için bir yapılandırma kullanma ve yapılandırma verilerini, her ortam için verileri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f51f-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="2f51f-108">Yapılandırma verilerini nedir?</span><span class="sxs-lookup"><span data-stu-id="2f51f-108">What is configuration data?</span></span>

<span data-ttu-id="2f51f-109">Yapılandırma verilerini bir karma tablosunda tanımlı ve söz konusu yapılandırmayı derlerken bir DSC yapılandırması için geçirilen verilerdir.</span><span class="sxs-lookup"><span data-stu-id="2f51f-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="2f51f-110">Ayrıntılı bir açıklaması için **ConfigurationData** hashtable, bkz: [yapılandırma verilerini kullanarak](configData.md).</span><span class="sxs-lookup"><span data-stu-id="2f51f-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="2f51f-111">Basit bir örnek</span><span class="sxs-lookup"><span data-stu-id="2f51f-111">A simple example</span></span>

<span data-ttu-id="2f51f-112">Bunun nasıl çalıştığını görmek için basit bir örneğe göz atalım.</span><span class="sxs-lookup"><span data-stu-id="2f51f-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="2f51f-113">Sağlar, tek bir yapılandırma oluşturacağız **IIS** bazı düğümler ve, varsa **Hyper-V** bazılarında mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="2f51f-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

<span data-ttu-id="2f51f-114">Bu komut dosyasının son satırında geçirme yapılandırma derler `$MyData` değeri olarak **ConfigurationData** parametresi.</span><span class="sxs-lookup"><span data-stu-id="2f51f-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="2f51f-115">İki MOF dosyaları oluşturduğunuz oluşur:</span><span class="sxs-lookup"><span data-stu-id="2f51f-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="2f51f-116">`$MyData` iki farklı düğümleri her biri kendi belirtir `NodeName` ve `Role`.</span><span class="sxs-lookup"><span data-stu-id="2f51f-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="2f51f-117">Yapılandırma dinamik olarak oluşturur **düğüm** alır gelen düğümleri koleksiyonu alarak blokları `$MyData` (özellikle `$AllNodes`) ve söz konusu koleksiyonunda filtre `Role` özelliği...</span><span class="sxs-lookup"><span data-stu-id="2f51f-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="2f51f-118">Geliştirme ve üretim ortamları tanımlamak için yapılandırma verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="2f51f-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="2f51f-119">Bir Web sitesi geliştirme ve üretim ortamları ayarlamak için tek bir yapılandırması kullanan tam bir örneğe bakalım.</span><span class="sxs-lookup"><span data-stu-id="2f51f-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="2f51f-120">Geliştirme ortamında, hem IIS hem de SQL Server tek düğümlerine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2f51f-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="2f51f-121">Üretim ortamında, IIS ve SQL Server ayrı düğümde yüklü.</span><span class="sxs-lookup"><span data-stu-id="2f51f-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="2f51f-122">İki farklı ortamlar için verileri belirtmek için bir yapılandırma verileri .psd1 dosyası kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="2f51f-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

 ### <a name="configuration-data-file"></a><span data-ttu-id="2f51f-123">Yapılandırma verileri dosyası</span><span class="sxs-lookup"><span data-stu-id="2f51f-123">Configuration data file</span></span>

<span data-ttu-id="2f51f-124">Geliştirme ve üretim ortamı veri adındaki bir dosyada tanımlarsınız `DevProdEnvData.psd1` gibi:</span><span class="sxs-lookup"><span data-stu-id="2f51f-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a><span data-ttu-id="2f51f-125">Yapılandırma komut dosyası</span><span class="sxs-lookup"><span data-stu-id="2f51f-125">Configuration script file</span></span>

<span data-ttu-id="2f51f-126">Şimdi Yapılandırması'nda tanımlanan bir `.ps1` dosyası filtreleyeceğiz tanımladığımız içindeki düğümleri `DevProdEnvData.psd1` rollerine göre (`MSSQL`, `Dev`, veya her ikisi de) ve buna göre yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="2f51f-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="2f51f-127">Üretim ortamında bunları iki farklı düğümlere sahipken geliştirme ortamı SQL Server ve IIS bir düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2f51f-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="2f51f-128">Site içerikleri belirtildiği gibi farklı ayrıca `SiteContents` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2f51f-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="2f51f-129">Yapılandırma betiğini sonunda diyoruz yapılandırması (MOF belgeye, geçirme derlemeniz) `DevProdEnvData.psd1` olarak `$ConfigurationData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2f51f-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="2f51f-130">**Not:** Bu yapılandırma, modülleri gerektirir `xSqlPs` ve `xWebAdministration` hedef düğüme yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="2f51f-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="2f51f-131">Yapılandırma adındaki bir dosyada tanımlayalım `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="2f51f-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="2f51f-132">Bu yapılandırma çalıştırdığınızda, üç MOF dosyaları oluşturulur (her biri adlı giriş **AllNodes** dizisi):</span><span class="sxs-lookup"><span data-stu-id="2f51f-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="2f51f-133">Düğümü olmayan verileri kullanma</span><span class="sxs-lookup"><span data-stu-id="2f51f-133">Using non-node data</span></span>

<span data-ttu-id="2f51f-134">İçin ek anahtarlar ekleyebilirsiniz **ConfigurationData** bir düğüme özgü olmayan veriler için karma tablo.</span><span class="sxs-lookup"><span data-stu-id="2f51f-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="2f51f-135">Aşağıdaki yapılandırmayı iki Web sitesi varlığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f51f-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="2f51f-136">Her Web sitesi için veri tanımlanmış **AllNodes** dizisi.</span><span class="sxs-lookup"><span data-stu-id="2f51f-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="2f51f-137">Dosya `Config.xml` ada sahip başka bir anahtar olarak tanımlarız şekilde iki Web sitesi için kullanılan `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="2f51f-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="2f51f-138">İstediğiniz kadar ek anahtarlar ve sonraki her şey adı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2f51f-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="2f51f-139">`NonNodeData` ayrılmış bir sözcük değil yalnızca ne ilave bir anahtar adı verdik olduğu.</span><span class="sxs-lookup"><span data-stu-id="2f51f-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="2f51f-140">Özel değişkeni kullanılarak ek anahtarlara erişmek **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="2f51f-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="2f51f-141">Bu örnekte, `ConfigFileContents` satırla erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="2f51f-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="2f51f-142">içinde `File` kaynak blok.</span><span class="sxs-lookup"><span data-stu-id="2f51f-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="2f51f-143">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2f51f-143">See Also</span></span>
- [<span data-ttu-id="2f51f-144">Yapılandırma verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="2f51f-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="2f51f-145">Yapılandırma verilerinde kimlik bilgisi seçeneklerinden</span><span class="sxs-lookup"><span data-stu-id="2f51f-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="2f51f-146">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="2f51f-146">DSC Configurations</span></span>](configurations.md)
