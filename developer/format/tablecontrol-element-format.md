---
title: TableControl öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063841"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="74db6-102">TableControl Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="74db6-102">TableControl Element (Format)</span></span>

<span data-ttu-id="74db6-103">Bir görünüm için bir tablo biçiminde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74db6-103">Defines a table format for a view.</span></span>

<span data-ttu-id="74db6-104">ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74db6-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74db6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74db6-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="74db6-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="74db6-106">Attributes and Elements</span></span>

<span data-ttu-id="74db6-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableControl` öğesi.</span><span class="sxs-lookup"><span data-stu-id="74db6-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="74db6-108">Tablonun satırlarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="74db6-108">You must specify the rows of the table.</span></span> <span data-ttu-id="74db6-109">Diğer tüm alt öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="74db6-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="74db6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74db6-110">Attributes</span></span>

<span data-ttu-id="74db6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="74db6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74db6-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="74db6-112">Child Elements</span></span>

|<span data-ttu-id="74db6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="74db6-113">Element</span></span>|<span data-ttu-id="74db6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74db6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74db6-115">TableControl (biçimi) için AutoSize öğesi</span><span class="sxs-lookup"><span data-stu-id="74db6-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="74db6-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="74db6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="74db6-117">Sütun boyutu ve sütun sayısı verilerin boyutuna bağlı olarak ayarlanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="74db6-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="74db6-118">TableControl (biçimi) için HideTableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="74db6-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="74db6-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="74db6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="74db6-120">Tablo üstbilgisinin değil görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="74db6-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="74db6-121">TableControl (biçimi) için TableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="74db6-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="74db6-122">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="74db6-122">Required element.</span></span><br /><br /> <span data-ttu-id="74db6-123">Etiketler, genişliğini ve Tablo görünümünde sütunları için veri hizalaması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74db6-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="74db6-124">TableControl (biçimi) için TableRowEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="74db6-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="74db6-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="74db6-125">Optional element.</span></span><br /><br /> <span data-ttu-id="74db6-126">Tablo görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="74db6-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="74db6-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="74db6-127">Parent Elements</span></span>

|<span data-ttu-id="74db6-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="74db6-128">Element</span></span>|<span data-ttu-id="74db6-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74db6-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74db6-130">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74db6-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="74db6-131">Bir veya daha fazla nesne üyeleri görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74db6-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="74db6-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74db6-132">Remarks</span></span>

<span data-ttu-id="74db6-133">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="74db6-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="74db6-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="74db6-134">Example</span></span>

<span data-ttu-id="74db6-135">Bu örnek gösterir bir `TableControl` özelliklerini görüntülemek için kullanılan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="74db6-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="74db6-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="74db6-136">See Also</span></span>

[<span data-ttu-id="74db6-137">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74db6-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="74db6-138">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74db6-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="74db6-139">TableControl (biçimi) için AutoSize öğesi</span><span class="sxs-lookup"><span data-stu-id="74db6-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="74db6-140">HideTableHeaders öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74db6-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="74db6-141">TableHeaders öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74db6-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="74db6-142">TableRowEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74db6-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="74db6-143">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="74db6-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
