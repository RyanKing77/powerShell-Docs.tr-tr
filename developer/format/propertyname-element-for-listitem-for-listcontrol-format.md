---
title: ListItem ListControl (biçimi) için için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846630"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="f2615-102">ListControl ListItem için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f2615-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="f2615-103">.NET özelliğinin değeri, listede görüntülenen belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2615-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="f2615-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) ListItems öğesi (biçimi) LISTITEM öğesinin (biçimi) PropertyName öğesi ListItem (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f2615-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2615-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2615-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2615-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2615-106">Attributes and Elements</span></span>

<span data-ttu-id="f2615-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2615-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2615-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2615-108">Attributes</span></span>

<span data-ttu-id="f2615-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2615-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2615-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2615-110">Child Elements</span></span>

<span data-ttu-id="f2615-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2615-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2615-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2615-112">Parent Elements</span></span>

|<span data-ttu-id="f2615-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2615-113">Element</span></span>|<span data-ttu-id="f2615-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2615-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2615-115">LISTITEM öğesinin (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f2615-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="f2615-116">Özellik veya betik değeri liste görünümünün satırda görüntülenen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2615-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2615-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="f2615-117">Text Value</span></span>

<span data-ttu-id="f2615-118">Özellik değeri görüntülenen adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f2615-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2615-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2615-119">Remarks</span></span>

<span data-ttu-id="f2615-120">Bu öğe belirtildiğinde, belirtemezsiniz [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2615-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="f2615-121">Özellik değeri görüntülenmesinin yanı sıra değeri veya değerin görünümünü değiştirmek için kullanılan biçim dizesi için bir etiket de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2615-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="f2615-122">Liste görünümünde veri belirtme hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f2615-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2615-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2615-123">Example</span></span>

<span data-ttu-id="f2615-124">Aşağıdaki örnek, özellik değeri görüntülenir ve etiket belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f2615-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="f2615-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f2615-125">See Also</span></span>

[<span data-ttu-id="f2615-126">ListItem ListControl (biçimi) için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="f2615-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f2615-127">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2615-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f2615-128">LISTITEM öğesinin ListControl(Format) için</span><span class="sxs-lookup"><span data-stu-id="f2615-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="f2615-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="f2615-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
