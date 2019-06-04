---
ms.date: 12/14/2018
keywords: PowerShell cmdlet'i
title: Taşınabilir modülleri yazma
ms.openlocfilehash: 237f6aaea0ed019c54d04a8477d7a456edf00910
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470986"
---
# <a name="portable-modules"></a>Taşınabilir modülleri

Windows PowerShell için yazılmış [.NET Framework][] için PowerShell Core yazılırken [.NET Core][]. Windows PowerShell ve PowerShell Core çalışma modülleri taşınabilir modüllerdir. .NET Framework ve .NET Core son derece uyumlu olsa da, kullanılabilir API'lerden ikisi arasındaki farklılıklar vardır. Ayrıca API farklılıkları Windows PowerShell ve PowerShell Core kullanılabilen vardır. Modüller hem ortamlarında kullanılmak üzere bu farklılıkları farkında olmanız gerekir.

## <a name="porting-an-existing-module"></a>Varolan bir modülle taşıma

### <a name="porting-a-pssnapin"></a>Bir PSSnapIn taşıma

PowerShell [ek bileşen](/powershell/developer/cmdlet/modules-and-snap-ins) PowerShell Core desteklenmez. Ancak, bir PSSnapIn bir PowerShell modülüne Dönüştür Önemsiz değildir. Genellikle, bir sınıfın türetildiği tek kaynak dosyadaki PSSnapIn kayıt kodu [PSSnapIn][].
Bu kaynak dosyası derlemeden kaldırın; artık gerekli değildir.

Kullanım [yeni ModuleManifest][] PSSnapIn kayıt kodu gereksinimini yerini alan yeni bir modül bildirimi oluşturmak için. Değerlerden bazıları **PSSnapIn** (gibi **açıklama**) içinde modül bildirimi yeniden kullanılabilir.

**RootModule** cmdlet'leri uygulayan derleme (dll) adına modül bildirimindeki özelliği ayarlanmalıdır.

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET Portability Analyzer (diğer adıyla APIPort)

Bağlantı noktası modüllerine başlayın PowerShell Core ile iş Windows PowerShell için yazılan [.NET taşınabilirlik Çözümleyicisi][]. .NET modülde kullanılan API'ler, .NET Framework, .NET Core ve diğer .NET çalışma zamanları ile uyumlu olup olmadığını belirlemek için derlenmiş bütünleştirilmiş kodunuzda bu aracı çalıştırın. Varsa, araç diğer API'ler önerir. Aksi takdirde, eklemeniz gerekebilir [çalışma zamanı denetimleri][] ve kısıtlama özellikleri özel çalışma zamanları içinde kullanılabilir değil.

## <a name="creating-a-new-module"></a>Yeni modül oluşturuluyor

