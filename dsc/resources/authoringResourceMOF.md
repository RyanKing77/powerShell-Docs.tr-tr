---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MOF ile özel bir DSC kaynağı yazma
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059737"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="f1b16-103">MOF ile özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="f1b16-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="f1b16-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f1b16-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f1b16-105">Bu konu başlığında, biz Windows PowerShell Desired State Configuration (DSC) özel bir kaynak için şema MOF dosyasında tanımlayın ve bir Windows PowerShell komut dosyası kaynak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f1b16-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="f1b16-106">Bu özel kaynak oluşturma ve web sitenizi bulundurma içindir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="f1b16-107">MOF şeması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1b16-107">Creating the MOF schema</span></span>

<span data-ttu-id="f1b16-108">Şemanın bir DSC yapılandırma betiği tarafından yapılandırılabilir, kaynak özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f1b16-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="f1b16-109">MOF kaynak klasör yapısı</span><span class="sxs-lookup"><span data-stu-id="f1b16-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="f1b16-110">DSC özel kaynak MOF şemasıyla uygulamak için aşağıdaki klasör yapısını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f1b16-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="f1b16-111">MOF şeması Demo_IISWebsite.schema.mof dosyasında tanımlanır ve kaynak betiği Demo_IISWebsite.psm1 içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f1b16-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="f1b16-112">İsteğe bağlı olarak, bir modül bildirimi (psd1) dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1b16-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="f1b16-113">Not DSCResources adlı en üst düzey klasör altında bir klasör oluşturmak için gerekli olduğunu ve her bir kaynak klasör kaynak adıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1b16-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="f1b16-114">MOF dosyasının içeriği</span><span class="sxs-lookup"><span data-stu-id="f1b16-114">The contents of the MOF file</span></span>

