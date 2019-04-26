---
title: GroupBy (biçimi) için etiket öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065419"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="e8b12-102">GroupBy için Etiket Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e8b12-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="e8b12-103">Yeni bir grup ile karşılaşıldığında görüntülenen etiketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8b12-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="e8b12-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) GroupBy öğesi görünümü (biçimi) etiketi öğesinin GroupBy (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e8b12-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8b12-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8b12-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8b12-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e8b12-106">Attributes and Elements</span></span>

<span data-ttu-id="e8b12-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Label` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8b12-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8b12-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e8b12-108">Attributes</span></span>

<span data-ttu-id="e8b12-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8b12-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8b12-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e8b12-110">Child Elements</span></span>

<span data-ttu-id="e8b12-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8b12-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e8b12-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e8b12-112">Parent Elements</span></span>

|<span data-ttu-id="e8b12-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8b12-113">Element</span></span>|<span data-ttu-id="e8b12-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8b12-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8b12-115">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e8b12-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="e8b12-116">Yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8b12-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e8b12-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="e8b12-117">Text Value</span></span>

<span data-ttu-id="e8b12-118">Windows PowerShell bir yeni özellik veya komut dosyası değerini karşılaştığında görüntülenen metni belirtin.</span><span class="sxs-lookup"><span data-stu-id="e8b12-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8b12-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8b12-119">Remarks</span></span>

<span data-ttu-id="e8b12-120">Bu öğe tarafından belirtilen metin ek olarak, Windows PowerShell grubu başlayıp önce ve sonra grubu boş bir satır ekler. yeni değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e8b12-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="e8b12-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8b12-121">Example</span></span>

<span data-ttu-id="e8b12-122">Aşağıdaki örnek yeni bir Grup etiketi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e8b12-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="e8b12-123">Görüntülenen etiket şuna benzer şekilde görünür: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="e8b12-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="e8b12-124">Bu öğe içeren tam bir biçimlendirme dosyası örneği için bkz: [geniş Görünüm (gruplandırma ölçütü)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="e8b12-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8b12-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e8b12-125">See Also</span></span>

[<span data-ttu-id="e8b12-126">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e8b12-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e8b12-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e8b12-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
