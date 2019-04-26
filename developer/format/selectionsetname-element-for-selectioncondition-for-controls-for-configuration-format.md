---
title: İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064039"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="d8eca-102">Yapılandırma Denetimleri için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="d8eca-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d8eca-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8eca-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="d8eca-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8eca-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="d8eca-105">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8eca-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d8eca-106">Yapılandırma öğesi (biçimi) denetimleri öğesinin yapılandırma (biçimi) denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğe için denetimler için özel denetim için denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy denetimleri için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için yapılandırma (biçimi) CustomEntry öğesi SelectionCondition denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="d8eca-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8eca-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8eca-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8eca-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d8eca-108">Attributes and Elements</span></span>

<span data-ttu-id="d8eca-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8eca-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8eca-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8eca-110">Attributes</span></span>

<span data-ttu-id="d8eca-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8eca-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8eca-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d8eca-112">Child Elements</span></span>

<span data-ttu-id="d8eca-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8eca-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8eca-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d8eca-114">Parent Elements</span></span>

|<span data-ttu-id="d8eca-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8eca-115">Element</span></span>|<span data-ttu-id="d8eca-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8eca-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8eca-117">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="d8eca-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d8eca-118">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d8eca-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d8eca-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="d8eca-119">Text Value</span></span>

<span data-ttu-id="d8eca-120">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d8eca-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8eca-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8eca-121">Remarks</span></span>

<span data-ttu-id="d8eca-122">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="d8eca-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="d8eca-123">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d8eca-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d8eca-124">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8eca-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="d8eca-125">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d8eca-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8eca-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d8eca-126">See Also</span></span>

[<span data-ttu-id="d8eca-127">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="d8eca-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d8eca-128">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="d8eca-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d8eca-129">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="d8eca-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d8eca-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="d8eca-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