<span data-ttu-id="f1b16-115">Özel Web sitesi kaynağı için kullanılan bir örnek MOF dosyası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="f1b16-116">Bu örneği takip etmek için bu şema bir dosyaya kaydedin ve dosyayı çağrı *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="f1b16-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="f1b16-117">Önceki kod hakkında aşağıdakileri unutmayın:</span><span class="sxs-lookup"><span data-stu-id="f1b16-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="f1b16-118">`FriendlyName` DSC yapılandırma betiklerini özel bu kaynakta başvurmak için kullanabileceğiniz adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f1b16-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="f1b16-119">Bu örnekte, `Website` kolay adı eşdeğerdir `Archive` yerleşik Archive kaynağı için.</span><span class="sxs-lookup"><span data-stu-id="f1b16-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="f1b16-120">Özel kaynağınızın öğesinden türetilmelidir için tanımladığınız sınıf `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="f1b16-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="f1b16-121">Tür niteleyicisi `[Key]`, bu özellik kaynak örneğini benzersiz şekilde tanımlayacak bir özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="f1b16-122">En az bir `[Key]` özelliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="f1b16-123">`[Required]` Niteleyici özelliği gerekli olduğunu gösterir (bir değer, bu kaynağı kullanan bir yapılandırma betiği belirtilmelidir).</span><span class="sxs-lookup"><span data-stu-id="f1b16-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="f1b16-124">`[write]` Niteleyicisi özel kaynağın bir yapılandırma komut dosyası kullanırken bu özellik isteğe bağlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="f1b16-125">`[read]` Niteleyici bir özelliği yapılandırması tarafından ayarlanamaz ve yalnızca raporlama amacıyla olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="f1b16-126">`Values` altında tanımlanmış değerleri listesine özelliğine atanabilecek değerleri sınırlayan `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="f1b16-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="f1b16-127">Daha fazla bilgi için [ValueMap ve değer niteleyicileri](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="f1b16-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="f1b16-128">Bir özellik da dahil olmak üzere `Ensure` değerlerle `Present` ve `Absent` kaynağınızda yerleşik DSC kaynakları ile tutarlı bir stil sağlamak için bir yol olarak önerilir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="f1b16-129">Şema dosyası özel kaynağınızın şu şekilde adlandırın: `classname.schema.mof`burada `classname` izleyen tanımlayıcı `class` anahtar sözcüğü, bir şema tanımı.</span><span class="sxs-lookup"><span data-stu-id="f1b16-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="f1b16-130">Kaynak betiği yazma</span><span class="sxs-lookup"><span data-stu-id="f1b16-130">Writing the resource script</span></span>

<span data-ttu-id="f1b16-131">Kaynak betiği kaynak mantığını uygular.</span><span class="sxs-lookup"><span data-stu-id="f1b16-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="f1b16-132">Bu modülde adlı üç işlev içermelidir **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="f1b16-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="f1b16-133">Kaynağınız için oluşturduğunuz MOF şemada tanımlanan özellikler kümesini aynı olan bir parametre kümesi üç işlev uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="f1b16-134">Bu belgede, bu özellikler kümesi "kaynak özellikleri." başvuruda bulunulur</span><span class="sxs-lookup"><span data-stu-id="f1b16-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="f1b16-135">Adlı bir dosyada bu üç işlev Store <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="f1b16-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="f1b16-136">Aşağıdaki örnekte, işlevlerin Demo_IISWebsite.psm1 adlı bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="f1b16-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> [!NOTE]
> <span data-ttu-id="f1b16-137">Kaynağınız üzerinde birden çok kez aynı yapılandırma betiğini çalıştırdığınızda hatasız almanız gerekir ve kaynak betiği bir kez çalışıyor olarak aynı durumda kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1b16-137">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="f1b16-138">Bunu gerçekleştirmek için emin olun, **Get-TargetResource** ve **Test TargetResource** kaynak değiştirmeden işlevleri bırakın ve söz konusu çağırma **Set-TargetResource**birden çok kez aynı parametre ile bir dizideki değerleri her zaman bir kez çağırmak için eşdeğer işlev.</span><span class="sxs-lookup"><span data-stu-id="f1b16-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="f1b16-139">İçinde **Get-TargetResource** uygulama işlev, belirtilen kaynak örneğinin durumunu denetlemek için parametre olarak sağlanan anahtar kaynak özellik değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1b16-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="f1b16-140">Bu işlev, anahtarları ve gerçek değerler karşılık gelen değer olarak, bu özelliklerin tüm kaynak özellikleri listeleyen bir karma tablo döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="f1b16-141">Aşağıdaki kod örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1b16-141">The following code provides an example.</span></span>

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

<span data-ttu-id="f1b16-142">Kaynak özellikleri yapılandırma komut dosyası için belirtilen değerlere bağlı olarak **kümesi TargetResource** aşağıdakilerden birini yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="f1b16-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="f1b16-143">Yeni bir Web sitesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1b16-143">Create a new website</span></span>
* <span data-ttu-id="f1b16-144">Mevcut bir Web sitesini güncelleştir</span><span class="sxs-lookup"><span data-stu-id="f1b16-144">Update an existing website</span></span>
* <span data-ttu-id="f1b16-145">Mevcut bir Web sitesini Sil</span><span class="sxs-lookup"><span data-stu-id="f1b16-145">Delete an existing website</span></span>

<span data-ttu-id="f1b16-146">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-146">The following example illustrates this.</span></span>

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

<span data-ttu-id="f1b16-147">Son olarak, **Test TargetResource** işlevi olarak aynı parametre gerçekleştirmeniz gereken **Get-TargetResource** ve **kümesi TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="f1b16-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="f1b16-148">Uygulamanızda **Test TargetResource**, anahtar parametrelerinde belirtilen kaynak örneği durumunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f1b16-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="f1b16-149">Kaynak örneği durumunu gerçek parametre kümesi içinde belirtilen değerler eşleşmiyorsa dönüş **$false**.</span><span class="sxs-lookup"><span data-stu-id="f1b16-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="f1b16-150">Yoksa şunu Döndür **$true**.</span><span class="sxs-lookup"><span data-stu-id="f1b16-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="f1b16-151">Aşağıdaki kod uygulayan **Test TargetResource** işlevi.</span><span class="sxs-lookup"><span data-stu-id="f1b16-151">The following code implements the **Test-TargetResource** function.</span></span>

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

<span data-ttu-id="f1b16-152">**Not**: Daha kolay hata ayıklama için kullanılan **Write-Verbose** önceki üç işlev uygulamanızda cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="f1b16-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="f1b16-153">Bu cmdlet, metin ayrıntılı ileti akışa yazar.</span><span class="sxs-lookup"><span data-stu-id="f1b16-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="f1b16-154">Varsayılan olarak, ayrıntılı ileti akışı görüntülenmez, ancak değerini değiştirerek görüntüleyebilirsiniz **$VerbosePreference** kullanarak veya değişken **ayrıntılı** DSC cmdlet parametresinde yeni =.</span><span class="sxs-lookup"><span data-stu-id="f1b16-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="f1b16-155">Modül bildirimini oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1b16-155">Creating the module manifest</span></span>

<span data-ttu-id="f1b16-156">Son olarak, **yeni ModuleManifest** tanımlamak için cmdlet'i bir <ResourceName>özel kaynak modülünüzde .psd1 dosyası.</span><span class="sxs-lookup"><span data-stu-id="f1b16-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="f1b16-157">Bu cmdlet çağırdığınızda önceki bölümde açıklanan betiğin Modülü (.psm1) başvuru.</span><span class="sxs-lookup"><span data-stu-id="f1b16-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="f1b16-158">Dahil **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource** işlevlerini dışarı aktarma listesinde.</span><span class="sxs-lookup"><span data-stu-id="f1b16-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="f1b16-159">Bir örnek bildirim dosyası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="f1b16-160">PsDscRunAsCredential destekleme</span><span class="sxs-lookup"><span data-stu-id="f1b16-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="f1b16-161">**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="f1b16-162">**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](../configurations/configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak blok.</span><span class="sxs-lookup"><span data-stu-id="f1b16-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="f1b16-163">Daha fazla bilgi için [DSC çalıştıran kullanıcı kimlik bilgileriyle](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="f1b16-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="f1b16-164">Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişken kullanabilirsiniz `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="f1b16-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="f1b16-165">Örneğin aşağıdaki kod, kaynak ayrıntılı çıkış akışına çalıştırıldığı kullanıcı bağlamı yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="f1b16-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="f1b16-166">Düğümü yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="f1b16-166">Rebooting the Node</span></span>

<span data-ttu-id="f1b16-167">Gerçekleştirilen eylemleri, `Set-TargetResource` işlevi yeniden başlatma gerektiren, Genel Bayrak düğümü yeniden başlatma için LCM'yi bildirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1b16-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="f1b16-168">Metodundan hemen sonra bu yeniden başlatma gerçekleşir `Set-TargetResource` işlevi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f1b16-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="f1b16-169">İçinde `Set-TargetResource` işlev, aşağıdaki kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f1b16-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="f1b16-170">Düğümü yeniden başlatma için LCM'yi sırayla **RebootNodeIfNeeded** bayrağının ayarlanması gerekiyor `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1b16-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="f1b16-171">**ActionAfterReboot** ayarı da ayarlanmalıdır **ContinueConfiguration**, varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f1b16-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="f1b16-172">LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md), veya [yerel Configuration Manager'ı (v4) yapılandırma](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="f1b16-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
