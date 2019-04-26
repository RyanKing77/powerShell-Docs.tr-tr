---
title: ListItem ListControl (biçimi) için için FormatString öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065636"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="352fc-102">ListControl ListItem için FormatString Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="352fc-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="352fc-103">Özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="352fc-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="352fc-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) ListEntry öğesinin ListControl (biçimi) ListItems öğesinin ListControl (biçimi) LISTITEM öğesinin ListItem ListControl (biçimi) için FormatString öğesinin ListControl (biçimi)</span><span class="sxs-lookup"><span data-stu-id="352fc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="352fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="352fc-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="352fc-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="352fc-106">Attributes and Elements</span></span>

<span data-ttu-id="352fc-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `FormatString` öğesi.</span><span class="sxs-lookup"><span data-stu-id="352fc-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="352fc-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="352fc-108">Attributes</span></span>

<span data-ttu-id="352fc-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="352fc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="352fc-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="352fc-110">Child Elements</span></span>

<span data-ttu-id="352fc-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="352fc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="352fc-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="352fc-112">Parent Elements</span></span>

|<span data-ttu-id="352fc-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="352fc-113">Element</span></span>|<span data-ttu-id="352fc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="352fc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="352fc-115">LISTITEM öğesinin (biçimi)</span><span class="sxs-lookup"><span data-stu-id="352fc-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="352fc-116">Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="352fc-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="352fc-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="352fc-117">Text Value</span></span>

<span data-ttu-id="352fc-118">Verilerin biçimlendirilmesi için kullanılan desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="352fc-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="352fc-119">Örneğin, türünde herhangi bir özelliği değerini biçimlendirmek için bu düzeni kullanabilirsiniz [System.Timespan](/dotnet/api/System.TimeSpan): {0: aaa} {0} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="352fc-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="352fc-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="352fc-120">Remarks</span></span>

<span data-ttu-id="352fc-121">Tablo görünümleri, liste görünümleri, geniş görünümleri veya özel görünümlerini oluşturma biçim dizeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="352fc-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="352fc-122">Bir görünümü'nde görüntülenen bir değeri biçimlendirme hakkında daha fazla bilgi için bkz. [görüntülenen verileri biçimlendirme](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="352fc-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="352fc-123">Liste görünümlerinde biçim dizeleri kullanma hakkında daha fazla bilgi için bkz. [liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="352fc-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="352fc-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="352fc-124">Example</span></span>

<span data-ttu-id="352fc-125">Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.</span><span class="sxs-lookup"><span data-stu-id="352fc-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="352fc-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="352fc-126">See Also</span></span>

[<span data-ttu-id="352fc-127">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="352fc-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="352fc-128">LISTITEM öğesinin (biçimi)</span><span class="sxs-lookup"><span data-stu-id="352fc-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="352fc-129">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="352fc-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
