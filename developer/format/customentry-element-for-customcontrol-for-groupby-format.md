---
title: GroupBy (biçimi) için özel denetim için CustomEntry öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066496"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="cc0ac-102">GroupBy CustomControl için CustomEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="cc0ac-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="cc0ac-103">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-103">Provides a definition of the control.</span></span> <span data-ttu-id="cc0ac-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cc0ac-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="cc0ac-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc0ac-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc0ac-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc0ac-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="cc0ac-107">Attributes and Elements</span></span>

<span data-ttu-id="cc0ac-108">Aşağıdaki öznitelikler, alt ve üst öğelerinin bölümlerde `CustomEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc0ac-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc0ac-109">Attributes</span></span>

<span data-ttu-id="cc0ac-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc0ac-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="cc0ac-111">Child Elements</span></span>

|<span data-ttu-id="cc0ac-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc0ac-112">Element</span></span>|<span data-ttu-id="cc0ac-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc0ac-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc0ac-114">GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="cc0ac-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="cc0ac-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cc0ac-116">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="cc0ac-117">GroupBy (biçimi) için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="cc0ac-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="cc0ac-118">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-118">Required element.</span></span><br /><br /> <span data-ttu-id="cc0ac-119">Denetimin veri görüntüleme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc0ac-120">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="cc0ac-120">Parent Elements</span></span>

|<span data-ttu-id="cc0ac-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc0ac-121">Element</span></span>|<span data-ttu-id="cc0ac-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc0ac-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc0ac-123">GroupBy (biçimi) için özel denetim için CustomEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="cc0ac-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="cc0ac-124">Denetim için tanımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc0ac-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc0ac-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc0ac-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="cc0ac-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="cc0ac-126">See Also</span></span>

[<span data-ttu-id="cc0ac-127">GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="cc0ac-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="cc0ac-128">GroupBy (biçimi) için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="cc0ac-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="cc0ac-129">GroupBy (biçimi) için özel denetim için CustomEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="cc0ac-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="cc0ac-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="cc0ac-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
