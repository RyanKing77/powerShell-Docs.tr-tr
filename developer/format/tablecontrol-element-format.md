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
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848856"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="0ca1a-102">TableControl Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="0ca1a-102">TableControl Element (Format)</span></span>

<span data-ttu-id="0ca1a-103">Bir görünüm için bir tablo biçiminde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-103">Defines a table format for a view.</span></span>

<span data-ttu-id="0ca1a-104">ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0ca1a-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ca1a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ca1a-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ca1a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ca1a-106">Attributes and Elements</span></span>

<span data-ttu-id="0ca1a-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableControl` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="0ca1a-108">Tablonun satırlarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-108">You must specify the rows of the table.</span></span> <span data-ttu-id="0ca1a-109">Diğer tüm alt öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ca1a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ca1a-110">Attributes</span></span>

<span data-ttu-id="0ca1a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ca1a-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ca1a-112">Child Elements</span></span>

|<span data-ttu-id="0ca1a-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ca1a-113">Element</span></span>|<span data-ttu-id="0ca1a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ca1a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ca1a-115">TableControl (biçimi) için AutoSize öğesi</span><span class="sxs-lookup"><span data-stu-id="0ca1a-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="0ca1a-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0ca1a-117">Sütun boyutu ve sütun sayısı verilerin boyutuna bağlı olarak ayarlanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="0ca1a-118">TableControl (biçimi) için HideTableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="0ca1a-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="0ca1a-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0ca1a-120">Tablo üstbilgisinin değil görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="0ca1a-121">TableControl (biçimi) için TableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="0ca1a-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="0ca1a-122">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-122">Required element.</span></span><br /><br /> <span data-ttu-id="0ca1a-123">Etiketler, genişliğini ve Tablo görünümünde sütunları için veri hizalaması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="0ca1a-124">TableRowEntries öğesi TableCotrol (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="0ca1a-124">TableRowEntries Element for TableCotrol (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="0ca1a-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0ca1a-126">Tablo görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ca1a-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ca1a-127">Parent Elements</span></span>

|<span data-ttu-id="0ca1a-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ca1a-128">Element</span></span>|<span data-ttu-id="0ca1a-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ca1a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ca1a-130">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0ca1a-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="0ca1a-131">Bir veya daha fazla nesne üyeleri görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ca1a-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ca1a-132">Remarks</span></span>

<span data-ttu-id="0ca1a-133">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0ca1a-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ca1a-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ca1a-134">Example</span></span>

<span data-ttu-id="0ca1a-135">Bu örnek gösterir bir `TableControl` özelliklerini görüntülemek için kullanılan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="0ca1a-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0ca1a-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0ca1a-136">See Also</span></span>

[<span data-ttu-id="0ca1a-137">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ca1a-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0ca1a-138">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0ca1a-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="0ca1a-139">TableControl (biçimi) için AutoSize öğesi</span><span class="sxs-lookup"><span data-stu-id="0ca1a-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="0ca1a-140">HideTableHeaders öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0ca1a-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="0ca1a-141">TableHeaders öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0ca1a-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="0ca1a-142">TableRowEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0ca1a-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="0ca1a-143">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="0ca1a-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)