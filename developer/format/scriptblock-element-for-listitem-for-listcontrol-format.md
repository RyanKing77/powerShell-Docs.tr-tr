---
title: ListItem ListControl (biçimi) için için ScriptBlock öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064586"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="52acd-102">ListControl ListItem için ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="52acd-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="52acd-103">Betikte satır değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="52acd-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="52acd-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListEntry ListControl (biçimi) ListItems öğesinin ListEntries ListEntry öğesinin ListControl (biçimi) ListItem ListControl (biçimi) için ListControl (biçimi) ScriptBlock öğesinin ListItems için ListControl (biçimi) LISTITEM öğesinin</span><span class="sxs-lookup"><span data-stu-id="52acd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52acd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52acd-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52acd-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="52acd-106">Attributes and Elements</span></span>

<span data-ttu-id="52acd-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="52acd-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52acd-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52acd-108">Attributes</span></span>

<span data-ttu-id="52acd-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="52acd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52acd-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="52acd-110">Child Elements</span></span>

<span data-ttu-id="52acd-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="52acd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="52acd-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="52acd-112">Parent Elements</span></span>

|<span data-ttu-id="52acd-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="52acd-113">Element</span></span>|<span data-ttu-id="52acd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52acd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52acd-115">LISTITEM öğesinin (biçimi)</span><span class="sxs-lookup"><span data-stu-id="52acd-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="52acd-116">Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="52acd-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="52acd-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="52acd-117">Text Value</span></span>

<span data-ttu-id="52acd-118">Değeri satır içinde görüntülenen komut dosyasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="52acd-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="52acd-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52acd-119">Remarks</span></span>

<span data-ttu-id="52acd-120">Bu öğe belirtildiğinde, belirtemezsiniz [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="52acd-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="52acd-121">Liste görünümünde betikleri belirtme hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="52acd-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="52acd-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="52acd-122">Example</span></span>

<span data-ttu-id="52acd-123">Aşağıdaki örnek, değeri görüntülenen özelliği belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="52acd-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="52acd-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="52acd-124">See Also</span></span>

[<span data-ttu-id="52acd-125">ListItem ListControl (biçimi) için için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="52acd-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="52acd-126">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="52acd-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="52acd-127">LISTITEM öğesinin ListControl (biçimi) için ListItems için</span><span class="sxs-lookup"><span data-stu-id="52acd-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="52acd-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="52acd-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
