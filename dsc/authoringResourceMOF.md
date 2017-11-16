---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Özel bir DSC kaynağı MOF ile yazma"
ms.openlocfilehash: 58d6ba3995d3d6dea2787cfa347e0b1386bc40af
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="ad5b5-103">Özel bir DSC kaynağı MOF ile yazma</span><span class="sxs-lookup"><span data-stu-id="ad5b5-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="ad5b5-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ad5b5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ad5b5-105">Bu konuda, biz Windows PowerShell istenen durum yapılandırması (DSC) özel bir kaynak için şemayı MOF dosyasında tanımlayın ve bir Windows PowerShell komut dosyası kaynağı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="ad5b5-106">Bu özel oluşturmak ve bir web sitesi sürdürmek için kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="ad5b5-107">MOF şema oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad5b5-107">Creating the MOF schema</span></span>

<span data-ttu-id="ad5b5-108">Şema bir DSC yapılandırma komut dosyası tarafından yapılandırılabilir, kaynağın özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="ad5b5-109">MOF kaynak için klasör yapısı</span><span class="sxs-lookup"><span data-stu-id="ad5b5-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="ad5b5-110">DSC özel kaynak MOF şemasıyla uygulamak için aşağıdaki klasör yapısını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="ad5b5-111">MOF şema Demo_IISWebsite.schema.mof dosyasında tanımlanmış ve bir kaynak betik Demo_IISWebsite.psm1 tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="ad5b5-112">İsteğe bağlı olarak, bir modül bildirimi (psd1) dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="ad5b5-113">Not DSCResources altında en üst düzey klasör adında bir klasör oluşturmak için gerekli olduğunu ve klasör için her bir kaynağın kaynak adıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="ad5b5-114">MOF dosyasının içeriği</span><span class="sxs-lookup"><span data-stu-id="ad5b5-114">The contents of the MOF file</span></span>

