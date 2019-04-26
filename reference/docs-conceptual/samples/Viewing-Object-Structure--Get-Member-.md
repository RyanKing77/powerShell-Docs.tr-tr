---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: İzleme nesnesi yapı Get üyesi
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058854"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="27829-103">Nesne yapısını (Get-Member) görüntüleme</span><span class="sxs-lookup"><span data-stu-id="27829-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="27829-104">Nesneleri merkezi bir rol Windows PowerShell'de yürütmek için rasgele nesne türleri ile çalışmak üzere tasarlanmış çeşitli yerel komutlar vardır.</span><span class="sxs-lookup"><span data-stu-id="27829-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="27829-105">En önemli bir **Get-Member** komutu.</span><span class="sxs-lookup"><span data-stu-id="27829-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="27829-106">Bir komut verir nesnelerini çözümlemek için basit için bu komutun çıkışı yönlendirmek için bir tekniktir **Get-Member** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="27829-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="27829-107">**Get-Member** cmdlet'i gösterilmektedir, nesne türünün adını ve üyelerinin tam listesi.</span><span class="sxs-lookup"><span data-stu-id="27829-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="27829-108">Döndürülen öğe sayısını bazen zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="27829-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="27829-109">Örneğin, bir işlem nesnesi, 100'den fazla üye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="27829-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="27829-110">Tümünü görmek için tüm üyelerini bir işlem nesnesi ve sayfa çıktısını görmek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="27829-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="27829-111">Bu komutun çıktısı, aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="27829-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="27829-112">Bu bilgilerin uzun listesi daha kullanışlı için görmek istediğiniz öğeleri filtreleyerek yapabiliyoruz.</span><span class="sxs-lookup"><span data-stu-id="27829-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="27829-113">**Get-Member** komut özellikleri yalnızca üyeleri Listele olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="27829-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="27829-114">Çeşitli özellikler biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="27829-114">There are several forms of properties.</span></span> <span data-ttu-id="27829-115">Ayarlarsanız cmdlet herhangi bir tür özelliklerini görüntüler **Get-Member MemberType** parametre değerine **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="27829-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="27829-116">Sonuç listesini yine de çok uzun, ancak biraz daha kolay yönetilebilir:</span><span class="sxs-lookup"><span data-stu-id="27829-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="27829-117">MemberType izin verilen değerleri AliasProperty, CodeProperty, özelliği, NoteProperty, ScriptProperty, özellikleri, PropertySet, yöntem, CodeMethod, ScriptMethod, yöntemleri, ParameterizedProperty, MemberSet ve tüm verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="27829-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="27829-118">Bir işlem için 60'tan fazla özellik yok.</span><span class="sxs-lookup"><span data-stu-id="27829-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="27829-119">Windows PowerShell genellikle yalnızca bir dizi iyi bilinen herhangi bir nesne için özellikler, bunların tümünün gösteren gösterilir nedeni yönetilemeyen büyüklükte bir bilgi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27829-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="27829-120">Windows PowerShell nasıl sonlanan adlara sahip XML dosyalarında depolanan bilgileri kullanarak bir nesne türü görüntüleneceğini belirler. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="27829-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="27829-121">.NET System.Diagnostics.Process nesneleri olan işlem nesneleri için biçimlendirme veri DotNetTypes.format.ps1xml içinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="27829-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="27829-122">Varsayılan olarak Windows PowerShell görüntüleyen dışındaki özellikleri bakmak gerekiyorsa, çıktı verilerini kendiniz biçimlendirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="27829-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="27829-123">Bu biçim cmdlet'lerini kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27829-123">This can be done by using the format cmdlets.</span></span>