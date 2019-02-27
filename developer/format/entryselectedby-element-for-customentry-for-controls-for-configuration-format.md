---
title: İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848681"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="0249d-102">Yapılandırma Denetimleri için CustomEntry EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="0249d-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0249d-103">Ortak denetim ya da bu denetim için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0249d-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="0249d-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0249d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0249d-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için CustomEntry denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) EntrySelectedBy öğesinin denetimler için özel denetim için biçim) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="0249d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0249d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0249d-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0249d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0249d-107">Attributes and Elements</span></span>

<span data-ttu-id="0249d-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0249d-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0249d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0249d-109">Attributes</span></span>

<span data-ttu-id="0249d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="0249d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0249d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0249d-111">Child Elements</span></span>

|<span data-ttu-id="0249d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="0249d-112">Element</span></span>|<span data-ttu-id="0249d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0249d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0249d-114">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="0249d-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0249d-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0249d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0249d-116">Kullanılacak ortak denetim tanımı bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0249d-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="0249d-117">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="0249d-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0249d-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0249d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0249d-119">Bir ortak denetimi bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0249d-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="0249d-120">TypeName öğesi EntrySelectedBy yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="0249d-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0249d-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0249d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0249d-122">Ortak denetimi bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0249d-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0249d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0249d-123">Parent Elements</span></span>

|<span data-ttu-id="0249d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="0249d-124">Element</span></span>|<span data-ttu-id="0249d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0249d-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0249d-126">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="0249d-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="0249d-127">Bir ortak denetimi tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0249d-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0249d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0249d-128">Remarks</span></span>

<span data-ttu-id="0249d-129">En azından her tanımı en az bir .NET türü, seçim kümesi veya belirtilen seçim koşulu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0249d-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="0249d-130">Türler, seçimi ayarlar veya belirtebileceğiniz seçimi koşullar sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="0249d-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="0249d-131">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0249d-131">See Also</span></span>

[<span data-ttu-id="0249d-132">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="0249d-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="0249d-133">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="0249d-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0249d-134">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="0249d-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="0249d-135">TypeName öğesi EntrySelectdBy yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="0249d-135">TypeName Element for EntrySelectdBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0249d-136">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="0249d-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
