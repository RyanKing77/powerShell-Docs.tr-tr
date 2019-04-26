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
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066303"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="d60a0-102">Yapılandırma Denetimleri için CustomEntry EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="d60a0-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d60a0-103">Ortak denetim ya da bu denetim için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d60a0-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="d60a0-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d60a0-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d60a0-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için CustomEntry denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) EntrySelectedBy öğesinin denetimler için özel denetim için biçim) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="d60a0-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d60a0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d60a0-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d60a0-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d60a0-107">Attributes and Elements</span></span>

<span data-ttu-id="d60a0-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d60a0-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d60a0-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d60a0-109">Attributes</span></span>

<span data-ttu-id="d60a0-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="d60a0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d60a0-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d60a0-111">Child Elements</span></span>

|<span data-ttu-id="d60a0-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d60a0-112">Element</span></span>|<span data-ttu-id="d60a0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d60a0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d60a0-114">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="d60a0-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d60a0-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="d60a0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d60a0-116">Kullanılacak ortak denetim tanımı bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d60a0-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="d60a0-117">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="d60a0-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="d60a0-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="d60a0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d60a0-119">Bir ortak denetimi bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d60a0-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="d60a0-120">TypeName öğesi EntrySelectedBy yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="d60a0-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d60a0-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="d60a0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d60a0-122">Ortak denetimi bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d60a0-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d60a0-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d60a0-123">Parent Elements</span></span>

|<span data-ttu-id="d60a0-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d60a0-124">Element</span></span>|<span data-ttu-id="d60a0-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d60a0-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d60a0-126">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="d60a0-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="d60a0-127">Bir ortak denetimi tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d60a0-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d60a0-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d60a0-128">Remarks</span></span>

<span data-ttu-id="d60a0-129">En azından her tanımı en az bir .NET türü, seçim kümesi veya belirtilen seçim koşulu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d60a0-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="d60a0-130">Türler, seçimi ayarlar veya belirtebileceğiniz seçimi koşullar sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="d60a0-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="d60a0-131">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d60a0-131">See Also</span></span>

[<span data-ttu-id="d60a0-132">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="d60a0-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d60a0-133">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="d60a0-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="d60a0-134">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="d60a0-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="d60a0-135">TypeName öğesi EntrySelectedBy yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="d60a0-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="d60a0-136">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="d60a0-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
