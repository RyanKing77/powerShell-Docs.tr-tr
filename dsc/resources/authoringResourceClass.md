---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: PowerShell sınıfları ile özel bir DSC kaynağı yazma
ms.openlocfilehash: 0759685b04688f574d72b62a15833832ad19e816
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405850"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>PowerShell sınıfları ile özel bir DSC kaynağı yazma

> Şunun için geçerlidir: Windows PowerShell 5.0

Windows PowerShell 5.0 PowerShell sınıflarını sunulmasıyla birlikte, bir sınıf oluşturarak artık bir DSC kaynağı tanımlayabilirsiniz. Ayrı bir MOF dosyası oluşturmanız gerekmez. Bu nedenle sınıf hem şema hem de kaynak uygulamasını tanımlar. Sınıf tabanlı bir kaynak klasör yapısını de daha basit, çünkü bir **DSCResources** klasörü gerekli değildir.

Sınıf tabanlı DSC kaynak, şema özellikleri özellik türü belirtmek için özniteliklerle değiştirilebilir sınıfı olarak tanımlanır... Kaynak tarafından uygulanan **Get()**, **Set()**, ve **Test()** yöntemleri (eşdeğer **Get-TargetResource**, **Kümesi TargetResource**, ve **Test TargetResource** betik kaynağa işlevleri.

Bu konuda, basit bir kaynağı oluşturacağız **FileResource** , belirtilen yolda bir dosya yönetir.

DSC kaynakları hakkında daha fazla bilgi için bkz. [derleme özel Windows PowerShell Desired State Configuration kaynakları](authoringResource.md)

>**Not:** Genel koleksiyonlar sınıf tabanlı kaynakları desteklenmez.

## <a name="folder-structure-for-a-class-resource"></a>Bir sınıf kaynak klasör yapısı

DSC özel kaynak PowerShell sınıfı ile uygulamak için aşağıdaki klasör yapısını oluşturun. Sınıfı içinde tanımlanan **MyDscResource.psm1** ve modül bildirimini tanımlanan **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a>Sınıf oluşturma

Class anahtar sözcüğü, bir PowerShell sınıfı oluşturmak için kullanın. DSC kaynağı bir sınıf olduğunu belirtmek için kullanın **DscResource()** özniteliği. DSC kaynak adını sınıf adıdır.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Özellikleri bildirme

DSC kaynak şema özellikleri sınıfı olarak tanımlanır. Şu üç özellik gibi bildirin.

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

Özellikleri öznitelikleri tarafından değiştirildiğini dikkat edin. Öznitelikleri anlamını aşağıdaki gibidir:

- **DscProperty(Key)**: Özelliği gereklidir. Özelliği bir anahtardır. Tüm özelliklerin değerlerini, bir kaynak örneği yapılandırması içindeki benzersiz olarak tanımlanabilmesi için anahtarları birleştirmeniz olarak işaretlendi.
- **DscProperty(Mandatory)**: Özelliği gereklidir.
- **DscProperty(NotConfigurable)**: Özellik salt okunurdur. Bu özniteliği ile işaretlenmiş özellikleri yapılandırma tarafından ayarlanamaz, ancak tarafından doldurulur **Get()** varsa yöntemi.
- **DscProperty()**: Özellik yapılandırılabilir, ancak gerekli değildir.

**$Path** ve **$SourcePath** özellikleri her iki dizelerdir. **$CreationTime** olduğu bir [DateTime](/dotnet/api/system.datetime) özelliği. **$Ensure** gibi tanımlı bir numaralandırma türü, bir özelliktir.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>Yöntem uygulama

**Get()**, **Set()**, ve **Test()** yöntemlerdir alınmak üzere **Get-TargetResource**, **TargetResource Ayarla** , ve **Test TargetResource** betik kaynağa işlevleri.

Bu kod ayrıca dosyasından kopyalayan bir yardımcı işlevini CopyFile() işlevi içerir **$SourcePath** için **$Path**.

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
Tam sınıf dosyası izler.

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

Bir sınıf tabanlı kaynak DSC altyapısı kullanılabilir hale getirmek için içermelidir bir **DscResourcesToExport** deyimi bildirimi dosyasındaki kaynak dışarı aktarılacak modülü bildirir. Bizim bildiriminin şöyle görünür:

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

## <a name="test-the-resource"></a>Test kaynağı

Sınıf ve bildirim dosyaları daha önce açıklandığı gibi klasör yapısında kaydettikten sonra yeni kaynak kullanan yapılandırması oluşturabilirsiniz. DSC yapılandırması çalıştırma hakkında daha fazla bilgi için bkz: [yapılandırmaları kabul etme](../pull-server/enactingConfigurations.md). Aşağıdaki yapılandırmayı denetleyeceği olmadığını dosyasını `c:\test\test.txt` var ve aksi durumda, dosyayı kopyalar `c:\test.txt` (oluşturmanız gerekir `c:\test.txt` yapılandırma çalıştırmadan önce).

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

>**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerde desteklenir.

**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](../configurations/configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak blok.
Daha fazla bilgi için [DSC çalıştıran kullanıcı kimlik bilgileriyle](../configurations/runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Gerektiren veya PsDscRunAsCredential kaynağınız için izin verme

**DscResource()** özniteliği isteğe bağlı bir parametre alır **RunAsCredential**.
Bu parametre üç değerden birini alır:

- `Optional` **PsDscRunAsCredential** bu kaynak çağrısı yapılandırmalar için isteğe bağlıdır. Bu varsayılan değerdir.
- `Mandatory` **PsDscRunAsCredential** bu kaynak çağıran herhangi bir yapılandırma için kullanılmalıdır.
- `NotSupported` Bu kaynak çağrısı yapılandırmaları kullanamaz **PsDscRunAsCredential**.
- `Default` Aynı `Optional`.

Örneğin, özel kaynağınızın kullanarak desteklemiyor belirtin için aşağıdaki öznitelik kullanın **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a>Erişim kullanıcı bağlamı

Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişken kullanabilirsiniz `$global:PsDscContext`.

Örneğin aşağıdaki kod, kaynak ayrıntılı çıkış akışına çalıştırıldığı kullanıcı bağlamı yazmalısınız:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Ayrıca bkz:
### <a name="concepts"></a>Kavramlar
[Derleme özel Windows PowerShell Desired State Configuration kaynakları](authoringResource.md)