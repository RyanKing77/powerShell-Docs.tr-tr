---
title: SelectionSetName öğesi ViewSelectedBy (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076234"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="578c1-102">ViewSelectedBy için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="578c1-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="578c1-103">Görünüm tarafından görüntülenen .NET nesneleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="578c1-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="578c1-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ViewSelectedBy öğesi (biçimi) SelectionSetName öğesi ViewSelectedBy (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="578c1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="578c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="578c1-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="578c1-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="578c1-106">Attributes and Elements</span></span>

<span data-ttu-id="578c1-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="578c1-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="578c1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="578c1-108">Attributes</span></span>

<span data-ttu-id="578c1-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="578c1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="578c1-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="578c1-110">Child Elements</span></span>

<span data-ttu-id="578c1-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="578c1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="578c1-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="578c1-112">Parent Elements</span></span>

|<span data-ttu-id="578c1-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="578c1-113">Element</span></span>|<span data-ttu-id="578c1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="578c1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="578c1-115">ViewSelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="578c1-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="578c1-116">Görünüm tarafından görüntülenen .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="578c1-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="578c1-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="578c1-117">Text Value</span></span>

<span data-ttu-id="578c1-118">Tarafından tanımlanan seçim kümesinin adını belirtmek `Name` seçimi kümesi için öğesi.</span><span class="sxs-lookup"><span data-stu-id="578c1-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="578c1-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="578c1-119">Remarks</span></span>

<span data-ttu-id="578c1-120">Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="578c1-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="578c1-121">Tanımlama ve başvurma seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="578c1-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="578c1-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="578c1-122">Example</span></span>

<span data-ttu-id="578c1-123">Aşağıdaki örnek, bir liste görünümü için seçim belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="578c1-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="578c1-124">Aynı şemayı, tablo, geniş ve özel görünümleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="578c1-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="578c1-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="578c1-125">See Also</span></span>

[<span data-ttu-id="578c1-126">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="578c1-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="578c1-127">ViewSelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="578c1-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="578c1-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="578c1-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
