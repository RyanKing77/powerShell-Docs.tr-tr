---
title: Açıklama tabanlı Yardım betiklerde yerleştirme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083238"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="ad35e-102">Betiklere Yorum Tabanlı Yardım Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="ad35e-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="ad35e-103">Bu konuda, bir komut dosyası için açıklama tabanlı Yardım yerleştirileceği yeri açıklanmaktadır. böylece `Get-Help` cmdlet'i, açıklama tabanlı Yardım konusuna değildir komut dosyasında olabilir herhangi işlevleri ve komut dosyaları ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="ad35e-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="ad35e-104">Bir komut dosyası için açıklama tabanlı Yardım yerleştirileceği yeri</span><span class="sxs-lookup"><span data-stu-id="ad35e-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="ad35e-105">Komut dosyasının başında.</span><span class="sxs-lookup"><span data-stu-id="ad35e-105">At the beginning of the script file.</span></span> <span data-ttu-id="ad35e-106">Betik Yardım betikte yalnızca açıklama ve boş satırları tarafından öncesinde.</span><span class="sxs-lookup"><span data-stu-id="ad35e-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="ad35e-107">Betiğin sonunda.</span><span class="sxs-lookup"><span data-stu-id="ad35e-107">At the end of the script file.</span></span>

  <span data-ttu-id="ad35e-108">Listedeki ilk öğe (sonra Yardımı) betik gövdesi bir işlev bildirimi ise, işlev bildirimi ile Yardım komut dosyasının sonuna arasındaki en az iki boş satırlar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad35e-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="ad35e-109">Aksi takdirde, Yardım işlevi değildir komut için Yardım için Yardım'ı olacak şekilde yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="ad35e-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="ad35e-110">Bir komut dosyası yerleşimden Yardım örnekleri</span><span class="sxs-lookup"><span data-stu-id="ad35e-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="ad35e-111">Aşağıdaki örnekler, her bir komut dosyası için açıklama tabanlı Yardım yerleştirme seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad35e-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="ad35e-112">Bir komut dosyasının başında Yardım</span><span class="sxs-lookup"><span data-stu-id="ad35e-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="ad35e-113">Aşağıdaki örnek, açıklama tabanlı bir komut dosyasının başında gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad35e-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="ad35e-114">Bir betik sonunda Yardım</span><span class="sxs-lookup"><span data-stu-id="ad35e-114">Help at the End of a Script</span></span>

 <span data-ttu-id="ad35e-115">Aşağıdaki örnek, açıklama tabanlı bir komut dosyası sonunda gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad35e-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```