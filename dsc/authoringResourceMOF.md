---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Özel bir DSC kaynağı MOF ile yazma
ms.openlocfilehash: 4e336e837d2153fecab8325cb8714ffed85a6175
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Özel bir DSC kaynağı MOF ile yazma

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Bu konuda, biz Windows PowerShell istenen durum yapılandırması (DSC) özel bir kaynak için şemayı MOF dosyasında tanımlayın ve bir Windows PowerShell komut dosyası kaynağı uygulayın. Bu özel oluşturmak ve bir web sitesi sürdürmek için kaynaktır.

## <a name="creating-the-mof-schema"></a>MOF şema oluşturma

Şema bir DSC yapılandırma komut dosyası tarafından yapılandırılabilir, kaynağın özelliklerini tanımlar.

### <a name="folder-structure-for-a-mof-resource"></a>MOF kaynak için klasör yapısı

DSC özel kaynak MOF şemasıyla uygulamak için aşağıdaki klasör yapısını oluşturun. MOF şema Demo_IISWebsite.schema.mof dosyasında tanımlanmış ve bir kaynak betik Demo_IISWebsite.psm1 tanımlanır. İsteğe bağlı olarak, bir modül bildirimi (psd1) dosyası oluşturabilirsiniz.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Not DSCResources altında en üst düzey klasör adında bir klasör oluşturmak için gerekli olduğunu ve klasör için her bir kaynağın kaynak adıyla aynı olmalıdır.

### <a name="the-contents-of-the-mof-file"></a>MOF dosyasının içeriği

Bir özel Web sitesi kaynağı için kullanılan örnek bir MOF dosyası aşağıdadır. Bu örnek izlemek için bu şemayı bir dosyaya kaydedin ve dosyayı çağrısı *Demo_IISWebsite.schema.mof*.

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

* `FriendlyName` Bu özel kaynak DSC yapılandırma komut dosyalarında başvurmak için kullanabileceğiniz adını tanımlar. Bu örnekte, `Website` kolay adı eşdeğerdir `Archive` yerleşik arşiv kaynak için.
* Özel kaynak öğesinden türetilmelidir için tanımladığınız sınıfı `OMI_BaseResource`.
* Tür niteleyicisi `[Key]`, bu özellik kaynağı örneği benzersiz olarak tanımlayacak bir özelliği belirtir. En az bir `[Key]` özelliği gereklidir.
* `[Required]` Niteleyicisi özelliği gerekli olduğunu gösterir (bir değer bu kaynağı kullanan tüm yapılandırma komut belirtilmelidir).
* `[write]` Niteleyicisi özel kaynağın bir yapılandırma komut dosyası kullanırken bu özellik isteğe bağlı olduğunu gösterir. `[read]` Niteleyicisi bir özelliği bir yapılandırma tarafından ayarlanamaz ve raporlama amacıyla yalnızca olduğunu gösterir.
* `Values` tanımlı değerler listesi özelliğine atanmış değerleri sınırlayan `ValueMap`. Daha fazla bilgi için bkz: [ValueMap ve değer niteleyicileri](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* Bir özelliği de dahil olmak üzere adlı `Ensure` değerlerle `Present` ve `Absent` yerleşik DSC kaynakları ile tutarlı bir stil korumak için bir yöntem olarak, kaynak önerilir.
* Aşağıdaki gibi özel kaynağınız için şema dosyası adı: `classname.schema.mof`, burada `classname` izleyen tanımlayıcısıdır `class` şema tanımı bir anahtar sözcük.

### <a name="writing-the-resource-script"></a>Kaynak betik yazma

Kaynak betik kaynak mantığını uygular. Bu modülde çağrılan üç işlevler içermelidir **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource**. Tüm üç işlevleri, kaynak için oluşturulmuş MOF şemasında tanımlanan özellikler kümesini aynıdır bir parametre kümesi almanız gerekir. Bu belgede, bu özellikler kümesi için "kaynak özellikleri." adlandırılır Bu üç işlevlerin bir dosyada adlı deposu <ResourceName>.psm1. Aşağıdaki örnekte, işlevleri Demo_IISWebsite.psm1 adlı bir dosyada depolanır.

> **Not**:, aynı yapılandırma komut dosyası, kaynaktaki birden çok kez çalıştırdığınızda, hiçbir hata alması gereken ve kaynak komut dosyası bir kez çalışıyor olarak aynı durumda kalması gerekir. Bunu gerçekleştirmek için emin olun, **Get-TargetResource** ve **Test TargetResource** kaynak değişmeden işlevleri bırakın ve o çağırma **Set-TargetResource**birden çok kez aynı parametre ile bir sırada değerleri her zaman bir kez çağırmak için eşdeğer işlev.

İçinde **Get-TargetResource** uygulama işlev, belirtilen kaynak örneği durumunu denetlemek için parametre olarak sağlanan anahtar kaynak özellik değerleri kullanın. Bu işlev, anahtarlar ve karşılık gelen değerler olarak bu özelliklerin gerçek değerler olarak tüm kaynak özelliklerini listeleyen bir karma tablosu döndürmesi gerekir. Aşağıdaki kod bir örnek sağlar.

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

Kaynak özellikleri yapılandırma komut dosyası için belirtilen değerlere bağlı olarak **kümesi TargetResource** aşağıdakilerden birini yapmanız gerekir:

* Yeni bir Web sitesi oluşturma
* Mevcut bir Web güncelleştir
* Var olan bir Web sitesi silme

Aşağıdaki örnekte bu gösterilmektedir.

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

Son olarak, **Test TargetResource** işlevi olarak aynı parametre almalıdır **Get-TargetResource** ve **kümesi TargetResource**. Uygulamanızda **Test TargetResource**, anahtar parametrelerinde belirtilen kaynak örneği durumunu kontrol edin. Kaynak örneği gerçek durumunu parametre kümesi belirtilen değerler eşleşmiyorsa, dönüş **$false**. Aksi takdirde, dönüş **$true**.

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

**Not**: daha kolay hata ayıklama için kullanmak **Write-Verbose** cmdlet uygulamanızda önceki üç işlev.
>Bu cmdlet, ayrıntılı ileti akışı metin yazar.
>Varsayılan olarak, ayrıntılı ileti akışı görüntülenmez, ancak değerini değiştirerek görüntüleyebilirsiniz **$VerbosePreference** değişken veya kullanarak **ayrıntılı** DSC cmdlet parametresinde = yeni.

### <a name="creating-the-module-manifest"></a>Modül bildirimi oluşturma

Son olarak, **yeni ModuleManifest** tanımlamak için cmdlet bir <ResourceName>, özel kaynak modül için .psd1 dosya. Bu cmdlet çağırdığınızda, önceki bölümde açıklanan betiği Modülü (.psm1) başvuru. Dahil **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource** işlevleri dışarı aktarma listesinde. Bildirim dosyası örneği verilmiştir.

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

>**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerinde desteklenir.

**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak bloğu.
Daha fazla bilgi için bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).

Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişkeni kullanabilirsiniz `$PsDscContext`.

Örneğin aşağıdaki kodu kaynak ayrıntılı çıktı akışına çalıştırıldığı kullanıcı bağlamı yazarsınız:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```