---
title: TypeName öğesi EntrySelectedBy WideControl (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056016"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="dfa35-102">WideControl EntrySelectedBy için SelectionCondition TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="dfa35-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="dfa35-103">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfa35-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="dfa35-104">Bu tür, mevcut olduğunda tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfa35-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="dfa35-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin WideEntry (biçimi) EntrySelectedBy EntrySelectedBy WideEntry (biçimi) için için SelectionCondition TypeName öğesinin WideEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="dfa35-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dfa35-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfa35-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfa35-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfa35-107">Attributes and Elements</span></span>

<span data-ttu-id="dfa35-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="dfa35-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfa35-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dfa35-109">Attributes</span></span>

<span data-ttu-id="dfa35-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="dfa35-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dfa35-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfa35-111">Child Elements</span></span>

<span data-ttu-id="dfa35-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="dfa35-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dfa35-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfa35-113">Parent Elements</span></span>

|<span data-ttu-id="dfa35-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="dfa35-114">Element</span></span>|<span data-ttu-id="dfa35-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfa35-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfa35-116">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="dfa35-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="dfa35-117">Bu geniş bir girdi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dfa35-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dfa35-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="dfa35-118">Text Value</span></span>

<span data-ttu-id="dfa35-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="dfa35-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfa35-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfa35-120">Remarks</span></span>

<span data-ttu-id="dfa35-121">Seçim koşulu .NET türü belirtebilir veya bir seçim ayarlandı, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfa35-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="dfa35-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="dfa35-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dfa35-123">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="dfa35-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa35-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="dfa35-124">See Also</span></span>

[<span data-ttu-id="dfa35-125">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="dfa35-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="dfa35-126">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="dfa35-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dfa35-127">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="dfa35-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dfa35-128">SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="dfa35-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="dfa35-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="dfa35-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
