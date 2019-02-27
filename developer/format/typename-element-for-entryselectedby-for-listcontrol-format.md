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
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846889"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="85e96-102">ListControl EntrySelectedBy için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="85e96-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="85e96-103">Bu giriş liste görünümünün kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="85e96-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="85e96-104">Bir liste girişi için belirtilebilen türleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="85e96-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="85e96-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi TypeName öğesinin ListEntry (biçimi) EntrySelectedBy ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="85e96-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85e96-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85e96-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85e96-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85e96-107">Attributes and Elements</span></span>

<span data-ttu-id="85e96-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="85e96-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85e96-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85e96-109">Attributes</span></span>

<span data-ttu-id="85e96-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="85e96-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85e96-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85e96-111">Child Elements</span></span>

<span data-ttu-id="85e96-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="85e96-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85e96-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85e96-113">Parent Elements</span></span>

|<span data-ttu-id="85e96-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="85e96-114">Element</span></span>|<span data-ttu-id="85e96-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85e96-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85e96-116">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="85e96-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="85e96-117">Bu liste girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85e96-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="85e96-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="85e96-118">Text Value</span></span>

<span data-ttu-id="85e96-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="85e96-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="85e96-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85e96-120">Remarks</span></span>

<span data-ttu-id="85e96-121">Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85e96-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="85e96-122">Bu öğe listesi görünümü'nde nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="85e96-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="85e96-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="85e96-123">Example</span></span>

<span data-ttu-id="85e96-124">Aşağıdaki örnek, bir liste görünümü için bir giriş ayarlamak seçim belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85e96-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="85e96-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="85e96-125">See Also</span></span>

[<span data-ttu-id="85e96-126">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="85e96-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="85e96-127">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="85e96-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="85e96-128">EnrtySelectedBy ListEntry (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="85e96-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="85e96-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="85e96-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
