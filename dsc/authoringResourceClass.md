---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: PowerShell sınıfları içeren özel bir DSC kaynağı yazma
ms.openlocfilehash: 23669a6db17855e8d69aa0144c541bb4c799a9eb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="9c47a-103">PowerShell sınıfları içeren özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="9c47a-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="9c47a-104">İçin geçerlidir: Windows Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9c47a-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="9c47a-105">Windows PowerShell 5.0 PowerShell sınıflarda başlanmasıyla, bir sınıf oluşturarak şimdi DSC kaynağı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c47a-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="9c47a-106">Bu yüzden ayrı bir MOF dosyası oluşturmaya gerek sınıfı hem şema hem de kaynak uyarlamasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9c47a-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="9c47a-107">Sınıf tabanlı bir kaynak klasör yapısını de daha basit, çünkü bir **DSCResources** klasörü gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="9c47a-108">Sınıf tabanlı DSC kaynağı ' bir şema, özellik türü belirtmek özniteliklerle değiştirilebilir sınıfının özelliklerine olarak tanımlanır...</span><span class="sxs-lookup"><span data-stu-id="9c47a-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="9c47a-109">Kaynak tarafından uygulanan **Get()**, **Set()**, ve **Test()** yöntemleri (eşdeğer **Get-TargetResource**, **Kümesi TargetResource**, ve **Test TargetResource** bir komut dosyası kaynağı işlevlerde.</span><span class="sxs-lookup"><span data-stu-id="9c47a-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="9c47a-110">Bu konuda, basit bir kaynağı oluşturacağız **FileResource** belirtilen yolda bir dosya yönetir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="9c47a-111">DSC kaynakları hakkında daha fazla bilgi için bkz: [yapı özel Windows PowerShell istenen durum yapılandırma kaynağı](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="9c47a-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="9c47a-112">**Not:** genel koleksiyonlar sınıf tabanlı kaynaklara desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9c47a-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="9c47a-113">Bir sınıf kaynak için klasör yapısı</span><span class="sxs-lookup"><span data-stu-id="9c47a-113">Folder structure for a class resource</span></span>

<span data-ttu-id="9c47a-114">PowerShell sınıfı ile özel bir DSC kaynağı uygulamak için aşağıdaki klasör yapısını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c47a-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="9c47a-115">Sınıf tanımlanan **MyDscResource.psm1** ve modül bildirimi tanımlanan **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="9c47a-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="9c47a-116">Sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c47a-116">Create the class</span></span>

<span data-ttu-id="9c47a-117">Class anahtar sözcüğü bir PowerShell sınıfı oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c47a-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="9c47a-118">Bir sınıf bir DSC kaynağı olduğunu belirtmek için kullanın **DscResource()** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9c47a-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="9c47a-119">Sınıfın adını DSC kaynağı adıdır.</span><span class="sxs-lookup"><span data-stu-id="9c47a-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="9c47a-120">Özellikleri bildirme</span><span class="sxs-lookup"><span data-stu-id="9c47a-120">Declare properties</span></span>

<span data-ttu-id="9c47a-121">DSC kaynağı şeması sınıfının özelliklerine tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9c47a-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="9c47a-122">Şu üç özellik aşağıdaki gibi bildirin.</span><span class="sxs-lookup"><span data-stu-id="9c47a-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="9c47a-123">Özellikler öznitelikleri tarafından değiştirildiğinde dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9c47a-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="9c47a-124">Öznitelikleri anlamını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9c47a-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="9c47a-125">**DscProperty(Key)**: gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="9c47a-126">Özelliği bir anahtardır.</span><span class="sxs-lookup"><span data-stu-id="9c47a-126">The property is a key.</span></span> <span data-ttu-id="9c47a-127">Tüm özellik değerlerini anahtarları kaynak örnek bir yapılandırma içinde benzersiz şekilde tanımlamak için birleştirmeniz gerekir olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="9c47a-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="9c47a-128">**DscProperty(Mandatory)**: gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="9c47a-129">**DscProperty(NotConfigurable)**: özelliği salt okunur durumdadır.</span><span class="sxs-lookup"><span data-stu-id="9c47a-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="9c47a-130">Bu özniteliği ile işaretlenmiş özellikleri yapılandırma tarafından ayarlanamaz, ancak tarafından doldurulur **Get()** yöntemi varsa.</span><span class="sxs-lookup"><span data-stu-id="9c47a-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="9c47a-131">**DscProperty()**: özellik yapılandırılabilir, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="9c47a-132">**$Path** ve **$SourcePath** özellikleri her iki dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="9c47a-133">**$CreationTime** olan bir [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) özelliği.</span><span class="sxs-lookup"><span data-stu-id="9c47a-133">The **$CreationTime** is a [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) property.</span></span> <span data-ttu-id="9c47a-134">**$Ensure** şu şekilde tanımlanan bir numaralandırma türü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="9c47a-135">Yöntemler uygulama</span><span class="sxs-lookup"><span data-stu-id="9c47a-135">Implementing the methods</span></span>

<span data-ttu-id="9c47a-136">**Get()**, **Set()**, ve **Test()** yöntemleri benzer **Get-TargetResource**, **kümesi TargetResource** , ve **Test TargetResource** bir komut dosyası kaynağı işlevlerde.</span><span class="sxs-lookup"><span data-stu-id="9c47a-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="9c47a-137">Bu kod ayrıca CopyFile() işlevi, dosyadan kopyalar yardımcı bir işlev içerir **$SourcePath** için **$Path**.</span><span class="sxs-lookup"><span data-stu-id="9c47a-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="9c47a-138">Tam dosya</span><span class="sxs-lookup"><span data-stu-id="9c47a-138">The complete file</span></span>
<span data-ttu-id="9c47a-139">Tüm sınıf dosya izler.</span><span class="sxs-lookup"><span data-stu-id="9c47a-139">The complete class file follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## <a name="create-a-manifest"></a><span data-ttu-id="9c47a-140">Bir bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c47a-140">Create a manifest</span></span>

<span data-ttu-id="9c47a-141">Bir sınıf tabanlı kaynak DSC altyapısı kullanılabilir hale getirmek için içermelidir bir **DscResourcesToExport** deyimi bildirim dosyasındaki kaynak verilecek modül bildirir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="9c47a-142">Bizim bildirimi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="9c47a-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="9c47a-143">Kaynak test</span><span class="sxs-lookup"><span data-stu-id="9c47a-143">Test the resource</span></span>

<span data-ttu-id="9c47a-144">Sınıf ve bildirim dosyaları daha önce açıklandığı gibi Klasör yapısındaki kaydedildikten sonra yeni kaynak kullanan bir yapılandırması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c47a-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="9c47a-145">DSC yapılandırması çalıştırma hakkında daha fazla bilgi için bkz: [yapılandırmaları ederek ilerlemesini kabul ederek](enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="9c47a-145">For information about how to run a DSC configuration, see [Enacting configurations](enactingConfigurations.md).</span></span> <span data-ttu-id="9c47a-146">Aşağıdaki yapılandırma denetleyeceği olup olmadığını dosyasını `c:\test\test.txt` var ve aksi durumda, dosyadan kopyalar `c:\test.txt` (oluşturmanız gerekir `c:\test.txt` yapılandırma çalıştırmadan önce).</span><span class="sxs-lookup"><span data-stu-id="9c47a-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="9c47a-147">PsDscRunAsCredential destekleme</span><span class="sxs-lookup"><span data-stu-id="9c47a-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="9c47a-148">**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="9c47a-149">**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak bloğu.</span><span class="sxs-lookup"><span data-stu-id="9c47a-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="9c47a-150">Daha fazla bilgi için bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="9c47a-150">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="9c47a-151">Gerektiren veya PsDscRunAsCredential, kaynak için izin verme</span><span class="sxs-lookup"><span data-stu-id="9c47a-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="9c47a-152">**DscResource()** özniteliği isteğe bağlı bir parametre alır **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="9c47a-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="9c47a-153">Bu parametre üç değerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="9c47a-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="9c47a-154">`Optional` **PsDscRunAsCredential** bu kaynak çağrısına yapılandırmaları için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9c47a-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="9c47a-155">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-155">This is the default value.</span></span>
- <span data-ttu-id="9c47a-156">`Mandatory` **PsDscRunAsCredential** bu kaynak çağıran herhangi bir yapılandırma için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c47a-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="9c47a-157">`NotSupported` Bu kaynak çağrısına yapılandırmaları kullanamaz **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="9c47a-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="9c47a-158">`Default` Aynı `Optional`.</span><span class="sxs-lookup"><span data-stu-id="9c47a-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="9c47a-159">Örneğin, özel kaynak kullanımını desteklemez belirtmek için aşağıdaki öznitelik kullanın **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="9c47a-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="9c47a-160">Access kullanıcı bağlamı</span><span class="sxs-lookup"><span data-stu-id="9c47a-160">Access the user context</span></span>

<span data-ttu-id="9c47a-161">Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişkeni kullanabilirsiniz `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="9c47a-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="9c47a-162">Örneğin aşağıdaki kodu kaynak ayrıntılı çıktı akışına çalıştırıldığı kullanıcı bağlamı yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="9c47a-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="9c47a-163">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9c47a-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="9c47a-164">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="9c47a-164">Concepts</span></span>
[<span data-ttu-id="9c47a-165">Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c47a-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)