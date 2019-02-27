---
title: Özel biçimlendirme dosyaları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850039"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="3b7e2-102">Özel Biçimlendirme Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3b7e2-102">Custom Formatting Files</span></span>

<span data-ttu-id="3b7e2-103">Cmdlet'ler, İşlevler ve betikleri tarafından döndürülen nesneler için görüntüleme biçimini, biçimlendirme dosyaları (format.ps1xml) kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="3b7e2-104">Bu dosyaların bazıları, Windows PowerShell cmdlet'leri tarafından döndürülen nesnelere varsayılan görüntülenme biçimini tanımlamak için Windows PowerShell tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="3b7e2-105">Ancak, kendi özel biçimlendirme dosyaları varsayılan görüntü biçimleri üzerine yazmak veya kendi komutları tarafından döndürülen nesne gösterimini tanımlamak için de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="3b7e2-106">Windows PowerShell, görüntülenenler ve verileri nasıl biçimlendirildiğini belirlemek için bu biçimlendirme dosyalarında verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="3b7e2-107">Görüntülenen verileri, bir nesnenin özelliklerini veya bir betik bloğu değerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="3b7e2-108">Bir nesnenin özelliklerinden doğrudan kullanılabilir olmayan bir değer görüntülemek istiyorsanız, komut dosyası blokları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="3b7e2-109">Örneğin, bir nesnenin iki özellik değerini ekleyin ve verileri ayrı bir parçası toplamı görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="3b7e2-110">Kendi biçimlendirme dosya yazdığınızda, tanımlamanız gerekir *görünümleri* görüntülemek istediğiniz nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="3b7e2-111">Tanımlayabileceğiniz her nesne için tek bir görünümde, tek bir görünümde birden çok nesne için tanımlayabileceğiniz veya aynı nesne için birden çok görünüm tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="3b7e2-112">Tanımlayabileceğiniz görünümleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3b7e2-113">Biçimlendirme dosyaları işlem hattının getirilen nesneyi öğelerini belirlemek değil.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="3b7e2-114">Bir nesneyi ardışık düzene döndürüldüğünde, bu nesnenin tüm üyelerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="3b7e2-115">Biçim görünümleri</span><span class="sxs-lookup"><span data-stu-id="3b7e2-115">Format Views</span></span>

<span data-ttu-id="3b7e2-116">Bir tablo biçiminde, bir liste biçiminde, geniş bir biçim ve özel bir biçim, biçimlendirme görünümleri nesneleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="3b7e2-117">Çoğunlukla, her biçimlendirme tanımı bir görünüm açıklayan XML etiketleri kümesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="3b7e2-118">Her görünümü, görünümün adını Görünüm ve Tablo görünümü için sütun ve satır bilgileri gibi görünümün öğeleri kullanan nesneler içerir.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="3b7e2-119">Aşağıdaki görünüm mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-119">The following views are available.</span></span>

<span data-ttu-id="3b7e2-120">Tablo görünümü, bir nesne veya bir betik bloğu değerinde bir veya daha fazla sütun özelliklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="3b7e2-121">Her sütun, nesne veya bir betik bloğu değer özelliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="3b7e2-122">Bir nesne veya özelliklerini ve betik bloğu değerlerini birleşimini özelliklerinin bir alt nesneyi tüm özelliklerini gösteren bir tablo görünümü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="3b7e2-123">Tablodaki her satır, döndürülen nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="3b7e2-124">Bu görünüm hakkında daha fazla bilgi için bkz: [Tablo görünümü](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3b7e2-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="3b7e2-125">Liste görünümü, bir nesne veya bir betik bloğu değeri tek bir sütunda özelliklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="3b7e2-126">Her satır listenin isteğe bağlı bir etiket veya değeri özellik veya betik bloğunun ardından özellik adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="3b7e2-127">Bu görünüm hakkında daha fazla bilgi için bkz: [liste görünümü](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3b7e2-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="3b7e2-128">Tek bir özellik bir nesnenin ya da bir veya daha fazla sütun bir betik bloğu değer geniş görünüm listeler.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="3b7e2-129">Bu görünüm için üst bilgi veya etiket yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-129">There is no label or header for this view.</span></span> <span data-ttu-id="3b7e2-130">Bu görünüm hakkında daha fazla bilgi için bkz: [geniş Görünüm](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3b7e2-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="3b7e2-131">Özel Görünüm katı yapısını tablo görünümleri, liste görünümleri veya geniş görünümleri için belirtime uymuyor özelleştirilebilir bir görünümü nesne özelliklerini veya betik bloğu değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="3b7e2-132">Tablo görünümü veya liste görünümü gibi başka bir görünüm tarafından kullanılan özel bir görünüm tanımlayabilirsiniz veya tek başına özel görünüm tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="3b7e2-133">Bu görünüm hakkında daha fazla bilgi için bkz: [Özel Görünüm](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3b7e2-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="3b7e2-134">Görünüm XML öğeleri</span><span class="sxs-lookup"><span data-stu-id="3b7e2-134">View XML Elements</span></span>

<span data-ttu-id="3b7e2-135">Aşağıdaki örnek, iki sütun içeren bir tablo görünümü tanımlamak için kullanılan XML etiketlerinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="3b7e2-136">[ViewDefinitions](../format/viewdefinitions-element-format.md) öğedir biçimlendirme dosyasında tanımlanan tüm görünümleri için kapsayıcı öğe.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="3b7e2-137">[Görünümü](../format/view-element-format.md) öğe, belirli bir tablo, liste, geniş veya özel görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="3b7e2-138">Her görünümü içinde [adı](../format/name-element-for-view-format.md) öğesi, görünümün adını belirtir [ViewSelectedBy](../format/viewselectedby-element-format.md) öğe tanımlar Görünüm ve farklı denetim öğeleri kullanan nesneler (gibi `TableControl` öğesi) görüntüleme biçimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3b7e2-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="3b7e2-139">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3b7e2-139">See Also</span></span>

[<span data-ttu-id="3b7e2-140">Tablo görünümü</span><span class="sxs-lookup"><span data-stu-id="3b7e2-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="3b7e2-141">Liste Görünümü</span><span class="sxs-lookup"><span data-stu-id="3b7e2-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="3b7e2-142">Geniş Görünüm</span><span class="sxs-lookup"><span data-stu-id="3b7e2-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="3b7e2-143">Özel Görünüm</span><span class="sxs-lookup"><span data-stu-id="3b7e2-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="3b7e2-144">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="3b7e2-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
