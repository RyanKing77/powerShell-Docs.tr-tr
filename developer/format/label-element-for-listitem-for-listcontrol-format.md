---
title: Etiket öğesi için ListItem ListControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065436"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="65656-102">ListControl ListItem için Etiket Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="65656-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="65656-103">Sol özellik veya betik değerin satırında görüntülenen etiketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="65656-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="65656-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) ListItems ListEntry ListControl öğesi (için için ListEntry öğesinin ListControl (biçimi) ListItem ListControl (biçimi) için ListControl (biçimi) etiketi öğesinin ListItems için LISTITEM öğesinin biçimi)</span><span class="sxs-lookup"><span data-stu-id="65656-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65656-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65656-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65656-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="65656-106">Attributes and Elements</span></span>

<span data-ttu-id="65656-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Label` öğesi.</span><span class="sxs-lookup"><span data-stu-id="65656-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65656-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="65656-108">Attributes</span></span>

<span data-ttu-id="65656-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="65656-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65656-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="65656-110">Child Elements</span></span>

<span data-ttu-id="65656-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="65656-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65656-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="65656-112">Parent Elements</span></span>

|<span data-ttu-id="65656-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="65656-113">Element</span></span>|<span data-ttu-id="65656-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65656-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65656-115">LISTITEM öğesinin ListControl (biçimi) için ListItems için</span><span class="sxs-lookup"><span data-stu-id="65656-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="65656-116">Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65656-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="65656-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="65656-117">Text Value</span></span>

<span data-ttu-id="65656-118">Görüntü özelliği ya da komut değeri solundaki olacak şekilde bir etiket belirtin.</span><span class="sxs-lookup"><span data-stu-id="65656-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="65656-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65656-119">Remarks</span></span>

<span data-ttu-id="65656-120">Bir etiket belirtilmezse, özelliği veya komut dosyası adı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65656-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="65656-121">Liste görünümünde etiketler kullanma hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="65656-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="65656-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="65656-122">Example</span></span>

<span data-ttu-id="65656-123">Aşağıdaki örnek, bir etiket için bir satır eklemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="65656-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="65656-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="65656-124">See Also</span></span>

[<span data-ttu-id="65656-125">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="65656-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="65656-126">LISTITEM öğesinin (biçimi)</span><span class="sxs-lookup"><span data-stu-id="65656-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="65656-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="65656-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
