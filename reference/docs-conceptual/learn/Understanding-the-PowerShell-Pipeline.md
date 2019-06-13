---
ms.date: 08/23/2018
keywords: PowerShell cmdlet'i
title: PowerShell işlem hatları anlama
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030384"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="2bf14-103">Anlama işlem hatları</span><span class="sxs-lookup"><span data-stu-id="2bf14-103">Understanding pipelines</span></span>

<span data-ttu-id="2bf14-104">İşlem hatları kanal bağlı parçalarını bir dizi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="2bf14-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="2bf14-105">İşlem hattı taşıyarak öğeleri her bir kesim geçirin.</span><span class="sxs-lookup"><span data-stu-id="2bf14-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="2bf14-106">PowerShell'de bir işlem hattı oluşturmak için yöneltme işleci birlikte komutların Bağlan "|".</span><span class="sxs-lookup"><span data-stu-id="2bf14-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="2bf14-107">Her komutun çıkışı, sonraki komut için giriş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bf14-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="2bf14-108">İşlem hatları için kullanılan gösterim diğer Kabukları içinde kullanılan gösterim benzer.</span><span class="sxs-lookup"><span data-stu-id="2bf14-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="2bf14-109">İlk bakışta, işlem hatlarını nasıl PowerShell'de farklı belirgin olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2bf14-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="2bf14-110">Metin ekranda gördüğünüz olsa da, PowerShell komutları arasında değil metin nesneleri geçirir.</span><span class="sxs-lookup"><span data-stu-id="2bf14-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="2bf14-111">PowerShell işlem hattını</span><span class="sxs-lookup"><span data-stu-id="2bf14-111">The PowerShell pipeline</span></span>

<span data-ttu-id="2bf14-112">İşlem hatları tartışmaya komut satırı arabirimi içinde kullanılan en değerli kavram olarak oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="2bf14-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="2bf14-113">Düzgün kullanıldığında, işlem hatları karmaşık komutlarını kullanarak çabayı azaltmak ve komutlar için iş akışını görmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2bf14-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="2bf14-114">Her komut bir işlem hattı (işlem hattı öğesi olarak adlandırılır), ardışık düzende sonraki komuta çıktısını geçirir. öğe tarafından.</span><span class="sxs-lookup"><span data-stu-id="2bf14-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="2bf14-115">Komutlar, aynı anda birden fazla öğe işlemek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bf14-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="2bf14-116">Daha az kaynak tüketimi ve çıkış hemen başlama başlamak olanağı sonucudur.</span><span class="sxs-lookup"><span data-stu-id="2bf14-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="2bf14-117">Örneğin, kullanırsanız `Out-Host` çıkış sayfa sayfa görünümünü yalnızca başka bir komuttan çıkış görünüyor zorlamak için cmdlet'i sayfalarına parçalanmış ekranda görüntülenen normal metin ister:</span><span class="sxs-lookup"><span data-stu-id="2bf14-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="2bf14-118">Ayrıca disk belleği azaltır CPU kullanımı için işleme aktardığından `Out-Host` tam bir sayfa görüntüleme hazır olduğunda cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="2bf14-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="2bf14-119">Çıktı, sonraki sayfaya kullanılabilir hale gelene kadar yürütme işlem hattında önünde cmdlet'ler duraklatın.</span><span class="sxs-lookup"><span data-stu-id="2bf14-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="2bf14-120">Aşağıdaki komutları karşılaştırarak yöneltme CPU ve bellek kullanımı Windows Görev Yöneticisi'nde nasıl etkilediğini görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2bf14-120">You can see how piping impacts CPU and memory usage in the Windows Task Manager by comparing the following commands:</span></span>

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> <span data-ttu-id="2bf14-121">**Sayfalama** parametresi tüm PowerShell konaklar tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2bf14-121">The **Paging** parameter is not supported by all PowerShell hosts.</span></span> <span data-ttu-id="2bf14-122">Örneğin, çalıştığınızda kullanılacak **sayfalama** parametresi PowerShell ISE'de aşağıdaki hatayı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="2bf14-122">For example, when you try to use the **Paging** parameter in the PowerShell ISE, you see the following error:</span></span>
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="2bf14-123">İşlem hattı nesneleri</span><span class="sxs-lookup"><span data-stu-id="2bf14-123">Objects in the pipeline</span></span>

<span data-ttu-id="2bf14-124">PowerShell'de bir cmdlet çalıştırdığınızda, konsol penceresindeki metin olarak nesneleri temsil etmek gerekli olduğundan, metin çıktısı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="2bf14-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="2bf14-125">Metin çıktısı çıkış nesnesinin özelliklerini görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="2bf14-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="2bf14-126">Örneğin, düşünün `Get-Location` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="2bf14-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="2bf14-127">Çalıştırırsanız `Get-Location` geçerli konumunuzu C sürücüsünün kök olsa da, şu çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="2bf14-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="2bf14-128">Metin çıkışı bir özetidir bilgilerinin tarafından döndürülen nesne değil tam bir temsilini `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="2bf14-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="2bf14-129">Çıkış başlığı, ekranda görünen verileri biçimlendirir, oluşturduğunuz işlem tarafından eklenir.</span><span class="sxs-lookup"><span data-stu-id="2bf14-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="2bf14-130">Çıktı için kanal zaman `Get-Member` cmdlet'i tarafından döndürülen nesne hakkında bilgi alma `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="2bf14-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="2bf14-131">`Get-Location` döndürür bir **PATHINFO** geçerli yol ve diğer bilgileri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="2bf14-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
