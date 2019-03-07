---
title: SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851551"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="db34f-102">Görünüm CustomControl için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="db34f-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="db34f-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="db34f-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="db34f-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="db34f-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="db34f-105">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db34f-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="db34f-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries EntrySelectedBy görünümü (biçimi) için özel denetim için Öğe için CustomEntry görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="db34f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db34f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db34f-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db34f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="db34f-108">Attributes and Elements</span></span>

<span data-ttu-id="db34f-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="db34f-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db34f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="db34f-110">Attributes</span></span>

<span data-ttu-id="db34f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="db34f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db34f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="db34f-112">Child Elements</span></span>

<span data-ttu-id="db34f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="db34f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="db34f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="db34f-114">Parent Elements</span></span>

|<span data-ttu-id="db34f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="db34f-115">Element</span></span>|<span data-ttu-id="db34f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db34f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db34f-117">SelectionCondition öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="db34f-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="db34f-118">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="db34f-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="db34f-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="db34f-119">Text Value</span></span>

<span data-ttu-id="db34f-120">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="db34f-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="db34f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db34f-121">Remarks</span></span>

<span data-ttu-id="db34f-122">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="db34f-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="db34f-123">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="db34f-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="db34f-124">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="db34f-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="db34f-125">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="db34f-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db34f-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="db34f-126">See Also</span></span>

[<span data-ttu-id="db34f-127">SelectionCondition öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="db34f-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="db34f-128">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="db34f-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="db34f-129">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="db34f-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="db34f-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="db34f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)