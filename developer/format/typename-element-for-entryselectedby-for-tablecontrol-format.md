---
title: TableControl (biçimi) için EntrySelectedBy için TypeName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083969"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="46d89-102">TableControl EntrySelectedBy için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="46d89-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="46d89-103">Tablo görünümü bu girişi kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="46d89-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="46d89-104">Bir tablo girişi için belirtilebilen türleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="46d89-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="46d89-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi (biçimi) TypeName öğesi EntrySelectedBy için TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="46d89-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46d89-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46d89-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46d89-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="46d89-107">Attributes and Elements</span></span>

<span data-ttu-id="46d89-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="46d89-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="46d89-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46d89-109">Attributes</span></span>

<span data-ttu-id="46d89-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="46d89-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46d89-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="46d89-111">Child Elements</span></span>

<span data-ttu-id="46d89-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="46d89-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="46d89-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="46d89-113">Parent Elements</span></span>

|<span data-ttu-id="46d89-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="46d89-114">Element</span></span>|<span data-ttu-id="46d89-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46d89-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46d89-116">EntrySelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="46d89-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="46d89-117">Bu girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46d89-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="46d89-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="46d89-118">Text Value</span></span>

<span data-ttu-id="46d89-119">.NET türü adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="46d89-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="46d89-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46d89-120">Remarks</span></span>

<span data-ttu-id="46d89-121">Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46d89-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="46d89-122">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="46d89-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46d89-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="46d89-123">See Also</span></span>

[<span data-ttu-id="46d89-124">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="46d89-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="46d89-125">EntrySelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="46d89-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="46d89-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="46d89-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
