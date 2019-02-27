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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845517"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="7ef69-102">Yapılandırma Denetimleri için EntrySelectedBy SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="7ef69-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7ef69-103">Kullanılacak ortak bir denetim tanımı için bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ef69-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="7ef69-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ef69-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7ef69-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin yapılandırma (biçimi) denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğe için denetimler için özel denetim için denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy CustomEntry için için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için yapılandırma (biçimi) CustomEntry öğesi Yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7ef69-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ef69-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ef69-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ef69-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ef69-107">Attributes and Elements</span></span>

<span data-ttu-id="7ef69-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7ef69-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ef69-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7ef69-109">Attributes</span></span>

<span data-ttu-id="7ef69-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="7ef69-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ef69-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ef69-111">Child Elements</span></span>

|<span data-ttu-id="7ef69-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="7ef69-112">Element</span></span>|<span data-ttu-id="7ef69-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ef69-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ef69-114">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7ef69-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="7ef69-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7ef69-116">Koşul tetikleyen .NET özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef69-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7ef69-117">Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7ef69-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="7ef69-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7ef69-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef69-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="7ef69-120">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7ef69-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="7ef69-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7ef69-122">Koşul tetikleyen .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef69-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="7ef69-123">TypeName öğesi SelectionCondition yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="7ef69-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7ef69-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="7ef69-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7ef69-125">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ef69-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7ef69-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ef69-126">Parent Elements</span></span>

|<span data-ttu-id="7ef69-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="7ef69-127">Element</span></span>|<span data-ttu-id="7ef69-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ef69-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ef69-129">İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="7ef69-130">Bu giriş ortak denetim tanımının kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ef69-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7ef69-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ef69-131">Remarks</span></span>

<span data-ttu-id="7ef69-132">Aşağıdaki yönergeler, bir seçim koşulu tanımlarken gelmelidir:</span><span class="sxs-lookup"><span data-stu-id="7ef69-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="7ef69-133">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef69-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="7ef69-134">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ef69-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="7ef69-135">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7ef69-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ef69-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7ef69-136">See Also</span></span>

[<span data-ttu-id="7ef69-137">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7ef69-138">Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7ef69-139">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7ef69-140">TypeName öğesi SelectionCondition yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="7ef69-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7ef69-141">İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="7ef69-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="7ef69-142">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="7ef69-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
