---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Nesne Depolamak için Değişkenleri Kullanma
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 3168b64039a601857f9c684108de5770f88329e3
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134067"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="7779e-103">Nesneleri depolamak için değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7779e-103">Using variables to store objects</span></span>

<span data-ttu-id="7779e-104">PowerShell nesneleri ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7779e-104">PowerShell works with objects.</span></span> <span data-ttu-id="7779e-105">PowerShell değişkenleri olarak bilinen adlandırılmış nesneleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7779e-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="7779e-106">Değişken adları alt çizgi karakteri can herhangi bir alfasayısal karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7779e-106">Variables names can include the underscore character can any alphanumeric characters.</span></span> <span data-ttu-id="7779e-107">PowerShell'de kullanıldığında, bir değişkeni her zaman kullanarak belirtilen \$ karakteri ve ardından tarafından değişken adı.</span><span class="sxs-lookup"><span data-stu-id="7779e-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="7779e-108">Bir değişken oluşturma</span><span class="sxs-lookup"><span data-stu-id="7779e-108">Creating a variable</span></span>

<span data-ttu-id="7779e-109">Geçerli bir değişken adı yazarak bir değişken oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7779e-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="7779e-110">Bu örnekte sonuç verir, çünkü `$loc` bir değere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7779e-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="7779e-111">Bir değişken oluşturun ve aynı adımda bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="7779e-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="7779e-112">PowerShell, yoksa yalnızca değişkeni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7779e-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="7779e-113">Aksi takdirde, belirtilen değer var olan değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="7779e-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="7779e-114">Aşağıdaki örnek geçerli konumu değişkeninde depolar. `$loc`:</span><span class="sxs-lookup"><span data-stu-id="7779e-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="7779e-115">Bu komut yazarken PowerShell hiçbir çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7779e-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="7779e-116">PowerShell için 'Get-konum' çıktısını gönderir `$loc`.</span><span class="sxs-lookup"><span data-stu-id="7779e-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="7779e-117">PowerShell'de, atanan veya yeniden yönlendirilen değil veri ekranına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="7779e-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="7779e-118">Yazarak `$loc` geçerli konumunuzu gösterir:</span><span class="sxs-lookup"><span data-stu-id="7779e-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="7779e-119">Kullanabileceğiniz `Get-Member` değişkenlerin içeriğini hakkındaki bilgileri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="7779e-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="7779e-120">`Get-Member` gösteren `$loc` olduğu bir **PATHINFO** çıktısı gibi bir nesne `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="7779e-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="7779e-121">Değişkenleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="7779e-121">Manipulating variables</span></span>

<span data-ttu-id="7779e-122">PowerShell değişkenlerini için çeşitli komutlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7779e-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="7779e-123">Okunabilir bir biçimde yapılandırılabilip yazarak görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7779e-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="7779e-124">PowerShell, ayrıca çeşitli sistem tarafından tanımlanan değişkenler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7779e-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="7779e-125">Kullanabileceğiniz `Remove-Variable` PowerShell tarafından denetlenmez, değişkenleri, geçerli oturumdan kaldırmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7779e-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="7779e-126">Tüm değişkenleri temizlemek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="7779e-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="7779e-127">Önceki komutu çalıştırdıktan sonra `Get-Variable` cmdlet'i, PowerShell sistem değişkenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7779e-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="7779e-128">PowerShell, ayrıca bir değişken sürücü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7779e-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="7779e-129">Değişken sürücü kullanarak tüm PowerShell değişkenlerini görüntülemek için aşağıdaki örneği kullanın:</span><span class="sxs-lookup"><span data-stu-id="7779e-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="7779e-130">Cmd.exe değişkenlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="7779e-130">Using Cmd.exe variables</span></span>

<span data-ttu-id="7779e-131">PowerShell, Windows işlemi Cmd.exe dahil olmak üzere tüm kullanılabilir aynı ortam değişkenlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7779e-131">PowerShell can use the same environment variables available to any Windows process, including Cmd.exe.</span></span> <span data-ttu-id="7779e-132">Bu değişkenler adlı bir sürücüsü sunulan `env:`.</span><span class="sxs-lookup"><span data-stu-id="7779e-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="7779e-133">Bu değişkenler, aşağıdaki komutu yazarak görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7779e-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="7779e-134">Standart `*-Variable` cmdlet'leri olmayan ortam değişkenleri ile çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7779e-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="7779e-135">Ortam değişkenlerini kullanarak erişilen `env:` sürücü öneki.</span><span class="sxs-lookup"><span data-stu-id="7779e-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="7779e-136">Örneğin, **% SystemRoot %** Cmd.exe değişkeninde işletim sisteminin kök dizin adı içerir.</span><span class="sxs-lookup"><span data-stu-id="7779e-136">For example, the **%SystemRoot%** variable in Cmd.exe contains the operating system's root directory name.</span></span> <span data-ttu-id="7779e-137">PowerShell'de, kullandığınız `$env:SystemRoot` aynı değere erişmek için.</span><span class="sxs-lookup"><span data-stu-id="7779e-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="7779e-138">Ayrıca, oluşturabilir ve PowerShell içinde ortam değişkenlerinden değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7779e-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="7779e-139">PowerShell ortam değişkenlerinde başka bir yerde işletim sisteminde kullanılan ortam değişkenleri için bu kuralların izleyin.</span><span class="sxs-lookup"><span data-stu-id="7779e-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="7779e-140">Aşağıdaki örnek, yeni bir ortam değişkeni oluşturur:</span><span class="sxs-lookup"><span data-stu-id="7779e-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="7779e-141">Zorunlu olmasa da, tüm büyük harfleri kullanılacak ortam değişken adları için ortak olan.</span><span class="sxs-lookup"><span data-stu-id="7779e-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>