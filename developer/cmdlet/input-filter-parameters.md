---
title: Giriş filtre parametrelerini | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067697"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="0e801-102">Filtre Parametreleri Girişi</span><span class="sxs-lookup"><span data-stu-id="0e801-102">Input Filter Parameters</span></span>

<span data-ttu-id="0e801-103">Bir cmdlet tanımlayabilirsiniz `Filter`, `Include`, ve `Exclude` cmdlet etkiler giriş nesne kümesini filtrelemek parametreleri.</span><span class="sxs-lookup"><span data-stu-id="0e801-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="0e801-104">Genellikle, giriş nesne tarafından belirtilen bir `InputObject`, `Path`, veya `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0e801-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="0e801-105">Örneğin, bir cmdlet olabilir bir `Path` joker karakterler ve her bir giriş nesnesi için yol noktalarını kullanarak birden çok yol kabul eden bir parametre.</span><span class="sxs-lookup"><span data-stu-id="0e801-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="0e801-106">Birlikte kullanılan `Filter`, `Include`, ve `Exclude` parametreleri daha uygun yolları cmdlet çalıştırıldığında her saat çalışır.</span><span class="sxs-lookup"><span data-stu-id="0e801-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="0e801-107">Dahil etme ve dışlama parametreleri</span><span class="sxs-lookup"><span data-stu-id="0e801-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="0e801-108">`Include` Ve `Exclude` parametreleri dahil ya da cmdlet'e geçirilen giriş nesneler kümesinden dışlanan nesneleri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0e801-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="0e801-109">Filtre standart bir joker karakter dilinde ifade edilebilir olduğunda bu parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e801-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="0e801-110">(Joker karakterler hakkında daha fazla bilgi için bkz: [joker karakterleri destekleme Cmdlet parametreleri](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include` Parametre adları ekleme filtre eşleşen tüm nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0e801-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="0e801-111">`Exclude` Parametre adları eşleşen filtre tüm nesneleri dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="0e801-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="0e801-112">Filtre parametresi</span><span class="sxs-lookup"><span data-stu-id="0e801-112">Filter Parameter</span></span>

<span data-ttu-id="0e801-113">`Filter` Parametresi, standart bir joker karakter dilde değil ifade bir filtre belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e801-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="0e801-114">Örneğin, Active Directory hizmet arabirimi (ADSI) veya SQL filtreleri cmdlet'ine geçirilebilir kendi `Filter` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0e801-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="0e801-115">Windows PowerShell tarafından sağlanan Cmdlet'lerde, bu filtreler, cmdlet bir veri deposuna erişmek için Windows PowerShell sağlayıcıları tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0e801-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="0e801-116">Her bir sağlayıcı, genellikle kendi filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e801-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="0e801-117">Hiçbir giriş nesne kümesini belirtilirse filtreleme</span><span class="sxs-lookup"><span data-stu-id="0e801-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="0e801-118">Hiçbir giriş nesne kümesini belirtilirse, bu genellikle karşı tüm nesneleri filtrelemek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0e801-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="0e801-119">Daha fazla bilgi için[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="0e801-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e801-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0e801-120">See Also</span></span>

[<span data-ttu-id="0e801-121">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="0e801-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)