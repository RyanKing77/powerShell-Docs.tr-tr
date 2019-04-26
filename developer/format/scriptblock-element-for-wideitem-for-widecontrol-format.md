---
title: ScriptBlock öğesi WideItem WideControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064212"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="10cca-102">WideControl WideItem için ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="10cca-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="10cca-103">Değeri, geniş görünümde görüntülenir betiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10cca-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="10cca-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) WideItem öğesi (biçimi) ScriptBlock öğesi WideItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="10cca-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10cca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10cca-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10cca-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="10cca-106">Attributes and Elements</span></span>

<span data-ttu-id="10cca-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="10cca-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="10cca-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10cca-108">Attributes</span></span>

<span data-ttu-id="10cca-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="10cca-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10cca-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="10cca-110">Child Elements</span></span>

<span data-ttu-id="10cca-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="10cca-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10cca-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="10cca-112">Parent Elements</span></span>

|<span data-ttu-id="10cca-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="10cca-113">Element</span></span>|<span data-ttu-id="10cca-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10cca-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10cca-115">WideItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="10cca-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="10cca-116">Değeri, geniş görünümde görüntülenir özelliği veya betik bloğu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10cca-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="10cca-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="10cca-117">Text Value</span></span>

<span data-ttu-id="10cca-118">Değeri görüntülenen komut dosyasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="10cca-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="10cca-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10cca-119">Remarks</span></span>

<span data-ttu-id="10cca-120">Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="10cca-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="10cca-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="10cca-121">Example</span></span>

<span data-ttu-id="10cca-122">Bu örnek gösterir bir `WideItem` değeri görünümünde görüntülenen bir komut dosyası tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="10cca-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="10cca-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="10cca-123">See Also</span></span>

[<span data-ttu-id="10cca-124">WideItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="10cca-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="10cca-125">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="10cca-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="10cca-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="10cca-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
