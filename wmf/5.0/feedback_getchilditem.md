---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221910"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="453bc-102">-Derinliği parametresi Get-Childıtem var</span><span class="sxs-lookup"><span data-stu-id="453bc-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="453bc-103">**Get-Childıtem** artık bir **– derinliği** parametresi ile kullandığınız **– Recurse** özyineleme sınırlamak için:</span><span class="sxs-lookup"><span data-stu-id="453bc-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="453bc-104">PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 0</span><span class="sxs-lookup"><span data-stu-id="453bc-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="453bc-105">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği</span><span class="sxs-lookup"><span data-stu-id="453bc-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="453bc-106">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="453bc-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="453bc-107">d---4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="453bc-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="453bc-108">-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="453bc-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="453bc-109">-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="453bc-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="453bc-110">-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="453bc-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="453bc-111">PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 1</span><span class="sxs-lookup"><span data-stu-id="453bc-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="453bc-112">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği</span><span class="sxs-lookup"><span data-stu-id="453bc-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="453bc-113">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="453bc-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="453bc-114">d---4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="453bc-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="453bc-115">-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="453bc-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="453bc-116">-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="453bc-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="453bc-117">-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="453bc-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="453bc-118">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örnek\\Depth0</span><span class="sxs-lookup"><span data-stu-id="453bc-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="453bc-119">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="453bc-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="453bc-120">d---4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="453bc-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
