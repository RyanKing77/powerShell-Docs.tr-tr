---
title: TypeName öğesi türleri (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083799"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="3b6c6-102">Türler için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="3b6c6-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="3b6c6-103">.NET seçimi kümesine ait olan bir nesne türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="3b6c6-104">Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi) türler (biçimi) öğesi (biçimi) TypeName öğesi türleri</span><span class="sxs-lookup"><span data-stu-id="3b6c6-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3b6c6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b6c6-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b6c6-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3b6c6-106">Attributes and Elements</span></span>

<span data-ttu-id="3b6c6-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="3b6c6-108">En az bir `TypeName` öğe seçimi kümesinde eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b6c6-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b6c6-109">Attributes</span></span>

<span data-ttu-id="3b6c6-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3b6c6-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3b6c6-111">Child Elements</span></span>

<span data-ttu-id="3b6c6-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3b6c6-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3b6c6-113">Parent Elements</span></span>

|<span data-ttu-id="3b6c6-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b6c6-114">Element</span></span>|<span data-ttu-id="3b6c6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b6c6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b6c6-116">Türleri öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3b6c6-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="3b6c6-117">Seçimdeki ayarlanan .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3b6c6-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="3b6c6-118">Text Value</span></span>

<span data-ttu-id="3b6c6-119">.NET türünün tam adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b6c6-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b6c6-120">Remarks</span></span>

<span data-ttu-id="3b6c6-121">Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="3b6c6-122">Kendi görünümlerinizi tanımlarken, her bir görünüm içindeki tüm nesneleri listelemek yerine ayarlamak seçimi adını kullanarak nesne kümesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="3b6c6-123">Ortak seçimi ayarlar, biçimlendirme dosyası görünümlerini tanımlarken adlarına göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="3b6c6-124">Bu gibi durumlarda, `SelectionSetName` alt öğesi `ViewSelectedBy` görünüm öğesi kümesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="3b6c6-125">Ancak, farklı bir görünüm girişlerinin yalnızca görünüm bu girişi için geçerli bir seçim kümesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="3b6c6-126">Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3b6c6-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3b6c6-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6c6-127">Example</span></span>

<span data-ttu-id="3b6c6-128">Aşağıdaki örnekte gösterildiği bir `SelectionSet` dört .NET türlerini tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="3b6c6-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="3b6c6-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3b6c6-129">See Also</span></span>

[<span data-ttu-id="3b6c6-130">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="3b6c6-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3b6c6-131">SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3b6c6-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="3b6c6-132">SelectionSets öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3b6c6-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="3b6c6-133">Türleri öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3b6c6-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="3b6c6-134">Dosya biçimlendirme bir Windows PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="3b6c6-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
