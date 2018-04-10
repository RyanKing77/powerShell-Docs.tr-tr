---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 9065315ef39129e6a28234d972fe350fd5e7e11d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Bir JEA Uç Noktası Oluşturma ve Buna Bağlanma
JEA uç noktası oluşturmak için oluşturmanız ve ile oluşturulan bir özel olarak yapılandırılmış PowerShell oturumu yapılandırma dosyasını kaydetmek için gereken **yeni PSSessionConfigurationFile** cmdlet'i.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Bu şuna benzer bir oturum yapılandırma dosyası oluşturacak:
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

}
```
JEA uç noktası oluştururken, aşağıdaki parametreleri komutu (ve karşılık gelen anahtarları dosyasındaki) ayarlamanız gerekir:
1.  RestrictedRemoteServer SessionType
2.  İçin RunAsVirtualAccount **$true**
3.  "Kama" dökümleri sonra her bir oturumu kaydedileceği dizinine TranscriptPath
4.  Hangi grupların tanımlayan bir hashtable için RoleDefinitions erişimi hangi "rolü yeteneklerine."  Bu alan tanımlar **kimin** yapabilirsiniz **ne** Bu uç noktada.   Rol özellikleri, kısa süre içinde açıklanacaktır özel dosyalardır.


Hangi grupların hangi rolü özellikleri erişebildiği RoleDefinitions alanı tanımlar.  Bir rol özelliği kullanıcıları bağlamak için bir dizi sunulur özelliği tanımlayan bir dosyadır.  Rol özellikleri ile oluşturabileceğiniz **yeni PSRoleCapabilityFile** komutu.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Bu şuna benzeyen bir şablon rol özelliği oluşturur:
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}

```
JEA oturum yapılandırması tarafından kullanılmak üzere rol özellikleri "RoleCapabilities" adlı bir dizinde geçerli bir PowerShell modülü kaydedilmesi gerekir. Bir modül, isterseniz birden çok Rol Yetenek dosya olabilir.

Hangi cmdlet'ler, İşlevler, diğer adlar ve kullanıcı JEA oturumuna bağlanırken erişebilir betikleri yapılandırmaya başlamak için kendi kurallarınızı açıklamalı şablonları aşağıdaki Rol Yetenek dosyasına ekleyin. Rol özellikleri nasıl yapılandırabileceğiniz içine daha derin görünüm için tam denetleyin [Kılavuzu deneyimi](http://aka.ms/JEA).

Son olarak, oturum yapılandırması ve ilgili rol özellikleri özelleştirme tamamladıktan sonra bu oturum yapılandırmasını kaydetmek ve çalıştırarak uç noktası oluşturma **Register-PSSessionConfiguration**.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>JEA uç noktasına bağlanın
JEA uç noktasına bağlanmak için diğer bir PowerShell uç nokta works bağlanma aynı şekilde çalışır.  Yalnızca "ConfigurationName" parametresi olarak JEA uç nokta adınız vermeniz gerekir **New-PSSession**, **Invoke-Command**, veya **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
JEA oturumuna bağlandığında komutları Güvenilenler listesine erişiminiz rol özellikleri çalışan için sınırlı olacaktır. Rolü için izin verilmiyor komutu çalıştırmayı denerseniz, hatayla karşılaşır.