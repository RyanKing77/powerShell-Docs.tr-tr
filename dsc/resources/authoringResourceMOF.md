---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MOF ile özel bir DSC kaynağı yazma
ms.openlocfilehash: 2dcdeb49b50e23bc8b9d87293ebb8d8ec5e7b57d
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405692"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>MOF ile özel bir DSC kaynağı yazma

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Bu konu başlığında, biz Windows PowerShell Desired State Configuration (DSC) özel bir kaynak için şema MOF dosyasında tanımlayın ve bir Windows PowerShell komut dosyası kaynak uygulayın. Bu özel kaynak oluşturma ve web sitenizi bulundurma içindir.

## <a name="creating-the-mof-schema"></a>MOF şeması oluşturma

Şemanın bir DSC yapılandırma betiği tarafından yapılandırılabilir, kaynak özelliklerini tanımlar.

### <a name="folder-structure-for-a-mof-resource"></a>MOF kaynak klasör yapısı

DSC özel kaynak MOF şemasıyla uygulamak için aşağıdaki klasör yapısını oluşturun. MOF şeması Demo_IISWebsite.schema.mof dosyasında tanımlanır ve kaynak betiği Demo_IISWebsite.psm1 içinde tanımlanır. İsteğe bağlı olarak, bir modül bildirimi (psd1) dosyası oluşturabilirsiniz.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Not DSCResources adlı en üst düzey klasör altında bir klasör oluşturmak için gerekli olduğunu ve her bir kaynak klasör kaynak adıyla aynı olmalıdır.

### <a name="the-contents-of-the-mof-file"></a>MOF dosyasının içeriği

Özel Web sitesi kaynağı için kullanılan bir örnek MOF dosyası aşağıda verilmiştir. Bu örneği takip etmek için bu şema bir dosyaya kaydedin ve dosyayı çağrı *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Önceki kod hakkında aşağıdakileri unutmayın:

* `FriendlyName` DSC yapılandırma betiklerini özel bu kaynakta başvurmak için kullanabileceğiniz adını tanımlar. Bu örnekte, `Website` kolay adı eşdeğerdir `Archive` yerleşik Archive kaynağı için.
* Özel kaynağınızın öğesinden türetilmelidir için tanımladığınız sınıf `OMI_BaseResource`.
* Tür niteleyicisi `[Key]`, bu özellik kaynak örneğini benzersiz şekilde tanımlayacak bir özelliği belirtir. En az bir `[Key]` özelliği gereklidir.
* `[Required]` Niteleyici özelliği gerekli olduğunu gösterir (bir değer, bu kaynağı kullanan bir yapılandırma betiği belirtilmelidir).
* `[write]` Niteleyicisi özel kaynağın bir yapılandırma komut dosyası kullanırken bu özellik isteğe bağlı olduğunu gösterir. `[read]` Niteleyici bir özelliği yapılandırması tarafından ayarlanamaz ve yalnızca raporlama amacıyla olduğunu gösterir.
* `Values` altında tanımlanmış değerleri listesine özelliğine atanabilecek değerleri sınırlayan `ValueMap`. Daha fazla bilgi için [ValueMap ve değer niteleyicileri](/windows/desktop/WmiSdk/value-map).
* Bir özellik da dahil olmak üzere `Ensure` değerlerle `Present` ve `Absent` kaynağınızda yerleşik DSC kaynakları ile tutarlı bir stil sağlamak için bir yol olarak önerilir.
* Şema dosyası özel kaynağınızın şu şekilde adlandırın: `classname.schema.mof`burada `classname` izleyen tanımlayıcı `class` anahtar sözcüğü, bir şema tanımı.

### <a name="writing-the-resource-script"></a>Kaynak betiği yazma

Kaynak betiği kaynak mantığını uygular. Bu modülde adlı üç işlev içermelidir **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource**. Kaynağınız için oluşturduğunuz MOF şemada tanımlanan özellikler kümesini aynı olan bir parametre kümesi üç işlev uygulamanız gerekir. Bu belgede, bu özellikler kümesi "kaynak özellikleri." başvuruda bulunulur Adlı bir dosyada bu üç işlev Store <ResourceName>.psm1. Aşağıdaki örnekte, işlevlerin Demo_IISWebsite.psm1 adlı bir dosyada depolanır.

> **Not**: Kaynağınız üzerinde birden çok kez aynı yapılandırma betiğini çalıştırdığınızda hatasız almanız gerekir ve kaynak betiği bir kez çalışıyor olarak aynı durumda kalmalıdır. Bunu gerçekleştirmek için emin olun, **Get-TargetResource** ve **Test TargetResource** kaynak değiştirmeden işlevleri bırakın ve söz konusu çağırma **Set-TargetResource**birden çok kez aynı parametre ile bir dizideki değerleri her zaman bir kez çağırmak için eşdeğer işlev.

İçinde **Get-TargetResource** uygulama işlev, belirtilen kaynak örneğinin durumunu denetlemek için parametre olarak sağlanan anahtar kaynak özellik değerlerini kullanın. Bu işlev, anahtarları ve gerçek değerler karşılık gelen değer olarak, bu özelliklerin tüm kaynak özellikleri listeleyen bir karma tablo döndürmesi gerekir. Aşağıdaki kod örneği sağlar.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

Kaynak özellikleri yapılandırma komut dosyası için belirtilen değerlere bağlı olarak **kümesi TargetResource** aşağıdakilerden birini yapmalısınız:

* Yeni bir Web sitesi oluşturma
* Mevcut bir Web sitesini güncelleştir
* Mevcut bir Web sitesini Sil

Aşağıdaki örnek bunu göstermektedir.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Son olarak, **Test TargetResource** işlevi olarak aynı parametre gerçekleştirmeniz gereken **Get-TargetResource** ve **kümesi TargetResource**. Uygulamanızda **Test TargetResource**, anahtar parametrelerinde belirtilen kaynak örneği durumunu denetleyin. Kaynak örneği durumunu gerçek parametre kümesi içinde belirtilen değerler eşleşmiyorsa dönüş **$false**. Yoksa şunu Döndür **$true**.

Aşağıdaki kod uygulayan **Test TargetResource** işlevi.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

**Not**: Daha kolay hata ayıklama için kullanılan **Write-Verbose** önceki üç işlev uygulamanızda cmdlet'i.
>Bu cmdlet, metin ayrıntılı ileti akışa yazar.
>Varsayılan olarak, ayrıntılı ileti akışı görüntülenmez, ancak değerini değiştirerek görüntüleyebilirsiniz **$VerbosePreference** kullanarak veya değişken **ayrıntılı** DSC cmdlet parametresinde yeni =.

### <a name="creating-the-module-manifest"></a>Modül bildirimini oluşturma

Son olarak, **yeni ModuleManifest** tanımlamak için cmdlet'i bir <ResourceName>özel kaynak modülünüzde .psd1 dosyası. Bu cmdlet çağırdığınızda önceki bölümde açıklanan betiğin Modülü (.psm1) başvuru. Dahil **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource** işlevlerini dışarı aktarma listesinde. Bir örnek bildirim dosyası aşağıda verilmiştir.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential destekleme

>**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerde desteklenir.

**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](../configurations/configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak blok.
Daha fazla bilgi için [DSC çalıştıran kullanıcı kimlik bilgileriyle](../configurations/runAsUser.md).

Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişken kullanabilirsiniz `$PsDscContext`.

Örneğin aşağıdaki kod, kaynak ayrıntılı çıkış akışına çalıştırıldığı kullanıcı bağlamı yazmalısınız:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```
