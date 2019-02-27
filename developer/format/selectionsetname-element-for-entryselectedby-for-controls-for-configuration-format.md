---
title: İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850249"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="620cf-102">Yapılandırma Denetimleri için EntrySelectedBy SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="620cf-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="620cf-103">Denetimin bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="620cf-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="620cf-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="620cf-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="620cf-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) SelectionSetName öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="620cf-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="620cf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="620cf-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="620cf-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="620cf-107">Attributes and Elements</span></span>

<span data-ttu-id="620cf-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="620cf-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="620cf-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="620cf-109">Attributes</span></span>

<span data-ttu-id="620cf-110">Yok</span><span class="sxs-lookup"><span data-stu-id="620cf-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="620cf-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="620cf-111">Child Elements</span></span>

<span data-ttu-id="620cf-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="620cf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="620cf-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="620cf-113">Parent Elements</span></span>

|<span data-ttu-id="620cf-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="620cf-114">Element</span></span>|<span data-ttu-id="620cf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="620cf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="620cf-116">İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="620cf-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="620cf-117">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="620cf-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="620cf-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="620cf-118">Text Value</span></span>

<span data-ttu-id="620cf-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="620cf-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="620cf-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="620cf-120">Remarks</span></span>

<span data-ttu-id="620cf-121">Her denetim tanımı en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="620cf-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="620cf-122">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="620cf-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="620cf-123">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="620cf-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="620cf-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="620cf-124">See Also</span></span>

[<span data-ttu-id="620cf-125">İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="620cf-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="620cf-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="620cf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
