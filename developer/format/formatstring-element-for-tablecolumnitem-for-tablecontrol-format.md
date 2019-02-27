---
title: TableControl (biçimi) için TableColumnItem için FormatString öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845643"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="ca412-102">TableControl TableColumnItem için FormatString Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="ca412-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="ca412-103">Tablo özelliği veya komut dosyası değerini nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca412-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="ca412-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) TableColumnItems öğesi (biçimi) TableColumnItem öğesi (biçimi) TableColumnItem (biçimi) için FormatString öğesi</span><span class="sxs-lookup"><span data-stu-id="ca412-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca412-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca412-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca412-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca412-106">Attributes and Elements</span></span>

<span data-ttu-id="ca412-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `FormatString` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ca412-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca412-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca412-108">Attributes</span></span>

<span data-ttu-id="ca412-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca412-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca412-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca412-110">Child Elements</span></span>

<span data-ttu-id="ca412-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca412-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca412-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca412-112">Parent Elements</span></span>

|<span data-ttu-id="ca412-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca412-113">Element</span></span>|<span data-ttu-id="ca412-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca412-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca412-115">TableColumnItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="ca412-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="ca412-116">Özellik veya betik değeri satırın sütunda görüntülenen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca412-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ca412-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="ca412-117">Text Value</span></span>

<span data-ttu-id="ca412-118">Verilerin biçimlendirilmesi için kullanılan desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="ca412-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="ca412-119">Örneğin, bu düzen türü herhangi bir özelliği değerini biçimlendirmek için kullanılabilir [System.Timespan](/dotnet/api/System.TimeSpan): {0: aaa} {0} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="ca412-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca412-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca412-120">Remarks</span></span>

<span data-ttu-id="ca412-121">Tablo görünümleri, liste görünümleri, geniş görünümleri veya özel görünümlerini oluşturma biçim dizeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca412-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="ca412-122">Bir görünümü'nde görüntülenen bir değeri biçimlendirme hakkında daha fazla bilgi için bkz. [görüntülenen verileri biçimlendirme](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="ca412-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="ca412-123">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [Tablo görünümü](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ca412-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ca412-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca412-124">Example</span></span>

<span data-ttu-id="ca412-125">Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca412-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="ca412-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ca412-126">See Also</span></span>

[<span data-ttu-id="ca412-127">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca412-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ca412-128">Görüntülenen veriler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="ca412-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="ca412-129">TableColumnItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="ca412-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="ca412-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="ca412-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