<span data-ttu-id="ad5b5-115">Bir özel Web sitesi kaynağı için kullanılan örnek bir MOF dosyası aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="ad5b5-116">Bu örnek izlemek için bu şemayı bir dosyaya kaydedin ve dosyayı çağrısı *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="ad5b5-117">Önceki kod hakkında aşağıdakileri unutmayın:</span><span class="sxs-lookup"><span data-stu-id="ad5b5-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="ad5b5-118">`FriendlyName`Bu özel kaynak DSC yapılandırma komut dosyalarında başvurmak için kullanabileceğiniz adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="ad5b5-119">Bu örnekte, `Website` kolay adı eşdeğerdir `Archive` yerleşik arşiv kaynak için.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="ad5b5-120">Özel kaynak öğesinden türetilmelidir için tanımladığınız sınıfı `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="ad5b5-121">Tür niteleyicisi `[Key]`, bu özellik kaynağı örneği benzersiz olarak tanımlayacak bir özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="ad5b5-122">En az bir `[Key]` özelliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="ad5b5-123">`[Required]` Niteleyicisi özelliği gerekli olduğunu gösterir (bir değer bu kaynağı kullanan tüm yapılandırma komut belirtilmelidir).</span><span class="sxs-lookup"><span data-stu-id="ad5b5-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="ad5b5-124">`[write]` Niteleyicisi özel kaynağın bir yapılandırma komut dosyası kullanırken bu özellik isteğe bağlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="ad5b5-125">`[read]` Niteleyicisi bir özelliği bir yapılandırma tarafından ayarlanamaz ve raporlama amacıyla yalnızca olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="ad5b5-126">`Values`tanımlı değerler listesi özelliğine atanmış değerleri sınırlayan `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="ad5b5-127">Daha fazla bilgi için bkz: [ValueMap ve değer niteleyicileri](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span><span class="sxs-lookup"><span data-stu-id="ad5b5-127">For more information, see [ValueMap and Value Qualifiers](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span></span>
* <span data-ttu-id="ad5b5-128">Bir özelliği de dahil olmak üzere adlı `Ensure` değerlerle `Present` ve `Absent` yerleşik DSC kaynakları ile tutarlı bir stil korumak için bir yöntem olarak, kaynak önerilir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="ad5b5-129">Aşağıdaki gibi özel kaynağınız için şema dosyası adı: `classname.schema.mof`, burada `classname` izleyen tanımlayıcısıdır `class` şema tanımı bir anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="ad5b5-130">Kaynak betik yazma</span><span class="sxs-lookup"><span data-stu-id="ad5b5-130">Writing the resource script</span></span>

<span data-ttu-id="ad5b5-131">Kaynak betik kaynak mantığını uygular.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="ad5b5-132">Bu modülde çağrılan üç işlevler içermelidir **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="ad5b5-133">Tüm üç işlevleri, kaynak için oluşturulmuş MOF şemasında tanımlanan özellikler kümesini aynıdır bir parametre kümesi almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="ad5b5-134">Bu belgede, bu özellikler kümesi için "kaynak özellikleri." adlandırılır</span><span class="sxs-lookup"><span data-stu-id="ad5b5-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="ad5b5-135">Bu üç işlevlerin bir dosyada adlı deposu <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="ad5b5-136">Aşağıdaki örnekte, işlevleri Demo_IISWebsite.psm1 adlı bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="ad5b5-137">**Not**:, aynı yapılandırma komut dosyası, kaynaktaki birden çok kez çalıştırdığınızda, hiçbir hata alması gereken ve kaynak komut dosyası bir kez çalışıyor olarak aynı durumda kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="ad5b5-138">Bunu gerçekleştirmek için emin olun, **Get-TargetResource** ve **Test TargetResource** kaynak değişmeden işlevleri bırakın ve o çağırma **Set-TargetResource**birden çok kez aynı parametre ile bir sırada değerleri her zaman bir kez çağırmak için eşdeğer işlev.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="ad5b5-139">İçinde **Get-TargetResource** uygulama işlev, belirtilen kaynak örneği durumunu denetlemek için parametre olarak sağlanan anahtar kaynak özellik değerleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="ad5b5-140">Bu işlev, anahtarlar ve karşılık gelen değerler olarak bu özelliklerin gerçek değerler olarak tüm kaynak özelliklerini listeleyen bir karma tablosu döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="ad5b5-141">Aşağıdaki kod bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-141">The following code provides an example.</span></span>

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

<span data-ttu-id="ad5b5-142">Kaynak özellikleri yapılandırma komut dosyası için belirtilen değerlere bağlı olarak **kümesi TargetResource** aşağıdakilerden birini yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ad5b5-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="ad5b5-143">Yeni bir Web sitesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad5b5-143">Create a new website</span></span>
* <span data-ttu-id="ad5b5-144">Mevcut bir Web güncelleştir</span><span class="sxs-lookup"><span data-stu-id="ad5b5-144">Update an existing website</span></span>
* <span data-ttu-id="ad5b5-145">Var olan bir Web sitesi silme</span><span class="sxs-lookup"><span data-stu-id="ad5b5-145">Delete an existing website</span></span>

<span data-ttu-id="ad5b5-146">Aşağıdaki örnekte bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-146">The following example illustrates this.</span></span>

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

<span data-ttu-id="ad5b5-147">Son olarak, **Test TargetResource** işlevi olarak aynı parametre almalıdır **Get-TargetResource** ve **kümesi TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="ad5b5-148">Uygulamanızda **Test TargetResource**, anahtar parametrelerinde belirtilen kaynak örneği durumunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="ad5b5-149">Kaynak örneği gerçek durumunu parametre kümesi belirtilen değerler eşleşmiyorsa, dönüş **$false**.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="ad5b5-150">Aksi takdirde, dönüş **$true**.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="ad5b5-151">Aşağıdaki kod uygulayan **Test TargetResource** işlevi.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-151">The following code implements the **Test-TargetResource** function.</span></span>

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

<span data-ttu-id="ad5b5-152">**Not**: daha kolay hata ayıklama için kullanmak **Write-Verbose** cmdlet uygulamanızda önceki üç işlev.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span> 
><span data-ttu-id="ad5b5-153">Bu cmdlet, ayrıntılı ileti akışı metin yazar.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-153">This cmdlet writes text to the verbose message stream.</span></span> 
><span data-ttu-id="ad5b5-154">Varsayılan olarak, ayrıntılı ileti akışı görüntülenmez, ancak değerini değiştirerek görüntüleyebilirsiniz **$VerbosePreference** değişken veya kullanarak **ayrıntılı** DSC cmdlet parametresinde = yeni.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="ad5b5-155">Modül bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad5b5-155">Creating the module manifest</span></span>

<span data-ttu-id="ad5b5-156">Son olarak, **yeni ModuleManifest** tanımlamak için cmdlet bir <ResourceName>, özel kaynak modül için .psd1 dosya.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="ad5b5-157">Bu cmdlet çağırdığınızda, önceki bölümde açıklanan betiği Modülü (.psm1) başvuru.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="ad5b5-158">Dahil **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource** işlevleri dışarı aktarma listesinde.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="ad5b5-159">Bildirim dosyası örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="ad5b5-160">PsDscRunAsCredential destekleme</span><span class="sxs-lookup"><span data-stu-id="ad5b5-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="ad5b5-161">**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="ad5b5-162">**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak bloğu.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="ad5b5-163">Daha fazla bilgi için bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="ad5b5-163">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="ad5b5-164">Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişkeni kullanabilirsiniz `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="ad5b5-165">Örneğin aşağıdaki kodu kaynak ayrıntılı çıktı akışına çalıştırıldığı kullanıcı bağlamı yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="ad5b5-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```




