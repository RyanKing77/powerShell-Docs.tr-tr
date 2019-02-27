---
title: PropertyName öğesi WideItem WideControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850284"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="d7297-102">WideControl WideItem için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="d7297-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="d7297-103">Özellik değeri geniş görünümünde görüntülenen nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7297-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="d7297-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) WideItem öğesi (biçimi) PropertyName öğesi WideItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="d7297-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7297-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7297-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7297-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7297-106">Attributes and Elements</span></span>

<span data-ttu-id="d7297-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7297-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7297-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d7297-108">Attributes</span></span>

<span data-ttu-id="d7297-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7297-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7297-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7297-110">Child Elements</span></span>

<span data-ttu-id="d7297-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7297-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7297-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7297-112">Parent Elements</span></span>

|<span data-ttu-id="d7297-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d7297-113">Element</span></span>|<span data-ttu-id="d7297-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7297-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7297-115">WideItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="d7297-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="d7297-116">Özellik veya betik değeri geniş görünümünde görüntülenen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d7297-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d7297-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="d7297-117">Text Value</span></span>

<span data-ttu-id="d7297-118">Özellik değeri görüntülenen adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d7297-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7297-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7297-119">Remarks</span></span>

<span data-ttu-id="d7297-120">Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d7297-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d7297-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7297-121">Example</span></span>

<span data-ttu-id="d7297-122">Bu örnek, ProcessName özelliğinin değerini görüntüler geniş bir görünüm gösterir [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="d7297-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="d7297-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d7297-123">See Also</span></span>

[<span data-ttu-id="d7297-124">WideItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="d7297-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="d7297-125">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7297-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d7297-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="d7297-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
