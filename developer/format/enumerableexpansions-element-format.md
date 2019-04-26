---
title: EnumerableExpansions öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066099"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="6fb9c-102">EnumerableExpansions Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="6fb9c-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="6fb9c-103">Bir görünümü'nde görüntülendiğinde .NET koleksiyon nesnelerini nasıl genişletilir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="6fb9c-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6fb9c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6fb9c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6fb9c-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6fb9c-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6fb9c-106">Attributes and Elements</span></span>

<span data-ttu-id="6fb9c-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EnumerableExpansions` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="6fb9c-108">Kullanabileceğiniz bir alt öğe sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="6fb9c-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6fb9c-109">Attributes</span></span>

<span data-ttu-id="6fb9c-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6fb9c-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6fb9c-111">Child Elements</span></span>

|<span data-ttu-id="6fb9c-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fb9c-112">Element</span></span>|<span data-ttu-id="6fb9c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fb9c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6fb9c-114">EnumerableExpansion öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6fb9c-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="6fb9c-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6fb9c-116">Bir görünümü'nde görüntülendiğinde, genişletilmiş belirli .NET koleksiyon nesnelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6fb9c-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6fb9c-117">Parent Elements</span></span>

|<span data-ttu-id="6fb9c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fb9c-118">Element</span></span>|<span data-ttu-id="6fb9c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fb9c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6fb9c-120">DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6fb9c-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="6fb9c-121">Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6fb9c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fb9c-122">Remarks</span></span>

<span data-ttu-id="6fb9c-123">Bu öğe, koleksiyon nesnelerini ve koleksiyondaki nesnelerin nasıl görüntüleneceğini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="6fb9c-124">Bu durumda, destekleyen herhangi bir nesne için bir koleksiyon nesnesini ifade eder **System.Collections.ICollection** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6fb9c-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fb9c-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6fb9c-125">See Also</span></span>

[<span data-ttu-id="6fb9c-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6fb9c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
