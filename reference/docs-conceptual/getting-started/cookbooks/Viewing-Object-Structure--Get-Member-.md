---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Görüntüleme nesne yapısı Get üyesi"
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: 618f34bca7bfb76ce5d48ada642a687e279c8aad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2017
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="09ec6-103">Nesne yapısını (Get-üye) görüntüleme</span><span class="sxs-lookup"><span data-stu-id="09ec6-103">Viewing Object Structure (Get-Member)</span></span>
<span data-ttu-id="09ec6-104">Nesneleri Windows PowerShell'de merkezi bir rol oynar çünkü rasgele nesne türleri ile çalışmak üzere tasarlanmış birçok yerel komutlar vardır.</span><span class="sxs-lookup"><span data-stu-id="09ec6-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="09ec6-105">En önemlisi olan **Get-üye** komutu.</span><span class="sxs-lookup"><span data-stu-id="09ec6-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="09ec6-106">Bu komutun çıktısı kanal için bir komut verir nesnelerini çözümlemek için basit tekniği olan **Get-üye** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="09ec6-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="09ec6-107">**Get-üye** cmdlet'i gösterilmektedir, size, nesne türünün resmi adı ve üyeleri tam bir listesi.</span><span class="sxs-lookup"><span data-stu-id="09ec6-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="09ec6-108">Döndürülen öğe sayısını bazen zorlamayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="09ec6-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="09ec6-109">Örneğin, bir işlem nesnesi 100'den üyelere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="09ec6-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="09ec6-110">Tümünü görmek için işlem nesnesi ve sayfanın çıkış tüm üyelerini görmek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="09ec6-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="09ec6-111">Bu komutun çıktısı aşağıdakine benzer görünecektir:</span><span class="sxs-lookup"><span data-stu-id="09ec6-111">The output from this command will look something like this:</span></span>

```
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

<span data-ttu-id="09ec6-112">İçin görmeyi istiyoruz öğeleri filtreleyerek Biz bu uzun bilgi listesi daha kullanışlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ec6-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="09ec6-113">**Get-üye** komut özellikleri yalnızca üyelerin listesi olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="09ec6-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="09ec6-114">Birkaç forms özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="09ec6-114">There are several forms of properties.</span></span> <span data-ttu-id="09ec6-115">Biz ayarlarsanız cmdlet herhangi bir türde özelliklerini görüntüler **Get-üye MemberType** parametre değerine **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="09ec6-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="09ec6-116">Sonuç listesi çok uzun, ancak biraz daha kolay yönetilebilir hala şöyledir:</span><span class="sxs-lookup"><span data-stu-id="09ec6-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="09ec6-117">İzin verilen MemberType AliasProperty, CodeProperty, özelliği, NoteProperty, ScriptProperty, özellikler, PropertySet, yöntem, CodeMethod, ScriptMethod, yöntemleri, ParameterizedProperty, MemberSet ve tüm değerleri.</span><span class="sxs-lookup"><span data-stu-id="09ec6-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="09ec6-118">Bir işlem için 60 özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="09ec6-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="09ec6-119">Windows PowerShell genellikle iyi bilinen bir nesne için özellikler sayıda, bunların tümünün gösteren gösterilir neden Yönetilemeyen bir miktar bilgiye üretir.</span><span class="sxs-lookup"><span data-stu-id="09ec6-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="09ec6-120">Windows PowerShell biten adlara sahip XML dosyalarında depolanan bilgileri kullanarak bir nesne türü görüntülemek nasıl belirler. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="09ec6-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="09ec6-121">.NET System.Diagnostics.Process nesne olduğundan, işlem nesneleri biçimlendirme verilerini DotNetTypes.format.ps1xml içinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="09ec6-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="09ec6-122">Varsayılan olarak Windows PowerShell görüntüleyen olanlar dışındaki özellikleri bakmak gerekiyorsa, çıktı verilerini kendiniz biçimlendirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="09ec6-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="09ec6-123">Bu biçim cmdlet'leri kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="09ec6-123">This can be done by using the format cmdlets.</span></span>

