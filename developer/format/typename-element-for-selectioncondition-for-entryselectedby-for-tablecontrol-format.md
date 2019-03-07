---
title: TableControl (biçimi) için EntrySelectedBy için SelectionCondition için TypeName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847162"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a8ed8-102">TableControl EntrySelectedBy için SelectionCondition TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a8ed8-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a8ed8-103">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="a8ed8-104">Bu türü mevcut olduğunda, koşul karşılanır ve tablo satırı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="a8ed8-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi TableRowEntry (biçimi) için SelectionCondition öğesi EntrySelectedBy EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition TypeName öğesinin TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a8ed8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8ed8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8ed8-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8ed8-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8ed8-107">Attributes and Elements</span></span>

<span data-ttu-id="a8ed8-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8ed8-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8ed8-109">Attributes</span></span>

<span data-ttu-id="a8ed8-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8ed8-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8ed8-111">Child Elements</span></span>

<span data-ttu-id="a8ed8-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8ed8-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8ed8-113">Parent Elements</span></span>

|<span data-ttu-id="a8ed8-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8ed8-114">Element</span></span>|<span data-ttu-id="a8ed8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8ed8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8ed8-116">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a8ed8-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a8ed8-117">Bu tablo satırı kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a8ed8-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="a8ed8-118">Text Value</span></span>

<span data-ttu-id="a8ed8-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8ed8-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8ed8-120">Remarks</span></span>

<span data-ttu-id="a8ed8-121">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ed8-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="a8ed8-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a8ed8-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a8ed8-123">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a8ed8-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8ed8-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a8ed8-124">See Also</span></span>

[<span data-ttu-id="a8ed8-125">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8ed8-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a8ed8-126">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="a8ed8-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a8ed8-127">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a8ed8-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a8ed8-128">SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="a8ed8-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a8ed8-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a8ed8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)