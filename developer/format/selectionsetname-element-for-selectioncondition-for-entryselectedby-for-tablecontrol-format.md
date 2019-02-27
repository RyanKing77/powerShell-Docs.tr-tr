---
title: TableControl (biçimi) için EntrySelectedBy için SelectionCondition için SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851908"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="60b93-102">TableControl EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="60b93-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="60b93-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60b93-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="60b93-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu tablo görünümü tanımını kullanarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="60b93-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="60b93-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi TableRowEntry (biçimi) için SelectionCondition öğesi EntrySelectedBy EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition SelectionSetName öğesinin TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="60b93-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60b93-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60b93-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60b93-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60b93-107">Attributes and Elements</span></span>

<span data-ttu-id="60b93-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="60b93-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60b93-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60b93-109">Attributes</span></span>

<span data-ttu-id="60b93-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="60b93-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60b93-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60b93-111">Child Elements</span></span>

<span data-ttu-id="60b93-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="60b93-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60b93-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60b93-113">Parent Elements</span></span>

|<span data-ttu-id="60b93-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="60b93-114">Element</span></span>|<span data-ttu-id="60b93-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60b93-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60b93-116">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="60b93-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="60b93-117">Bu tablo görünümü tanımı için kullanılmak üzere mevcut olmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60b93-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60b93-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="60b93-118">Text Value</span></span>

<span data-ttu-id="60b93-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="60b93-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="60b93-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60b93-120">Remarks</span></span>

<span data-ttu-id="60b93-121">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="60b93-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="60b93-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="60b93-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="60b93-123">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="60b93-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="60b93-124">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="60b93-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="60b93-125">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="60b93-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60b93-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="60b93-126">See Also</span></span>

[<span data-ttu-id="60b93-127">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="60b93-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="60b93-128">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="60b93-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="60b93-129">TypeName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="60b93-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="60b93-130">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="60b93-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="60b93-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="60b93-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
