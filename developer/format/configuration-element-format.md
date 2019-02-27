---
title: Yapılandırma öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847043"
---
# <a name="configuration-element-format"></a><span data-ttu-id="11a93-102">Yapılandırma Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="11a93-102">Configuration Element (Format)</span></span>

<span data-ttu-id="11a93-103">Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11a93-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="11a93-104">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="11a93-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="11a93-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11a93-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="11a93-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="11a93-106">Attributes and Elements</span></span>

<span data-ttu-id="11a93-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Configuration` öğesi.</span><span class="sxs-lookup"><span data-stu-id="11a93-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="11a93-108">Bu öğe biçimlendirme her dosya için kök öğesi olmalıdır ve bu öğe en az bir alt öğe içermelidir.</span><span class="sxs-lookup"><span data-stu-id="11a93-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11a93-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11a93-109">Attributes</span></span>

<span data-ttu-id="11a93-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="11a93-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11a93-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="11a93-111">Child Elements</span></span>

|<span data-ttu-id="11a93-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="11a93-112">Element</span></span>|<span data-ttu-id="11a93-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11a93-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11a93-114">Yapılandırma (biçimi) için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="11a93-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="11a93-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="11a93-115">Optional element.</span></span><br /><br /> <span data-ttu-id="11a93-116">Tüm biçimlendirme dosya görünümler tarafından kullanılabilen ortak denetimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11a93-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="11a93-117">DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="11a93-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="11a93-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="11a93-118">Optional element.</span></span><br /><br /> <span data-ttu-id="11a93-119">Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11a93-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="11a93-120">SelectionSets öğesi biçimi</span><span class="sxs-lookup"><span data-stu-id="11a93-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="11a93-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="11a93-121">Optional element.</span></span><br /><br /> <span data-ttu-id="11a93-122">Biçimlendirme dosyanın tüm görünümler tarafından kullanılan .NET nesneleri ortak kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11a93-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="11a93-123">ViewDefinitions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="11a93-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="11a93-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="11a93-124">Optional element.</span></span><br /><br /> <span data-ttu-id="11a93-125">Nesneleri görüntülemek için kullanılan görünümleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11a93-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="11a93-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="11a93-126">Parent Elements</span></span>

<span data-ttu-id="11a93-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="11a93-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="11a93-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11a93-128">Remarks</span></span>

<span data-ttu-id="11a93-129">Biçimlendirme dosyaları nesnelerin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11a93-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="11a93-130">Çoğu durumda, bu kök öğesi içeren bir [ViewDefinitions](./viewdefinitions-element-format.md) tablo, liste ve biçimlendirme dosyanın geniş görünümleri tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="11a93-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="11a93-131">Görünüm tanımları ek olarak, biçimlendirme dosyası ortak seçimi ayarlar, ayarları ve bu görünümleri kullanabileceğiniz denetimler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a93-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="11a93-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="11a93-132">See Also</span></span>

[<span data-ttu-id="11a93-133">Yapılandırma (biçimi) için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="11a93-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="11a93-134">DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="11a93-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="11a93-135">SelectionSets öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="11a93-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="11a93-136">ViewDefinitions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="11a93-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="11a93-137">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="11a93-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
