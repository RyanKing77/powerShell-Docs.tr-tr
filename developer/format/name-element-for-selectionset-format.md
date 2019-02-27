---
title: Öğe SelectionSet (biçimi) için ad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848331"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="8d8e5-102">SelectionSet için Ad Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="8d8e5-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="8d8e5-103">Seçimi kümesi başvurmak için kullanılan adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="8d8e5-104">Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi) adı öğesi SelectionSet (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8d8e5-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8d8e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d8e5-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8d8e5-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d8e5-106">Attributes and Elements</span></span>

<span data-ttu-id="8d8e5-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Name` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8d8e5-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d8e5-108">Attributes</span></span>

<span data-ttu-id="8d8e5-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8d8e5-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d8e5-110">Child Elements</span></span>

<span data-ttu-id="8d8e5-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8d8e5-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d8e5-112">Parent Elements</span></span>

|<span data-ttu-id="8d8e5-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d8e5-113">Element</span></span>|<span data-ttu-id="8d8e5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d8e5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8d8e5-115">SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8d8e5-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="8d8e5-116">Tek bir küme adı tarafından başvurulan .NET nesneleri kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8d8e5-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="8d8e5-117">Text Value</span></span>

<span data-ttu-id="8d8e5-118">Seçimi kümesi başvurmak için adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="8d8e5-119">Hangi karakter sınırlama kullanılabilir vardır.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d8e5-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d8e5-120">Remarks</span></span>

<span data-ttu-id="8d8e5-121">Burada belirtilen ad kullanılır `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="8d8e5-122">Göre görünümü, görünüm tanımı tarafından kullanılabilecek seçim kümesi (görünümler birden çok tanım olabilir) veya seçim koşulu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="8d8e5-123">Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8d8e5-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="8d8e5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d8e5-124">Example</span></span>

<span data-ttu-id="8d8e5-125">Bu örnek gösterir bir `SelectionSet` dört .NET türlerini tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="8d8e5-126">"FileSystemTypes" seçimi kümesinin adıdır.</span><span class="sxs-lookup"><span data-stu-id="8d8e5-126">The name of the selection set is "FileSystemTypes".</span></span>

```xml
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

## <a name="see-also"></a><span data-ttu-id="8d8e5-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8d8e5-127">See Also</span></span>

[<span data-ttu-id="8d8e5-128">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="8d8e5-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8d8e5-129">SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8d8e5-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="8d8e5-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="8d8e5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
