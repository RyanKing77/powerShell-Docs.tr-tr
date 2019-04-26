---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne Sıralama
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086060"
---
# <a name="sorting-objects"></a><span data-ttu-id="d0680-103">Nesne Sıralama</span><span class="sxs-lookup"><span data-stu-id="d0680-103">Sorting Objects</span></span>

<span data-ttu-id="d0680-104">Biz barkodları taramanızı daha kolay hale getirmek için görüntülenen verileri düzenleyebilirsiniz `Sort-Object` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d0680-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="d0680-105">`Sort-Object` Sıralanacak bir veya daha fazla özellik adını alır ve bu özelliklerin değerlerine göre sıralanmış verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0680-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="d0680-106">Temel sıralama</span><span class="sxs-lookup"><span data-stu-id="d0680-106">Basic sorting</span></span>

<span data-ttu-id="d0680-107">Alt dizinleri ve dosyaları geçerli dizin listeleme sorununu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d0680-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="d0680-108">Sıralamada kullanmak istiyorsanız **LastWriteTime** göre ve ardından **adı**, biz yazarak bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0680-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

<span data-ttu-id="d0680-109">Belirterek nesneleri ters sırada sıralayabilirsiniz **azalan** parametresi geçin.</span><span class="sxs-lookup"><span data-stu-id="d0680-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a><span data-ttu-id="d0680-110">Karma tabloları kullanma</span><span class="sxs-lookup"><span data-stu-id="d0680-110">Using hash tables</span></span>

<span data-ttu-id="d0680-111">Bir dizi içinde karma tabloları kullanarak farklı özellikleri farklı siparişleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0680-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="d0680-112">Her karma tablo kullanan bir **ifade** özellik adını bir dize olarak belirtmek için anahtarı ve bir **artan** veya **azalan** göre sıralama düzeni belirlemek için anahtar `$true` veya `$false`.</span><span class="sxs-lookup"><span data-stu-id="d0680-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="d0680-113">**İfade** anahtarı zorunludur.</span><span class="sxs-lookup"><span data-stu-id="d0680-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="d0680-114">**Artan** veya **azalan** anahtardır isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d0680-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="d0680-115">Aşağıdaki örnek, azalan nesneleri sıralar **LastWriteTime** sırası ve artan **adı** sırası.</span><span class="sxs-lookup"><span data-stu-id="d0680-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

<span data-ttu-id="d0680-116">De bir scriptblock ayarlayabilirsiniz **ifade** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="d0680-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="d0680-117">Çalıştırırken `Sort-Object` cmdlet'ini scriptblock yürütülür ve sonuçları sıralamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0680-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="d0680-118">Aşağıdaki örnek nesneleri arasındaki zaman aralığı göre azalan düzende sıralar **CreationTime** ve **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="d0680-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a><span data-ttu-id="d0680-119">İpuçları</span><span class="sxs-lookup"><span data-stu-id="d0680-119">Tips</span></span>

<span data-ttu-id="d0680-120">Atlayabilirsiniz **özelliği** parametre adı şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="d0680-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="d0680-121">Yanında, başvurabilirsiniz `Sort-Object` yerleşik diğer tarafından `sort`:</span><span class="sxs-lookup"><span data-stu-id="d0680-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="d0680-122">Karma tabloları içindeki anahtarları sıralamak için aşağıdaki gibi kısaltılmış:</span><span class="sxs-lookup"><span data-stu-id="d0680-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="d0680-123">Bu örnekte, **e** anlamına gelen **ifade**, **d** anlamına gelen **azalan**ve **bir** anlamına gelen **artan**.</span><span class="sxs-lookup"><span data-stu-id="d0680-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="d0680-124">Okunabilirliği artırmak için karma tablo ayrı bir değişken içine koyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0680-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```