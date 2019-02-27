---
title: GroupBy (biçimi) için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851901"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="5da36-102">GroupBy için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="5da36-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="5da36-103">.NET özelliğinin değeri değiştiğinde yeni bir grup başlatan belirtir.</span><span class="sxs-lookup"><span data-stu-id="5da36-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="5da36-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) PropertyName öğesinin GroupBy (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5da36-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5da36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5da36-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5da36-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5da36-106">Attributes and Elements</span></span>

<span data-ttu-id="5da36-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5da36-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5da36-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5da36-108">Attributes</span></span>

<span data-ttu-id="5da36-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="5da36-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5da36-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5da36-110">Child Elements</span></span>

<span data-ttu-id="5da36-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5da36-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5da36-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5da36-112">Parent Elements</span></span>

|<span data-ttu-id="5da36-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5da36-113">Element</span></span>|<span data-ttu-id="5da36-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5da36-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5da36-115">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5da36-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="5da36-116">.NET nesne grubu nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5da36-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5da36-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="5da36-117">Text Value</span></span>

<span data-ttu-id="5da36-118">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="5da36-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5da36-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5da36-119">Remarks</span></span>

<span data-ttu-id="5da36-120">Bu özelliğin değeri değiştiğinde yeni bir grup Windows PowerShell başlatır.</span><span class="sxs-lookup"><span data-stu-id="5da36-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="5da36-121">Bu öğe belirtildiğinde, belirtemezsiniz [ScriptBlock](./scriptblock-element-for-groupby-format.md) yeni bir grup başlatmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="5da36-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="5da36-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="5da36-122">Example</span></span>

<span data-ttu-id="5da36-123">Aşağıdaki örnek, bir özellik değeri değiştiğinde yeni bir Grup Başlat gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5da36-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="5da36-124">Bu öğe içeren tam bir biçimlendirme dosyası örneği için bkz: [geniş Görünüm (gruplandırma ölçütü)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="5da36-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5da36-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5da36-125">See Also</span></span>

[<span data-ttu-id="5da36-126">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5da36-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5da36-127">GroupBy (biçimi) için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="5da36-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="5da36-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="5da36-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
