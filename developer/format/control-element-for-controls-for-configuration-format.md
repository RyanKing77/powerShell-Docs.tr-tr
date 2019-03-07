---
title: Denetim öğesi için denetimleri için yapılandırma (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848835"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="563b7-102">Yapılandırma Denetimleri için Denetim Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="563b7-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="563b7-103">Biçimlendirme dosya ve denetime başvurmak için kullanılan ad tüm görünümler tarafından kullanılan ortak bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="563b7-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="563b7-104">Yapılandırma öğesi (biçimi) denetimleri öğesi denetimleri yapılandırma (biçimi) için yapılandırma (biçimi) denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="563b7-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="563b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="563b7-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="563b7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="563b7-106">Attributes and Elements</span></span>

<span data-ttu-id="563b7-107">Öznitelikler, alt ve üst öğe için aşağıdaki bölümlerde açıklanmaktadır `Control` öğesi.</span><span class="sxs-lookup"><span data-stu-id="563b7-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="563b7-108">Her alt öğenin yalnızca bir tane belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="563b7-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="563b7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="563b7-109">Attributes</span></span>

<span data-ttu-id="563b7-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="563b7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="563b7-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="563b7-111">Child Elements</span></span>

|<span data-ttu-id="563b7-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="563b7-112">Element</span></span>|<span data-ttu-id="563b7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="563b7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="563b7-114">Özel denetim öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="563b7-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="563b7-115">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="563b7-115">Required element.</span></span><br /><br /> <span data-ttu-id="563b7-116">Denetimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="563b7-116">Defines the control.</span></span>|
|[<span data-ttu-id="563b7-117">Name öğesi denetimi için yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="563b7-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="563b7-118">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="563b7-118">Required element.</span></span><br /><br /> <span data-ttu-id="563b7-119">Denetime başvurmak için kullanılan adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="563b7-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="563b7-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="563b7-120">Parent Elements</span></span>

|<span data-ttu-id="563b7-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="563b7-121">Element</span></span>|<span data-ttu-id="563b7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="563b7-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="563b7-123">Denetim öğesi yapılandırmasının (biçimi)</span><span class="sxs-lookup"><span data-stu-id="563b7-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="563b7-124">Tüm görünümlere biçimlendirme dosyasının veya diğer denetimleri tarafından kullanılabilen ortak denetimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="563b7-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="563b7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="563b7-125">Remarks</span></span>

<span data-ttu-id="563b7-126">Bu denetim için verilen ad, aşağıdaki öğeleri başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="563b7-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="563b7-127">ExpressionBinding öğesi CustomItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="563b7-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="563b7-128">GroupBy öğesi View(Format) için</span><span class="sxs-lookup"><span data-stu-id="563b7-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="563b7-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="563b7-129">See Also</span></span>

[<span data-ttu-id="563b7-130">Denetim öğesi yapılandırmasının (biçimi)</span><span class="sxs-lookup"><span data-stu-id="563b7-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="563b7-131">Özel denetim öğesi denetimi için yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="563b7-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="563b7-132">ExpressionBinding öğesi CustomItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="563b7-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="563b7-133">GroupBy öğesi View(Format) için</span><span class="sxs-lookup"><span data-stu-id="563b7-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="563b7-134">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="563b7-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="563b7-135">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="563b7-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)