---
title: WideItem WideControl (biçimi) için için FormatString öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065691"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="f029d-102">WideControl WideItem için FormatString Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f029d-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="f029d-103">Özellik veya betik değeri Görünümü'nde nasıl görüntüleneceğini tanımlayan bir biçim deseni belirtir.</span><span class="sxs-lookup"><span data-stu-id="f029d-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="f029d-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi WideControl (biçimi) FormatString öğesi WideItem öğesinin WideControl (biçimi) için WideItem WideControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f029d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f029d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f029d-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f029d-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f029d-106">Attributes and Elements</span></span>

<span data-ttu-id="f029d-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `FormatString` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f029d-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f029d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f029d-108">Attributes</span></span>

<span data-ttu-id="f029d-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="f029d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f029d-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f029d-110">Child Elements</span></span>

<span data-ttu-id="f029d-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f029d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f029d-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f029d-112">Parent Elements</span></span>

|<span data-ttu-id="f029d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f029d-113">Element</span></span>|<span data-ttu-id="f029d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f029d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f029d-115">WideItem öğesi WideControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f029d-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="f029d-116">Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f029d-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f029d-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="f029d-117">Text Value</span></span>

<span data-ttu-id="f029d-118">Verilerin biçimlendirilmesi için kullanılan desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="f029d-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="f029d-119">Örneğin, türünde herhangi bir özelliği değerini biçimlendirmek için bu düzeni kullanabilirsiniz [System.Timespan](/dotnet/api/System.TimeSpan): {0: aaa} {0} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="f029d-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="f029d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f029d-120">Remarks</span></span>

<span data-ttu-id="f029d-121">Tablo görünümleri, liste görünümleri, geniş görünümleri veya özel görünümlerini oluşturma biçim dizeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f029d-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="f029d-122">Bir görünümü'nde görüntülenen bir değeri biçimlendirme hakkında daha fazla bilgi için bkz. [görüntülenen verileri biçimlendirme](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="f029d-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="f029d-123">Geniş görünümlerde biçim dizeleri kullanma hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f029d-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f029d-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f029d-124">Example</span></span>

<span data-ttu-id="f029d-125">Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.</span><span class="sxs-lookup"><span data-stu-id="f029d-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="f029d-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f029d-126">See Also</span></span>

[<span data-ttu-id="f029d-127">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="f029d-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f029d-128">WideItem öğesi WideControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f029d-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="f029d-129">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="f029d-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
