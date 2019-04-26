---
title: İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075775"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="fa982-102">Yapılandırma Denetimleri için EntrySelectedBy SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="fa982-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="fa982-103">Kullanılacak ortak bir denetim tanımı için bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa982-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="fa982-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa982-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="fa982-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin yapılandırma (biçimi) denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğe için denetimler için özel denetim için denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy CustomEntry için için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için yapılandırma (biçimi) CustomEntry öğesi Yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="fa982-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa982-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa982-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa982-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fa982-107">Attributes and Elements</span></span>

<span data-ttu-id="fa982-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fa982-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa982-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa982-109">Attributes</span></span>

<span data-ttu-id="fa982-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="fa982-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa982-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fa982-111">Child Elements</span></span>

|<span data-ttu-id="fa982-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa982-112">Element</span></span>|<span data-ttu-id="fa982-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa982-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa982-114">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fa982-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="fa982-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fa982-116">Koşul tetikleyen .NET özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa982-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="fa982-117">Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fa982-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="fa982-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fa982-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa982-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="fa982-120">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fa982-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="fa982-121">Optional element.</span></span><br /><br /> <span data-ttu-id="fa982-122">Koşul tetikleyen .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa982-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="fa982-123">TypeName öğesi SelectionCondition yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="fa982-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fa982-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="fa982-124">Optional element.</span></span><br /><br /> <span data-ttu-id="fa982-125">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa982-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fa982-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fa982-126">Parent Elements</span></span>

|<span data-ttu-id="fa982-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa982-127">Element</span></span>|<span data-ttu-id="fa982-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa982-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa982-129">İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="fa982-130">Bu giriş ortak denetim tanımının kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa982-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fa982-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa982-131">Remarks</span></span>

<span data-ttu-id="fa982-132">Aşağıdaki yönergeler, bir seçim koşulu tanımlarken gelmelidir:</span><span class="sxs-lookup"><span data-stu-id="fa982-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="fa982-133">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa982-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="fa982-134">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa982-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="fa982-135">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fa982-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa982-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fa982-136">See Also</span></span>

[<span data-ttu-id="fa982-137">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fa982-138">Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fa982-139">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fa982-140">TypeName öğesi SelectionCondition yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="fa982-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fa982-141">İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="fa982-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="fa982-142">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="fa982-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
