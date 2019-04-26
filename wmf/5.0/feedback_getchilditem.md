---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085309"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="eafa9-102">Get-childıtem öğesinin-Depth parametresi var</span><span class="sxs-lookup"><span data-stu-id="eafa9-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="eafa9-103">**Get-Childıtem** artık bir **– derinliği** parametresi ile kullandığınız **– Recurse** özyineleme sınırlamak için:</span><span class="sxs-lookup"><span data-stu-id="eafa9-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="eafa9-104">PS: C:\\kullanıcılar\\slee\\indirir\\örnek&gt; Get-Childıtem-Recurse - derinliği 0</span><span class="sxs-lookup"><span data-stu-id="eafa9-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="eafa9-105">Dizini: C:\\kullanıcılar\\slee\\indirir\\örneği</span><span class="sxs-lookup"><span data-stu-id="eafa9-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="eafa9-106">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="eafa9-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="eafa9-107">d---4/14/2015-17:36 Depth0</span><span class="sxs-lookup"><span data-stu-id="eafa9-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="eafa9-108">-a---14/4/2015 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="eafa9-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="eafa9-109">-a---14/4/2015 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="eafa9-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="eafa9-110">-a---14/4/2015 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="eafa9-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="eafa9-111">PS: C:\\kullanıcılar\\slee\\indirir\\örnek&gt; Get-Childıtem-Recurse - derinlik 1</span><span class="sxs-lookup"><span data-stu-id="eafa9-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="eafa9-112">Dizini: C:\\kullanıcılar\\slee\\indirir\\örneği</span><span class="sxs-lookup"><span data-stu-id="eafa9-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="eafa9-113">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="eafa9-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="eafa9-114">d---4/14/2015-17:36 Depth0</span><span class="sxs-lookup"><span data-stu-id="eafa9-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="eafa9-115">-a---14/4/2015 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="eafa9-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="eafa9-116">-a---14/4/2015 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="eafa9-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="eafa9-117">-a---14/4/2015 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="eafa9-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="eafa9-118">Dizini: C:\\kullanıcılar\\slee\\indirir\\örnek\\Depth0</span><span class="sxs-lookup"><span data-stu-id="eafa9-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="eafa9-119">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="eafa9-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="eafa9-120">d---4/14/2015-17:33 Depth1</span><span class="sxs-lookup"><span data-stu-id="eafa9-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
