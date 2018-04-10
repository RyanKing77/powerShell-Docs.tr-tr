---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="58dd5-102">-Derinliği parametresi Get-Childıtem var</span><span class="sxs-lookup"><span data-stu-id="58dd5-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="58dd5-103">**Get-Childıtem** artık bir **– derinliği** parametresi ile kullandığınız **– Recurse** özyineleme sınırlamak için:</span><span class="sxs-lookup"><span data-stu-id="58dd5-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="58dd5-104">PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 0</span><span class="sxs-lookup"><span data-stu-id="58dd5-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="58dd5-105">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği</span><span class="sxs-lookup"><span data-stu-id="58dd5-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="58dd5-106">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="58dd5-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="58dd5-107">d---4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="58dd5-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="58dd5-108">-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="58dd5-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="58dd5-109">-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="58dd5-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="58dd5-110">-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="58dd5-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="58dd5-111">PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 1</span><span class="sxs-lookup"><span data-stu-id="58dd5-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="58dd5-112">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği</span><span class="sxs-lookup"><span data-stu-id="58dd5-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="58dd5-113">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="58dd5-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="58dd5-114">d---4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="58dd5-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="58dd5-115">-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref</span><span class="sxs-lookup"><span data-stu-id="58dd5-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="58dd5-116">-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="58dd5-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="58dd5-117">-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="58dd5-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="58dd5-118">Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örnek\\Depth0</span><span class="sxs-lookup"><span data-stu-id="58dd5-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="58dd5-119">Mod LastWriteTime uzunluğu adı</span><span class="sxs-lookup"><span data-stu-id="58dd5-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="58dd5-120">d---4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="58dd5-120">d----- 4/14/2015 5:33 PM Depth1</span></span>