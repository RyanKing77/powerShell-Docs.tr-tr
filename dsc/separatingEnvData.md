---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma ve ortam verilerini ayırma
ms.openlocfilehash: 3c7f1ba93b4438b3eb440dc1f2349eff0606ac0a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188131"
---
# <a name="separating-configuration-and-environment-data"></a>Yapılandırma ve ortam verilerini ayırma

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Yapılandırma verilerini kullanarak yapılandırmasından kendisini bir DSC yapılandırmasında kullanılan veri ayırmak yararlı olabilir.
Bunu yaparak, birden çok ortamlar için tek bir yapılandırmayı kullanabilirsiniz.

Örneğin, bir uygulama geliştiriyorsanız, geliştirme ve üretim ortamları için bir yapılandırma kullanın ve yapılandırma verilerini her ortam için verileri belirtmek için kullanın.

## <a name="what-is-configuration-data"></a>Yapılandırma verilerini nedir?

Yapılandırma verileri, bir karma tablosunda tanımlı ve bu yapılandırma derlediğinizde DSC yapılandırması için geçirilen verilerdir.

Ayrıntılı bir açıklaması için **ConfigurationData** hashtable, bkz: [yapılandırma verilerini kullanarak](configData.md).

## <a name="a-simple-example"></a>Basit bir örnek

Bunun nasıl çalıştığını görmek için çok basit bir örneğe bakalım.
Sağlar tek bir yapılandırma oluşturacağız **IIS** bazı düğümler, üzerinde mevcut olduğunu ve **Hyper-V** bazılarında mevcuttur:

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

Bu komut dosyasının son satırında geçirme yapılandırmanın derler `$MyData` değeri olarak **ConfigurationData** parametresi.

İki MOF dosyaları oluşturduğunuz oluşur:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` her biri kendi iki farklı düğümleri belirtir `NodeName` ve `Role`. Yapılandırma dinamik olarak oluşturur **düğümü** alır gelen düğümler topluluğunu alarak blokları `$MyData` (özellikle `$AllNodes`) ve o koleksiyonu karşı filtreler `Role` özelliği...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Geliştirme ve üretim ortamlarını tanımlamak için yapılandırma verileri kullanma

Bir Web sitesi geliştirme ve üretim ortamlarını ayarlama tek bir yapılandırması kullanan tam bir örneğe bakalım. Geliştirme ortamında, IIS ve SQL Server tek düğümlerine yüklenir. Üretim ortamında, IIS ve SQL Server ayrı düğümlerine yüklenir. İki farklı ortamlar için verileri belirtmek için bir yapılandırma verileri .psd1 dosyası kullanacağız.

 ### <a name="configuration-data-file"></a>Yapılandırma veri dosyası

Geliştirme ve üretim ortamı veri adındaki bir dosyada tanımlarız `DevProdEnvData.psd1` gibi:

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

Şimdi, yapılandırmada, tanımlanmış bir `.ps1` dosyasında, biz filtre biz tanımlanan düğümleri `DevProdEnvData.psd1` rolleri tarafından (`MSSQL`, `Dev`, veya her ikisini de) ve uygun biçimde yapılandırın.
Üretim ortamında bunları iki farklı düğümlerde sahipken geliştirme ortamı SQL Server ve IIS bir düğümde vardır.
Site içeriği belirtildiği gibi farklı de `SiteContents` özellikleri.

Yapılandırma komut dosyası sonunda diyoruz yapılandırma (bir MOF belgeye, geçirme derlemeniz) `DevProdEnvData.psd1` olarak `$ConfigurationData` parametresi.

>**Not:** modülleri için bu yapılandırma gereklidir `xSqlPs` ve `xWebAdministration` hedef düğümde yüklü.

Şimdi adındaki bir dosyada gereken yapılandırmayı tanımlayan `MyWebApp.ps1`:

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

Bu yapılandırma çalıştırdığınızda, üç MOF dosyaları oluşturulur (her adlı giriş **AllNodes** array):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Düğümü olmayan verileri kullanma

Ek anahtarları ekleyebilirsiniz **ConfigurationData** hashtable bir düğüme özgü olmayan veriler için.
Aşağıdaki yapılandırma iki Web sitesi varlığını sağlar.
Her Web sitesi için veri tanımlanmış **AllNodes** dizi.
Dosya `Config.xml` Biz bu ada sahip bir ek anahtar tanımlamak için her iki Web siteleri için kullanılan `NonNodeData`.
İstediğiniz istediğiniz ve herhangi bir şey ad kadar ek anahtarlar sahip olduğunu unutmayın.
`NonNodeData` ayrılmış bir sözcük değil yalnızca ne ek anahtarı adlandırın karar değil.

Özel değişkeni kullanarak bir ek anahtar erişim **$ConfigurationData**.
Bu örnekte, `ConfigFileContents` içeren satırı erişilir:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 içinde `File` kaynak bloğu.


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
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
- [Yapılandırma verileri kullanma](configData.md)
- [Yapılandırma verilerini seçeneklerinde kimlik bilgileri](configDataCredentials.md)
- [DSC yapılandırmaları](configurations.md)
