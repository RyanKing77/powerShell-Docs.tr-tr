---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: "Bulma komut dosyası"
ms.openlocfilehash: 15bf23b803250c7893fe970c2580592ea7c0a4b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="find-script"></a>Bulma komut dosyası

Belirtilen ölçütlerle eşleşen PowerShell komut dosyalarını bir çevrimiçi galeriden bulur.

## <a name="description"></a>Açıklama

Bulma komut dosyası belirtilen ölçütlerle eşleşen kayıtlı depoları komut dosyalarından bulur.
Bulunan her komut dosyası için bulma komut dosyası, isteğe bağlı olarak yöneltilen PSRepositoryItemInfo nesnesi yükleme komut dosyası için komut dosyalarını yüklemek için döndürür.
Bulma komut dosyası cmdlet'i, farklı arama ölçütleri ad, etiket, filtre, komutu ad, sürüm aralığı, tam sürümünü, bağımlılıklarını dahil olmak üzere tüm sürümleri gibi ve belirli veya tüm kayıtlı depoları ile komut dosyaları bulmak için olanak tanır.

- Bulma komut dosyası için komut dosyasına dayalı filtre içeriği komutuyla ve - parametrelerini içerir.
- Bulma komut dosyası sürümü parametrelerle filtre uygulayabilirsiniz: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Bu parametreler MinmimumVersion ve MaximumVersion dışında birbirini dışlar.
  - Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek betiği adıyla izin verilir.
  - RequiredVersion parametresi belirtilmezse, bulma komut dosyası hiçbir en düşük sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya komut dosyası en son sürümünü betik en son sürümünü döndürür. 
  - RequiredVersion parametresi belirtilirse, bulma komut dosyası, yalnızca belirtilen sürümü ile tam olarak bir komut dosyası sürümünü döndürür.
- Bulma komut dosyası, komut dosyası meta filtreleyebilir - etiketi parametresine sahip.
- Bulma komut dosyası deposu özgü arama dili filtreleyebilir - filtre parametresine sahip.
- Bulma komut dosyası komut dosyalarının tümü veya bir kayıtlı depoları çok filtre uygulayabilirsiniz.

**Not:** kayıtlı PSRepository geçerli ScriptSourceLocation sahip olmalıdır. Set-PSRepository ScriptSourceLocation değerini ayarlamak için kullanabilirsiniz.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Bulma komut dosyası](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a>Örnek komutlar

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```

