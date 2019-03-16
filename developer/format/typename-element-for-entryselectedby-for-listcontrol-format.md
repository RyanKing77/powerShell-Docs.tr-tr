---
title: TypeName öğesi EntrySelectedBy ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059703"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f2efb-102">ListControl EntrySelectedBy için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f2efb-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f2efb-103">Bu giriş liste görünümünün kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2efb-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="f2efb-104">Bir liste girişi için belirtilebilen türleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="f2efb-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="f2efb-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi TypeName öğesinin ListEntry (biçimi) EntrySelectedBy ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f2efb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2efb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2efb-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2efb-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2efb-107">Attributes and Elements</span></span>

<span data-ttu-id="f2efb-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2efb-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2efb-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2efb-109">Attributes</span></span>

<span data-ttu-id="f2efb-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2efb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2efb-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2efb-111">Child Elements</span></span>

<span data-ttu-id="f2efb-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2efb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2efb-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2efb-113">Parent Elements</span></span>

|<span data-ttu-id="f2efb-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2efb-114">Element</span></span>|<span data-ttu-id="f2efb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2efb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2efb-116">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f2efb-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f2efb-117">Bu liste girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2efb-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2efb-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="f2efb-118">Text Value</span></span>

<span data-ttu-id="f2efb-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="f2efb-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2efb-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2efb-120">Remarks</span></span>

<span data-ttu-id="f2efb-121">Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2efb-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f2efb-122">Bu öğe listesi görünümü'nde nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f2efb-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2efb-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2efb-123">Example</span></span>

<span data-ttu-id="f2efb-124">Aşağıdaki örnek, bir liste görünümü için bir giriş ayarlamak seçim belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f2efb-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="f2efb-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f2efb-125">See Also</span></span>

[<span data-ttu-id="f2efb-126">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2efb-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f2efb-127">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f2efb-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f2efb-128">EntrySelectedBy ListEntry (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="f2efb-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f2efb-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="f2efb-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
