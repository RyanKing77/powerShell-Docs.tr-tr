---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "PowerShell sınıfları içeren özel bir DSC kaynağı yazma"
ms.openlocfilehash: 53757f965c51fee699409b5a8ecda802dda9801f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>PowerShell sınıfları içeren özel bir DSC kaynağı yazma

> İçin geçerlidir: Windows Windows PowerShell 5.0

Windows PowerShell 5.0 PowerShell sınıflarda başlanmasıyla, bir sınıf oluşturarak şimdi DSC kaynağı tanımlayabilirsiniz. Bu yüzden ayrı bir MOF dosyası oluşturmaya gerek sınıfı hem şema hem de kaynak uyarlamasını tanımlar. Sınıf tabanlı bir kaynak klasör yapısını de daha basit, çünkü bir **DSCResources** klasörü gerekli değildir.

Sınıf tabanlı DSC kaynağı ' bir şema, özellik türü belirtmek özniteliklerle değiştirilebilir sınıfının özelliklerine olarak tanımlanır... Kaynak tarafından uygulanan **Get()**, **Set()**, ve **Test()** yöntemleri (eşdeğer **Get-TargetResource**, **Kümesi TargetResource**, ve **Test TargetResource** bir komut dosyası kaynağı işlevlerde.

Bu konuda, basit bir kaynağı oluşturacağız **FileResource** belirtilen yolda bir dosya yönetir.

DSC kaynakları hakkında daha fazla bilgi için bkz: [yapı özel Windows PowerShell istenen durum yapılandırma kaynağı](authoringResource.md)

>**Not:** genel koleksiyonlar sınıf tabanlı kaynaklara desteklenmiyor.

## <a name="folder-structure-for-a-class-resource"></a>Bir sınıf kaynak için klasör yapısı

PowerShell sınıfı ile özel bir DSC kaynağı uygulamak için aşağıdaki klasör yapısını oluşturun. Sınıf tanımlanan **MyDscResource.psm1** ve modül bildirimi tanımlanan **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## <a name="create-the-class"></a>Sınıf oluşturma

Class anahtar sözcüğü bir PowerShell sınıfı oluşturmak için kullanın. Bir sınıf bir DSC kaynağı olduğunu belirtmek için kullanın **DscResource()** özniteliği. Sınıfın adını DSC kaynağı adıdır.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Özellikleri bildirme

DSC kaynağı şeması sınıfının özelliklerine tanımlanır. Şu üç özellik aşağıdaki gibi bildirin.

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

Özellikler öznitelikleri tarafından değiştirildiğinde dikkat edin. Öznitelikleri anlamını aşağıdaki gibidir:

- **DscProperty(Key)**: gerekli bir özelliktir. Özelliği bir anahtardır. Tüm özellik değerlerini anahtarları kaynak örnek bir yapılandırma içinde benzersiz şekilde tanımlamak için birleştirmeniz gerekir olarak işaretlenmiş.
- **DscProperty(Mandatory)**: gerekli bir özelliktir.
- **DscProperty(NotConfigurable)**: özelliği salt okunur durumdadır. Bu özniteliği ile işaretlenmiş özellikleri yapılandırma tarafından ayarlanamaz, ancak tarafından doldurulur **Get()** yöntemi varsa.
- **DscProperty()**: özellik yapılandırılabilir, ancak gerekli değildir.

**$Path** ve **$SourcePath** özellikleri her iki dizelerdir. **$CreationTime** olan bir [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) özelliği. **$Ensure** şu şekilde tanımlanan bir numaralandırma türü bir özelliktir.

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### <a name="implementing-the-methods"></a>Yöntemler uygulama

**Get()**, **Set()**, ve **Test()** yöntemleri benzer **Get-TargetResource**, **kümesi TargetResource** , ve **Test TargetResource** bir komut dosyası kaynağı işlevlerde.

Bu kod ayrıca CopyFile() işlevi, dosyadan kopyalar yardımcı bir işlev içerir **$SourcePath** için **$Path**. 

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

### <a name="the-complete-file"></a>Tam dosya
Tüm sınıf dosya izler.

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


## <a name="create-a-manifest"></a>Bir bildirimi oluşturma

Bir sınıf tabanlı kaynak DSC altyapısı kullanılabilir hale getirmek için içermelidir bir **DscResourcesToExport** deyimi bildirim dosyasındaki kaynak verilecek modül bildirir. Bizim bildirimi şöyle görünür:

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

## <a name="test-the-resource"></a>Kaynak test

Sınıf ve bildirim dosyaları daha önce açıklandığı gibi Klasör yapısındaki kaydedildikten sonra yeni kaynak kullanan bir yapılandırması oluşturabilirsiniz. DSC yapılandırması çalıştırma hakkında daha fazla bilgi için bkz: [yapılandırmaları ederek ilerlemesini kabul ederek](enactingConfigurations.md). Aşağıdaki yapılandırma denetleyeceği olup olmadığını dosyasını `c:\test\test.txt` var ve aksi durumda, dosyadan kopyalar `c:\test.txt` (oluşturmanız gerekir `c:\test.txt` yapılandırma çalıştırmadan önce).

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

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential destekleme

>**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerinde desteklenir.

**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak bloğu.
Daha fazla bilgi için bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Gerektiren veya PsDscRunAsCredential, kaynak için izin verme

**DscResource()** özniteliği isteğe bağlı bir parametre alır **RunAsCredential**.
Bu parametre üç değerden birini alır:

- `Optional` **PsDscRunAsCredential** bu kaynak çağrısına yapılandırmaları için isteğe bağlıdır. Bu varsayılan değerdir.
- `Mandatory` **PsDscRunAsCredential** bu kaynak çağıran herhangi bir yapılandırma için kullanılması gerekir.
- `NotSupported` Bu kaynak çağrısına yapılandırmaları kullanamaz **PsDscRunAsCredential**.
- `Default` Aynı `Optional`.

Örneğin, özel kaynak kullanımını desteklemez belirtmek için aşağıdaki öznitelik kullanın **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a>Access kullanıcı bağlamı

Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişkeni kullanabilirsiniz `$global:PsDscContext`.

Örneğin aşağıdaki kodu kaynak ayrıntılı çıktı akışına çalıştırıldığı kullanıcı bağlamı yazarsınız:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Ayrıca bkz:
### <a name="concepts"></a>Kavramlar
[Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma](authoringResource.md)

