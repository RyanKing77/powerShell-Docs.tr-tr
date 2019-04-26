---
title: Ad öğesi denetimi için denetimler için görünümü için (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065113"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="55ade-102">Görünüm Denetimleri için Denetim Ad Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="55ade-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="55ade-103">Denetimin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55ade-103">Specifies the name of the control.</span></span>

<span data-ttu-id="55ade-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) öğesi (biçimi) denetim öğesi için denetimleri için Name öğesi görünümü (biçimi) denetimi için görünümü (biçimi) için denetler</span><span class="sxs-lookup"><span data-stu-id="55ade-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55ade-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55ade-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55ade-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="55ade-106">Attributes and Elements</span></span>

<span data-ttu-id="55ade-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Name` öğesi.</span><span class="sxs-lookup"><span data-stu-id="55ade-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55ade-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55ade-108">Attributes</span></span>

<span data-ttu-id="55ade-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="55ade-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55ade-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="55ade-110">Child Elements</span></span>

<span data-ttu-id="55ade-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="55ade-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55ade-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="55ade-112">Parent Elements</span></span>

|<span data-ttu-id="55ade-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="55ade-113">Element</span></span>|<span data-ttu-id="55ade-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55ade-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55ade-115">Denetim öğesi görünümü (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="55ade-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="55ade-116">Görünüm ve denetimin başvurmak için kullanılan ad tarafından kullanılabilecek bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55ade-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55ade-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="55ade-117">Text Value</span></span>

<span data-ttu-id="55ade-118">Denetime başvurmak için kullanılan adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="55ade-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="55ade-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55ade-119">Remarks</span></span>

<span data-ttu-id="55ade-120">Burada belirtilen adı aşağıdaki öğeleri, bu denetime başvurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55ade-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="55ade-121">Oluştururken bir tablo, liste, geniş veya özel denetimi görünüm denetimi şu öğe tarafından belirtilebilir: [GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="55ade-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="55ade-122">Başka bir denetim oluşturma görünümü tarafından kullanılabilir olduğunda bu denetimi şu öğe tarafından belirtilebilir: [ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="55ade-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="55ade-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="55ade-123">See Also</span></span>

[<span data-ttu-id="55ade-124">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="55ade-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="55ade-125">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="55ade-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="55ade-126">Denetim öğesi görünümü (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="55ade-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="55ade-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="55ade-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
