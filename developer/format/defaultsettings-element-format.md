---
title: DefaultSettings öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066354"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="8694d-102">DefaultSettings Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="8694d-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="8694d-103">Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8694d-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="8694d-104">Ortak ayarları hataları görüntüleme koleksiyonları nasıl genişletilir, tanımlama, tabloları ve diğer metin kaydırma içerir.</span><span class="sxs-lookup"><span data-stu-id="8694d-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="8694d-105">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8694d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8694d-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8694d-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="8694d-107">Attributes and Elements</span></span>

<span data-ttu-id="8694d-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `DefaultSettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8694d-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8694d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8694d-109">Attributes</span></span>

<span data-ttu-id="8694d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="8694d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8694d-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="8694d-111">Child Elements</span></span>

|<span data-ttu-id="8694d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="8694d-112">Element</span></span>|<span data-ttu-id="8694d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8694d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8694d-114">DisplayError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="8694d-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8694d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8694d-116">Bir veri parçasını görüntülenirken bir hata oluştuğunda #ERR dize görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8694d-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="8694d-117">EnumerableExpansions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="8694d-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8694d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8694d-119">Bir görünümü'nde görüntülendiğinde genişletilmiş .NET nesneleri farklı yollarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8694d-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="8694d-120">PropertyCountForTable (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="8694d-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8694d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8694d-122">Bir nesne, nesne Tablo görünümünde görüntülemek için gereken özellikleri en az sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8694d-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="8694d-123">ShowError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="8694d-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8694d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8694d-125">Bir veri parçasını görüntülenirken bir hata oluştuğunda tam hata kaydı görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8694d-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="8694d-126">WrapTables öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="8694d-127">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8694d-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8694d-128">Sütun genişliğini uygun değilse, bir tablodaki verileri sonraki satıra taşınır belirtir.</span><span class="sxs-lookup"><span data-stu-id="8694d-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8694d-129">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="8694d-129">Parent Elements</span></span>

|<span data-ttu-id="8694d-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="8694d-130">Element</span></span>|<span data-ttu-id="8694d-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8694d-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8694d-132">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="8694d-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="8694d-133">Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8694d-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8694d-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8694d-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="8694d-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8694d-135">See Also</span></span>

[<span data-ttu-id="8694d-136">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="8694d-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="8694d-137">DisplayError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="8694d-138">EnumerableExpansions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="8694d-139">PropertyCountForTable (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="8694d-140">ShowError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="8694d-141">WrapTables öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8694d-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="8694d-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="8694d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
