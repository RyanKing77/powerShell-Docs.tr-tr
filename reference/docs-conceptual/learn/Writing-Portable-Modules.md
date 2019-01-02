---
ms.date: 12/14/2018
keywords: PowerShell cmdlet'i
title: Taşınabilir modülleri yazma
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747730"
---
# <a name="portable-modules"></a><span data-ttu-id="06dd2-103">Taşınabilir modülleri</span><span class="sxs-lookup"><span data-stu-id="06dd2-103">Portable Modules</span></span>

<span data-ttu-id="06dd2-104">Windows PowerShell için yazılmış [.NET Framework][] için PowerShell Core yazılırken [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="06dd2-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="06dd2-105">Windows PowerShell ve PowerShell Core çalışma modülleri taşınabilir modüllerdir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="06dd2-106">.NET Framework ve .NET Core son derece uyumlu olsa da, kullanılabilir API'lerden ikisi arasındaki farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="06dd2-107">Ayrıca API farklılıkları Windows PowerShell ve PowerShell Core kullanılabilen vardır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="06dd2-108">Modüller hem ortamlarında kullanılmak üzere bu farklılıkları farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="06dd2-109">Varolan bir modülle taşıma</span><span class="sxs-lookup"><span data-stu-id="06dd2-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="06dd2-110">Bir PSSnapIn taşıma</span><span class="sxs-lookup"><span data-stu-id="06dd2-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="06dd2-111">PowerShell Core PowerShell ek bileşenleri (PSSnapIn) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="06dd2-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="06dd2-112">Ancak, bir PSSnapIn bir PowerShell modülüne Dönüştür Önemsiz değildir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="06dd2-113">Genellikle, bir sınıfın türetildiği tek kaynak dosyadaki PSSnapIn kayıt kodu [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="06dd2-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="06dd2-114">Bu kaynak dosyası derlemeden kaldırın; artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="06dd2-115">Kullanım [yeni ModuleManifest][] PSSnapIn kayıt kodu gereksinimini yerini alan yeni bir modül bildirimi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="06dd2-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="06dd2-116">(Örneğin, açıklama) PSSnapIn değerlerinden bazılarını yeniden modül bildirimi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="06dd2-117">`RootModule` Cmdlet'leri uygulayan derleme (dll) adına modül bildirimindeki özelliği ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="06dd2-118">.NET Portability Analyzer (diğer adıyla APIPort)</span><span class="sxs-lookup"><span data-stu-id="06dd2-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="06dd2-119">Bağlantı noktası modüllerine başlayın PowerShell Core ile iş Windows PowerShell için yazılan [.NET Portability Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="06dd2-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="06dd2-120">.NET modülde kullanılan API'ler, .NET Framework, .NET Core ve diğer .NET çalışma zamanları ile uyumlu olup olmadığını belirlemek için derlenmiş bütünleştirilmiş kodunuzda bu aracı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06dd2-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="06dd2-121">Varsa, araç diğer API'ler önerir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="06dd2-122">Aksi takdirde, eklemeniz gerekebilir [çalışma zamanı denetimleri][] ve kısıtlama özellikleri özel çalışma zamanları içinde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="06dd2-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="06dd2-123">Yeni modül oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="06dd2-123">Creating a New Module</span></span>

<span data-ttu-id="06dd2-124">Yeni modül oluşturuluyorsa, zamanlayıcısının [.NET CLI][].</span><span class="sxs-lookup"><span data-stu-id="06dd2-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="06dd2-125">Standart PowerShell modülü şablonu yükleme</span><span class="sxs-lookup"><span data-stu-id="06dd2-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="06dd2-126">.NET CLI'yı yükledikten sonra basit bir PowerShell modülü oluşturmak için bir şablon Kitaplığı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="06dd2-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="06dd2-127">Modülü, Windows PowerShell, PowerShell Core, Windows, Linux ve macOS ile uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="06dd2-128">Aşağıdaki örnekte, şablon yükleneceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="06dd2-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="06dd2-129">Yeni Modül projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="06dd2-129">Creating a New Module Project</span></span>

<span data-ttu-id="06dd2-130">Şablon yüklendikten sonra bu şablonu kullanarak yeni bir PowerShell modülü projesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06dd2-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="06dd2-131">Bu örnekte, örnek modülü, 'myModule' adı verilir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="06dd2-132">Modülü oluşturma</span><span class="sxs-lookup"><span data-stu-id="06dd2-132">Building the Module</span></span>

<span data-ttu-id="06dd2-133">Projeyi oluşturmak için standart .NET CLI komutlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="06dd2-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="06dd2-134">Modül test etme</span><span class="sxs-lookup"><span data-stu-id="06dd2-134">Testing the Module</span></span>

<span data-ttu-id="06dd2-135">Modül oluşturduktan sonra içe aktarın ve örnek cmdlet'ini yürütün.</span><span class="sxs-lookup"><span data-stu-id="06dd2-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="06dd2-136">Aşağıdaki bölümlerde bu şablon tarafından kullanılan teknolojilerden bazıları ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="06dd2-137">.NET standard kitaplığı</span><span class="sxs-lookup"><span data-stu-id="06dd2-137">.NET Standard Library</span></span>

<span data-ttu-id="06dd2-138">[.NET standard][] bir resmi belirtimi .NET API'leri, tüm .NET uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="06dd2-139">Yönetilen kod hedefleyen .NET Standard'ın bu sürümü ile uyumlu olan .NET Framework ve .NET Core sürümleri ile .NET Standard çalışır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="06dd2-140">Bir API .NET Standard sürümünde mevcut olmasına karşın, .NET Core API uygulamasında oluşturabilecek bir `PlatformNotSupportedException` çalışma zamanında, bu nedenle Windows PowerShell ve PowerShell Core ile uyumluluğunu doğrulamak için en iyi modülünüzde hem ortamlarında testleri çalıştırmak için uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="06dd2-141">Ayrıca, modül platformlar arası olması amaçlanıyorsa testleri Linux ve macOS üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06dd2-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="06dd2-142">.NET Standard hedefleme, modül geliştikçe uyumsuz API'leri yanlışlıkla modüle tanışın yoksa, garanti eder.</span><span class="sxs-lookup"><span data-stu-id="06dd2-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="06dd2-143">Uyumsuzluk çalışma zamanı yerine derleme zamanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="06dd2-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="06dd2-144">Bununla birlikte, uyumlu API'leri kullandığınız sürece hedeflenecek .NET Windows PowerShell ve PowerShell Core ile çalışmak için standart bir modül için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="06dd2-145">Ara dil (IL) iki çalışma zamanları arasında uyumludur.</span><span class="sxs-lookup"><span data-stu-id="06dd2-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="06dd2-146">.NET Framework 4.6.1, .NET Standard 2.0 ile uyumlu olduğu hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06dd2-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="06dd2-147">.NET Standard 2.0 dışında API'leri kullanmıyorsanız, modülünüzün yeniden derleme PowerShell Core 6 ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="06dd2-148">PowerShell standart kitaplığı</span><span class="sxs-lookup"><span data-stu-id="06dd2-148">PowerShell Standard Library</span></span>

<span data-ttu-id="06dd2-149">[PowerShell standart][] kitaplıktır PowerShell API'lerini tüm sürümlerde kullanılabilir PowerShell, standart sürümüne eşit veya daha büyük bir resmi belirtimi.</span><span class="sxs-lookup"><span data-stu-id="06dd2-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="06dd2-150">Örneğin, [PowerShell Standard 5.1][] uyumlu Windows PowerShell 5.1 hem PowerShell Core 6.0 veya daha yeni.</span><span class="sxs-lookup"><span data-stu-id="06dd2-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="06dd2-151">PowerShell standart kitaplığı kullanarak modülünüzde derleme öneririz.</span><span class="sxs-lookup"><span data-stu-id="06dd2-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="06dd2-152">Kitaplık kullanılabilir ve uygulanan hem Windows PowerShell hem de PowerShell Core 6 API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="06dd2-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="06dd2-153">PowerShell standart her zaman ileten uyumlu olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="06dd2-154">Standart kitaplık 5.1 PowerShell kullanılarak oluşturulan bir modül, her zaman gelecekteki PowerShell sürümleriyle uyumlu olur.</span><span class="sxs-lookup"><span data-stu-id="06dd2-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="06dd2-155">Modül bildirimi</span><span class="sxs-lookup"><span data-stu-id="06dd2-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="06dd2-156">Windows PowerShell ve PowerShell Core belirten uyumluluk</span><span class="sxs-lookup"><span data-stu-id="06dd2-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="06dd2-157">Modülünüzün Windows PowerShell ve PowerShell Core ile çalıştığını doğruladıktan sonra modül bildirimini açıkça uyumluluk kullanarak belirtmelidir [CompatiblePSEditions][] özelliği.</span><span class="sxs-lookup"><span data-stu-id="06dd2-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="06dd2-158">Değerini `Desktop` modülü değerini sırasında Windows PowerShell ile uyumlu olduğu anlamına gelir `Core` modülü PowerShell Core ile uyumlu olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="06dd2-159">Her ikisi de dahil olmak üzere `Desktop` ve `Core` modülü Windows PowerShell ve PowerShell Core ile uyumlu olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="06dd2-160">`Core` otomatik olarak modül Windows, Linux ve macOS ile uyumlu olduğunu gelmez.</span><span class="sxs-lookup"><span data-stu-id="06dd2-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="06dd2-161">**CompatiblePSEditions** özelliği PowerShell V5'e çıkarılmıştır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="06dd2-162">Modül bildirimleri kullanan **CompatiblePSEditions** özelliği başarısız PowerShell v5'dan önceki sürümlerde yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="06dd2-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="06dd2-163">İşletim sistemi uyumluluğu belirten</span><span class="sxs-lookup"><span data-stu-id="06dd2-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="06dd2-164">İlk olarak, modülünüzün Linux ve macOS üzerinde çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="06dd2-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="06dd2-165">Ardından, bu işletim sistemlerine modül bildirimindeki uyumluluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="06dd2-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="06dd2-166">Bu sayede, işletim sistemi için yayımlandığında modülünüzde bulmak kullanıcılar için daha kolay [PowerShell Galerisi][].</span><span class="sxs-lookup"><span data-stu-id="06dd2-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="06dd2-167">Modül bildirimini içinde `PrivateData` özelliğine sahip bir `PSData` alt özellik.</span><span class="sxs-lookup"><span data-stu-id="06dd2-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="06dd2-168">İsteğe bağlı `Tags` özelliği `PSData` PowerShell galerisinde görünen değerlerin dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="06dd2-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="06dd2-169">PowerShell Galerisi aşağıdaki uyumluluk değerlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="06dd2-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="06dd2-170">Tag</span><span class="sxs-lookup"><span data-stu-id="06dd2-170">Tag</span></span>               | <span data-ttu-id="06dd2-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06dd2-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="06dd2-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="06dd2-172">PSEdition_Core</span></span>    | <span data-ttu-id="06dd2-173">PowerShell Core 6 ile uyumlu</span><span class="sxs-lookup"><span data-stu-id="06dd2-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="06dd2-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="06dd2-174">PSEdition_Desktop</span></span> | <span data-ttu-id="06dd2-175">Windows PowerShell ile uyumlu</span><span class="sxs-lookup"><span data-stu-id="06dd2-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="06dd2-176">Windows</span><span class="sxs-lookup"><span data-stu-id="06dd2-176">Windows</span></span>           | <span data-ttu-id="06dd2-177">Windows ile uyumlu</span><span class="sxs-lookup"><span data-stu-id="06dd2-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="06dd2-178">Linux</span><span class="sxs-lookup"><span data-stu-id="06dd2-178">Linux</span></span>             | <span data-ttu-id="06dd2-179">Linux (belirli distro yok) ile uyumlu</span><span class="sxs-lookup"><span data-stu-id="06dd2-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="06dd2-180">macOS</span><span class="sxs-lookup"><span data-stu-id="06dd2-180">macOS</span></span>             | <span data-ttu-id="06dd2-181">MacOS ile uyumlu</span><span class="sxs-lookup"><span data-stu-id="06dd2-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="06dd2-182">Örnek:</span><span class="sxs-lookup"><span data-stu-id="06dd2-182">Example:</span></span>

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
[.NET Framework]: /dotnet/framework/
[.NET core]: /dotnet/core/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[Yeni ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[çalışma zamanı denetimleri]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET standard]: /dotnet/standard/net-standard
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell standart]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Galerisi]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
