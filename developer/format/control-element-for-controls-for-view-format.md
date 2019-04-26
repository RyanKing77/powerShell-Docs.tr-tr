---
title: Denetim öğesi denetimleri için görüntüleme (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066779"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="432bb-102">Görünüm Denetimleri için Denetim Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="432bb-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="432bb-103">Görünüm ve denetimin başvurmak için kullanılan ad tarafından kullanılabilecek bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="432bb-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="432bb-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) öğesi (biçimi) denetim öğesi denetimleri için görüntüleme (biçimi) için denetler.</span><span class="sxs-lookup"><span data-stu-id="432bb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="432bb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="432bb-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="432bb-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="432bb-106">Attributes and Elements</span></span>

<span data-ttu-id="432bb-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Control` öğesi.</span><span class="sxs-lookup"><span data-stu-id="432bb-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="432bb-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="432bb-108">Attributes</span></span>

<span data-ttu-id="432bb-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="432bb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="432bb-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="432bb-110">Child Elements</span></span>

|<span data-ttu-id="432bb-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="432bb-111">Element</span></span>|<span data-ttu-id="432bb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="432bb-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="432bb-113">Name öğesi denetimi için Görünüm (biçimi)</span><span class="sxs-lookup"><span data-stu-id="432bb-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="432bb-114">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="432bb-114">Required element.</span></span><br /><br /> <span data-ttu-id="432bb-115">Denetimin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="432bb-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="432bb-116">Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="432bb-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="432bb-117">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="432bb-117">Required element.</span></span><br /><br /> <span data-ttu-id="432bb-118">Bu görünüm tarafından kullanılan denetimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="432bb-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="432bb-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="432bb-119">Parent Elements</span></span>

|<span data-ttu-id="432bb-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="432bb-120">Element</span></span>|<span data-ttu-id="432bb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="432bb-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="432bb-122">Denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="432bb-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="432bb-123">Belirli bir görünüm tarafından kullanılabilen görünüm denetimlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="432bb-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="432bb-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="432bb-124">Remarks</span></span>

<span data-ttu-id="432bb-125">Bu denetim, şu öğeler tarafından belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="432bb-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="432bb-126">CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="432bb-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="432bb-127">CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="432bb-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="432bb-128">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="432bb-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="432bb-129">GroupBy (biçimi) için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="432bb-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="432bb-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="432bb-130">See Also</span></span>

[<span data-ttu-id="432bb-131">Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="432bb-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="432bb-132">CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="432bb-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="432bb-133">CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="432bb-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="432bb-134">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="432bb-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="432bb-135">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="432bb-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="432bb-136">Denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="432bb-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="432bb-137">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="432bb-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="432bb-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="432bb-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
