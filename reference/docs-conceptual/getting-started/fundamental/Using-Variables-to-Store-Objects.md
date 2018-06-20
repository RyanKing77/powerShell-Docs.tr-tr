---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne Depolamak için Değişkenleri Kullanma
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953336"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="72c36-103">Nesne Depolamak için Değişkenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="72c36-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="72c36-104">PowerShell nesneler ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="72c36-104">PowerShell works with objects.</span></span> <span data-ttu-id="72c36-105">PowerShell temelde daha sonra kullanmak için çıktı korumak için nesneleri, adlandırılmış değişkenleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72c36-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="72c36-106">Diğer değişkenlerle birlikte çalışmaya kullanılıyorsa Kabukları PowerShell değişkenleri nesneleri, metin değil olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="72c36-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="72c36-107">Değişkenleri her zaman belirtilen ilk karakter $ ile ve bunların adları, herhangi bir alfasayısal karakter veya alt çizgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="72c36-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="72c36-108">Bir değişken oluşturma</span><span class="sxs-lookup"><span data-stu-id="72c36-108">Creating a Variable</span></span>
<span data-ttu-id="72c36-109">Geçerli bir değişken adı yazarak bir değişken oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c36-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="72c36-110">Bu sonuç verir, çünkü **$loc** bir değere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="72c36-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="72c36-111">Bir değişken oluşturun ve aynı adımını bir değere atayın.</span><span class="sxs-lookup"><span data-stu-id="72c36-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="72c36-112">Henüz yoksa PowerShell yalnızca değişken oluşturur; Aksi halde, belirtilen değer var olan değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="72c36-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="72c36-113">Geçerli konumunuz değişkende saklamak için **$loc**, türü:</span><span class="sxs-lookup"><span data-stu-id="72c36-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="72c36-114">Bu komut çıktı $loc gönderdiğinden yazdığınızda görüntülenen çıkış yok</span><span class="sxs-lookup"><span data-stu-id="72c36-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="72c36-115">PowerShell'de, görüntülenen çıktının bir yan etkisi, yönlendirilmiş aksi değil, verileri her zaman ekrana gönderilir olgu ' dir.</span><span class="sxs-lookup"><span data-stu-id="72c36-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="72c36-116">$Loc yazarak geçerli konumunuz gösterir:</span><span class="sxs-lookup"><span data-stu-id="72c36-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="72c36-117">Kullanabileceğiniz **Get-üye** değişkenleri içeriği hakkında bilgileri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="72c36-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="72c36-118">Get-üyesine $loc cmdlet'ine gösterir, bunun bir **PATHINFO** nesne Get-Location çıktısı gibi:</span><span class="sxs-lookup"><span data-stu-id="72c36-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="72c36-119">Değişkenleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="72c36-119">Manipulating Variables</span></span>
<span data-ttu-id="72c36-120">PowerShell değişkenlerini için çeşitli komutlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="72c36-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="72c36-121">Tam bir listesi okunabilir bir biçimde yazarak görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c36-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="72c36-122">Geçerli PowerShell oturumunda oluşturduğunuz değişkenlerinin yanı sıra çeşitli sistem tarafından tanımlanan değişkenler vardır.</span><span class="sxs-lookup"><span data-stu-id="72c36-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="72c36-123">Kullanabileceğiniz **Kaldır-Variable** cmdlet'ini tüm değişkenlerin PowerShell tarafından denetlenmeyen temizleyin.</span><span class="sxs-lookup"><span data-stu-id="72c36-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="72c36-124">Tüm değişkenleri temizlemek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="72c36-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="72c36-125">Bu, aşağıya bakın onay istemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72c36-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="72c36-126">Ardından çalıştırırsanız **Get-Variable** cmdlet, kalan PowerShell değişkenleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="72c36-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="72c36-127">Yazarak, ayrıca PowerShell sürücüsü değişken olduğundan, tüm PowerShell değişkenleri görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c36-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="72c36-128">Cmd.exe değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="72c36-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="72c36-129">PowerShell Cmd.exe olmamasına karşın, bir komut kabuğu ortamda çalışır ve hiçbir ortamında kullanılabilir aynı değişkenleri Windows kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72c36-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="72c36-130">Bu değişkenler adlı bir sürücüsü sunulan **env**:.</span><span class="sxs-lookup"><span data-stu-id="72c36-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="72c36-131">Bu değişkenler yazarak görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c36-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="72c36-132">Standart değişken cmdlet'leri çalışmak için tasarlanmamıştır rağmen **env:** değişkenleri kullanmaya devam edebilirsiniz bunları belirterek **env:** öneki.</span><span class="sxs-lookup"><span data-stu-id="72c36-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="72c36-133">Örneğin, işletim sisteminin kök dizini görmek için komut kabuğunu kullanabilirsiniz **% SystemRoot %** yazarak PowerShell içinde değişken:</span><span class="sxs-lookup"><span data-stu-id="72c36-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="72c36-134">Ayrıca, oluşturabilir ve ortam değişkenler PowerShell değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72c36-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="72c36-135">Başka bir yerde Windows ortam değişkenleri için normal kuralları için Windows Powershell'den erişilen ortam değişkenleri uygun.</span><span class="sxs-lookup"><span data-stu-id="72c36-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>