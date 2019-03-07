---
title: SelectionSetName öğesi EntrySelectedBy WideControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847372"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="e3461-102">WideControl EntrySelectedBy için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e3461-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="e3461-103">.NET nesne tanımı için belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3461-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="e3461-104">Bu nesnelerden birinin görüntülendiği zaman tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3461-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="e3461-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionSetName öğesinin WideEntry (biçimi) EntrySelectedBy WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="e3461-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3461-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3461-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3461-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3461-107">Attributes and Elements</span></span>

<span data-ttu-id="e3461-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e3461-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3461-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3461-109">Attributes</span></span>

<span data-ttu-id="e3461-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3461-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3461-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3461-111">Child Elements</span></span>

<span data-ttu-id="e3461-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3461-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3461-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3461-113">Parent Elements</span></span>

|<span data-ttu-id="e3461-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3461-114">Element</span></span>|<span data-ttu-id="e3461-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3461-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3461-116">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="e3461-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="e3461-117">Bu geniş bir girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3461-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3461-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="e3461-118">Text Value</span></span>

<span data-ttu-id="e3461-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3461-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3461-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3461-120">Remarks</span></span>

<span data-ttu-id="e3461-121">Her tanım, bir tür adı, seçim kümesi veya seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3461-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="e3461-122">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3461-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e3461-123">Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3461-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="e3461-124">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin bir görünüm için](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e3461-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e3461-125">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e3461-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3461-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e3461-126">See Also</span></span>

[<span data-ttu-id="e3461-127">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3461-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e3461-128">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="e3461-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e3461-129">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="e3461-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="e3461-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e3461-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)