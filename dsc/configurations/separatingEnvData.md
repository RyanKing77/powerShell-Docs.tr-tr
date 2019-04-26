---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma ve ortam verilerini ayırma
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080042"
---
# <a name="separating-configuration-and-environment-data"></a>Yapılandırma ve ortam verilerini ayırma

>Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

Yapılandırma verilerini kullanarak yapılandırma DSC yapılandırmasından kullanılan verileri ayırmak için yararlı olabilir.
Bunu yaparak, tek bir yapılandırma için birden çok ortamda kullanabilirsiniz.

Örneğin, bir uygulama geliştiriyorsanız geliştirme ve üretim ortamları için bir yapılandırma kullanma ve yapılandırma verilerini, her ortam için verileri belirtmek için kullanın.

## <a name="what-is-configuration-data"></a>Yapılandırma verilerini nedir?

Yapılandırma verilerini bir karma tablosunda tanımlı ve söz konusu yapılandırmayı derlerken bir DSC yapılandırması için geçirilen verilerdir.

Ayrıntılı bir açıklaması için **ConfigurationData** hashtable, bkz: [yapılandırma verilerini kullanarak](configData.md).

## <a name="a-simple-example"></a>Basit bir örnek

Bunun nasıl çalıştığını görmek için basit bir örneğe göz atalım.
Sağlar, tek bir yapılandırma oluşturacağız **IIS** bazı düğümler ve, varsa **Hyper-V** bazılarında mevcuttur:

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

Bu komut dosyasının son satırında geçirme yapılandırma derler `$MyData` değeri olarak **ConfigurationData** parametresi.

İki MOF dosyaları oluşturduğunuz oluşur:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` iki farklı düğümleri her biri kendi belirtir `NodeName` ve `Role`. Yapılandırma dinamik olarak oluşturur **düğüm** alır gelen düğümleri koleksiyonu alarak blokları `$MyData` (özellikle `$AllNodes`) ve söz konusu koleksiyonunda filtre `Role` özelliği...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Geliştirme ve üretim ortamları tanımlamak için yapılandırma verilerini kullanma

Bir Web sitesi geliştirme ve üretim ortamları ayarlamak için tek bir yapılandırması kullanan tam bir örneğe bakalım. Geliştirme ortamında, hem IIS hem de SQL Server tek düğümlerine yüklenir. Üretim ortamında, IIS ve SQL Server ayrı düğümde yüklü. İki farklı ortamlar için verileri belirtmek için bir yapılandırma verileri .psd1 dosyası kullanacağız.

### <a name="configuration-data-file"></a>Yapılandırma verileri dosyası

Geliştirme ve üretim ortamı veri adındaki bir dosyada tanımlarsınız `DevProdEnvData.psd1` gibi:

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

### <a name="configuration-script-file"></a>Yapılandırma komut dosyası

Şimdi Yapılandırması'nda tanımlanan bir `.ps1` dosyası filtreleyeceğiz tanımladığımız içindeki düğümleri `DevProdEnvData.psd1` rollerine göre (`MSSQL`, `Dev`, veya her ikisi de) ve buna göre yapılandırın.
Üretim ortamında bunları iki farklı düğümlere sahipken geliştirme ortamı SQL Server ve IIS bir düğüme sahiptir.
Site içerikleri belirtildiği gibi farklı ayrıca `SiteContents` özellikleri.

Yapılandırma betiğini sonunda diyoruz yapılandırması (MOF belgeye, geçirme derlemeniz) `DevProdEnvData.psd1` olarak `$ConfigurationData` parametresi.

>**Not:** Bu yapılandırma, modülleri gerektirir `xSqlPs` ve `xWebAdministration` hedef düğüme yüklenecek.

Yapılandırma adındaki bir dosyada tanımlayalım `MyWebApp.ps1`:

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

Bu yapılandırma çalıştırdığınızda, üç MOF dosyaları oluşturulur (her biri adlı giriş **AllNodes** dizisi):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Düğümü olmayan verileri kullanma

İçin ek anahtarlar ekleyebilirsiniz **ConfigurationData** bir düğüme özgü olmayan veriler için karma tablo.
Aşağıdaki yapılandırmayı iki Web sitesi varlığını sağlar.
Her Web sitesi için veri tanımlanmış **AllNodes** dizisi.
Dosya `Config.xml` ada sahip başka bir anahtar olarak tanımlarız şekilde iki Web sitesi için kullanılan `NonNodeData`.
İstediğiniz kadar ek anahtarlar ve sonraki her şey adı olduğunu unutmayın.
`NonNodeData` ayrılmış bir sözcük değil yalnızca ne ilave bir anahtar adı verdik olduğu.

Özel değişkeni kullanılarak ek anahtarlara erişmek **$ConfigurationData**.
Bu örnekte, `ConfigFileContents` satırla erişilebilir:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 içinde `File` kaynak blok.


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


## <a name="see-also"></a>Ayrıca bkz:
- [Yapılandırma verilerini kullanma](configData.md)
- [Yapılandırma verilerinde kimlik bilgisi seçeneklerinden](configDataCredentials.md)
- [DSC yapılandırmaları](configurations.md)
