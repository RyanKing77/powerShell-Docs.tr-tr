---
title: TypeName öğesi SelectionCondition EntrySelectedBy ListControl (biçimi) için için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851558"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="fe438-102">ListControl için EntrySelectedBy için SelectionCondition için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="fe438-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="fe438-103">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe438-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="fe438-104">Bu tür, mevcut olduğunda listesi girişi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe438-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="fe438-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) EntrySelectedBy öğesinin ListEntries ListEntry öğesinin ListControl (biçimi) ListEntry EntrySelectedBy ListControl (biçimi) için için SelectionCondition ListControl (biçimi) TypeName öğesinin EntrySelectedBy SelectionCondition öğesinin ListControl (biçimi)</span><span class="sxs-lookup"><span data-stu-id="fe438-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe438-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe438-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe438-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe438-107">Attributes and Elements</span></span>

<span data-ttu-id="fe438-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe438-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe438-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe438-109">Attributes</span></span>

<span data-ttu-id="fe438-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe438-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe438-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe438-111">Child Elements</span></span>

<span data-ttu-id="fe438-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe438-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe438-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe438-113">Parent Elements</span></span>

|<span data-ttu-id="fe438-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe438-114">Element</span></span>|<span data-ttu-id="fe438-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe438-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe438-116">EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="fe438-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fe438-117">Bu liste girişi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe438-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe438-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="fe438-118">Text Value</span></span>

<span data-ttu-id="fe438-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="fe438-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe438-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe438-120">Remarks</span></span>

<span data-ttu-id="fe438-121">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe438-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="fe438-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fe438-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="fe438-123">Diğer hakkında daha fazla bilgi için bir liste görünümü bileşenlerini görmek [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fe438-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe438-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fe438-124">See Also</span></span>

[<span data-ttu-id="fe438-125">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe438-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fe438-126">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="fe438-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fe438-127">EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="fe438-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="fe438-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="fe438-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)