Yeni modül oluşturuluyorsa, zamanlayıcısının [.NET CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>Standart PowerShell modülü şablonu yükleme

.NET CLI'yı yükledikten sonra basit bir PowerShell modülü oluşturmak için bir şablon Kitaplığı yükleyin.
Modülü, Windows PowerShell, PowerShell Core, Windows, Linux ve macOS ile uyumlu olacaktır.

Aşağıdaki örnekte, şablon yükleneceği gösterilmektedir:

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>Yeni Modül projesi oluşturma

Şablon yüklendikten sonra bu şablonu kullanarak yeni bir PowerShell modülü projesi oluşturabilirsiniz. Bu örnekte, örnek modülü, 'myModule' adı verilir.

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>Modülü oluşturma

Projeyi oluşturmak için standart .NET CLI komutlarını kullanın.

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>Modül test etme

Modül oluşturduktan sonra içe aktarın ve örnek cmdlet'ini yürütün.

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

Aşağıdaki bölümlerde bu şablon tarafından kullanılan teknolojilerden bazıları ayrıntılı olarak açıklanmaktadır.

## <a name="net-standard-library"></a>.NET standard kitaplığı

[.NET standard][] bir resmi belirtimi .NET API'leri, tüm .NET uygulamalarında kullanılabilir. Yönetilen kod hedefleyen .NET Standard'ın bu sürümü ile uyumlu olan .NET Framework ve .NET Core sürümleri ile .NET Standard çalışır.

> [!NOTE]
> Bir API .NET Standard sürümünde mevcut olmasına karşın, .NET Core API uygulamasında oluşturabilecek bir `PlatformNotSupportedException` çalışma zamanında, bu nedenle Windows PowerShell ve PowerShell Core ile uyumluluğunu doğrulamak için en iyi modülünüzde hem ortamlarında testleri çalıştırmak için uygulamadır.
> Ayrıca, modül platformlar arası olması amaçlanıyorsa testleri Linux ve macOS üzerinde çalıştırın.

.NET Standard hedefleme, modül geliştikçe uyumsuz API'leri yanlışlıkla modüle tanışın yoksa, garanti eder. Uyumsuzluk çalışma zamanı yerine derleme zamanında bulunur.

Bununla birlikte, uyumlu API'leri kullandığınız sürece hedeflenecek .NET Windows PowerShell ve PowerShell Core ile çalışmak için standart bir modül için gerekli değildir. Ara dil (IL) iki çalışma zamanları arasında uyumludur. .NET Framework 4.6.1, .NET Standard 2.0 ile uyumlu olduğu hedefleyebilirsiniz. .NET Standard 2.0 dışında API'leri kullanmıyorsanız, modülünüzün yeniden derleme PowerShell Core 6 ile çalışır.

## <a name="powershell-standard-library"></a>PowerShell standart kitaplığı

[PowerShell standart][] kitaplıktır PowerShell API'lerini tüm sürümlerde kullanılabilir PowerShell, standart sürümüne eşit veya daha büyük bir resmi belirtimi.

Örneğin, [PowerShell standart 5.1][] uyumlu Windows PowerShell 5.1 hem PowerShell Core 6.0 veya daha yeni.

PowerShell standart kitaplığı kullanarak modülünüzde derleme öneririz. Kitaplık kullanılabilir ve uygulanan hem Windows PowerShell hem de PowerShell Core 6 API'ler sağlar.
PowerShell standart her zaman ileten uyumlu olacak şekilde tasarlanmıştır. Standart kitaplık 5.1 PowerShell kullanılarak oluşturulan bir modül, her zaman gelecekteki PowerShell sürümleriyle uyumlu olur.

## <a name="module-manifest"></a>Modül bildirimi

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Windows PowerShell ve PowerShell Core belirten uyumluluk

Modülünüzün Windows PowerShell ve PowerShell Core ile çalıştığını doğruladıktan sonra modül bildirimini açıkça uyumluluk kullanarak belirtmelidir [CompatiblePSEditions][] özelliği. Değerini `Desktop` modülü değerini sırasında Windows PowerShell ile uyumlu olduğu anlamına gelir `Core` modülü PowerShell Core ile uyumlu olduğu anlamına gelir. Her ikisi de dahil olmak üzere `Desktop` ve `Core` modülü Windows PowerShell ve PowerShell Core ile uyumlu olduğu anlamına gelir.

> [!NOTE]
> `Core` otomatik olarak modül Windows, Linux ve macOS ile uyumlu olduğunu gelmez.
> **CompatiblePSEditions** özelliği PowerShell V5'e çıkarılmıştır. Modül bildirimleri kullanan **CompatiblePSEditions** özelliği başarısız PowerShell v5'dan önceki sürümlerde yüklenemedi.

### <a name="indicating-os-compatibility"></a>İşletim sistemi uyumluluğu belirten

İlk olarak, modülünüzün Linux ve macOS üzerinde çalıştığını doğrulayın. Ardından, bu işletim sistemlerine modül bildirimindeki uyumluluğunu gösterir. Bu sayede, işletim sistemi için yayımlandığında modülünüzde bulmak kullanıcılar için daha kolay [PowerShell Galerisi][].

Modül bildirimini içinde `PrivateData` özelliğine sahip bir `PSData` alt özellik. İsteğe bağlı `Tags` özelliği `PSData` PowerShell galerisinde görünen değerlerin dizisini alır. PowerShell Galerisi aşağıdaki uyumluluk değerlerini destekler:

| Etiket               | Açıklama                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | PowerShell Core 6 ile uyumlu          |
| PSEdition_Desktop | Windows PowerShell ile uyumlu         |
| Windows           | Windows ile uyumlu                    |
| Linux             | Linux (belirli distro yok) ile uyumlu |
| Mac OS             | MacOS ile uyumlu                      |

Örnek:

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[Yeni ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Çalışma zamanı denetimleri]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell standart]: https://github.com/PowerShell/PowerShellStandard
[PowerShell standart 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Galerisi]: https://www.powershellgallery.com
[.NET taşınabilirlik Çözümleyicisi]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
