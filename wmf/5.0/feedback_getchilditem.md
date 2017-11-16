---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="a98ee-102">-Derinliği parametresi Get-Childıtem var</span><span class="sxs-lookup"><span data-stu-id="a98ee-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="a98ee-103">**Get-Childıtem** artık bir **– derinliği** parametresi ile kullandığınız **– Recurse** özyineleme sınırlamak için:</span><span class="sxs-lookup"><span data-stu-id="a98ee-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="a98ee-104">PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 0</span><span class="sxs-lookup"><span data-stu-id="a98ee-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="a98ee-105">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği</span><span class="sxs-lookup"><span data-stu-id="a98ee-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a98ee-106">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="a98ee-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a98ee-107">d---4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="a98ee-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a98ee-108">-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="a98ee-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a98ee-109">-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a98ee-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a98ee-110">-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a98ee-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a98ee-111">PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 1</span><span class="sxs-lookup"><span data-stu-id="a98ee-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="a98ee-112">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği</span><span class="sxs-lookup"><span data-stu-id="a98ee-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a98ee-113">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="a98ee-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a98ee-114">d---4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="a98ee-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a98ee-115">-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="a98ee-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a98ee-116">-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a98ee-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a98ee-117">-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a98ee-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a98ee-118">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örnek\\Depth0</span><span class="sxs-lookup"><span data-stu-id="a98ee-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="a98ee-119">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="a98ee-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a98ee-120">d---4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="a98ee-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

