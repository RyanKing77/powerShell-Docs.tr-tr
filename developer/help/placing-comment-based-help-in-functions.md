---
title: Açıklama tabanlı Yardım işlevlerde yerleştirme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848177"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="58a65-102">İşlevlere Yorum Tabanlı Yardım Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="58a65-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="58a65-103">Bu konuda, bir işlev için açıklama tabanlı Yardım yerleştirileceği yeri açıklanmaktadır. böylece `Get-Help` cmdlet'i açıklama tabanlı Yardım konusunu doğru işlevi ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="58a65-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="58a65-104">Bir işlev için açıklama tabanlı Yardım yerleştirileceği yeri</span><span class="sxs-lookup"><span data-stu-id="58a65-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="58a65-105">İşlev gövdesi başında.</span><span class="sxs-lookup"><span data-stu-id="58a65-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="58a65-106">İşlev gövdesi sonunda.</span><span class="sxs-lookup"><span data-stu-id="58a65-106">At the end of the function body.</span></span>

- <span data-ttu-id="58a65-107">Önce `Function` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="58a65-107">Before the `Function` keyword.</span></span> <span data-ttu-id="58a65-108">İşlev bir betik veya betik modülü olduğunda olamaz birden çok boş satırı açıklama tabanlı Yardım son satırının arasında ve `Function` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="58a65-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="58a65-109">Aksi takdirde, `Get-Help` Yardım betiğiyle, işlev olmayan ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="58a65-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="58a65-110">Bir işlevde Yardım yerleştirme örnekleri</span><span class="sxs-lookup"><span data-stu-id="58a65-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="58a65-111">Aşağıdaki örnekler, her bir işlev için açıklama tabanlı Yardım üç yerleştirme seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="58a65-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="58a65-112">Bir işlev gövdesinin başında Yardım</span><span class="sxs-lookup"><span data-stu-id="58a65-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="58a65-113">Aşağıdaki örnek, açıklama tabanlı bir işlev gövdesinin başında gösterir.</span><span class="sxs-lookup"><span data-stu-id="58a65-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="58a65-114">Bir işlev gövdesinin sonunda Yardım</span><span class="sxs-lookup"><span data-stu-id="58a65-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="58a65-115">Aşağıdaki örnek, açıklama tabanlı bir işlev gövdesinin sonunda gösterir.</span><span class="sxs-lookup"><span data-stu-id="58a65-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="58a65-116">Önce Function anahtar Yardım</span><span class="sxs-lookup"><span data-stu-id="58a65-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="58a65-117">Aşağıdaki örnekler gösterilmektedir function anahtar sözcüğünü önce satırda açıklama tabanlı.</span><span class="sxs-lookup"><span data-stu-id="58a65-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```