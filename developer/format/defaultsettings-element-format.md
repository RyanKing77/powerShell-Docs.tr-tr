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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059074"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="72d41-102">DefaultSettings Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="72d41-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="72d41-103">Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72d41-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="72d41-104">Ortak ayarları hataları görüntüleme koleksiyonları nasıl genişletilir, tanımlama, tabloları ve diğer metin kaydırma içerir.</span><span class="sxs-lookup"><span data-stu-id="72d41-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="72d41-105">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72d41-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72d41-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72d41-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="72d41-107">Attributes and Elements</span></span>

<span data-ttu-id="72d41-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `DefaultSettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="72d41-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="72d41-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="72d41-109">Attributes</span></span>

<span data-ttu-id="72d41-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="72d41-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72d41-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="72d41-111">Child Elements</span></span>

|<span data-ttu-id="72d41-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="72d41-112">Element</span></span>|<span data-ttu-id="72d41-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72d41-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72d41-114">DisplayError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="72d41-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="72d41-115">Optional element.</span></span><br /><br /> <span data-ttu-id="72d41-116">Bir veri parçasını görüntülenirken bir hata oluştuğunda #ERR dize görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="72d41-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="72d41-117">EnumerableExpansions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="72d41-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="72d41-118">Optional element.</span></span><br /><br /> <span data-ttu-id="72d41-119">Bir görünümü'nde görüntülendiğinde genişletilmiş .NET nesneleri farklı yollarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72d41-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="72d41-120">PropertyCountForTable (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="72d41-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="72d41-121">Optional element.</span></span><br /><br /> <span data-ttu-id="72d41-122">Bir nesne, nesne Tablo görünümünde görüntülemek için gereken özellikleri en az sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="72d41-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="72d41-123">ShowError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="72d41-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="72d41-124">Optional element.</span></span><br /><br /> <span data-ttu-id="72d41-125">Bir veri parçasını görüntülenirken bir hata oluştuğunda tam hata kaydı görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="72d41-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="72d41-126">WrapTables öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="72d41-127">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="72d41-127">Optional element.</span></span><br /><br /> <span data-ttu-id="72d41-128">Sütun genişliğini uygun değilse, bir tablodaki verileri sonraki satıra taşınır belirtir.</span><span class="sxs-lookup"><span data-stu-id="72d41-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="72d41-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="72d41-129">Parent Elements</span></span>

|<span data-ttu-id="72d41-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="72d41-130">Element</span></span>|<span data-ttu-id="72d41-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72d41-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72d41-132">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="72d41-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="72d41-133">Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="72d41-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="72d41-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72d41-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="72d41-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="72d41-135">See Also</span></span>

[<span data-ttu-id="72d41-136">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="72d41-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="72d41-137">DisplayError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="72d41-138">EnumerableExpansions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="72d41-139">PropertyCountForTable (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="72d41-140">ShowError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="72d41-141">WrapTables öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="72d41-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="72d41-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="72d41-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
