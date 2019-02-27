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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845223"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="dc1ee-102">Görünüm Denetimleri için Denetim Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="dc1ee-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="dc1ee-103">Görünüm ve denetimin başvurmak için kullanılan ad tarafından kullanılabilecek bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="dc1ee-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) öğesi (biçimi) denetim öğesi denetimleri için görüntüleme (biçimi) için denetler.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc1ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc1ee-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc1ee-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc1ee-106">Attributes and Elements</span></span>

<span data-ttu-id="dc1ee-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Control` öğesi.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc1ee-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dc1ee-108">Attributes</span></span>

<span data-ttu-id="dc1ee-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc1ee-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc1ee-110">Child Elements</span></span>

|<span data-ttu-id="dc1ee-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="dc1ee-111">Element</span></span>|<span data-ttu-id="dc1ee-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc1ee-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc1ee-113">Name öğesi denetimi için Görünüm (biçimi)</span><span class="sxs-lookup"><span data-stu-id="dc1ee-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="dc1ee-114">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-114">Required element.</span></span><br /><br /> <span data-ttu-id="dc1ee-115">Denetimin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="dc1ee-116">Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="dc1ee-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="dc1ee-117">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-117">Required element.</span></span><br /><br /> <span data-ttu-id="dc1ee-118">Bu görünüm tarafından kullanılan denetimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dc1ee-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc1ee-119">Parent Elements</span></span>

|<span data-ttu-id="dc1ee-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="dc1ee-120">Element</span></span>|<span data-ttu-id="dc1ee-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc1ee-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc1ee-122">Denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="dc1ee-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="dc1ee-123">Belirli bir görünüm tarafından kullanılabilen görünüm denetimlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc1ee-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dc1ee-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc1ee-124">Remarks</span></span>

<span data-ttu-id="dc1ee-125">Bu denetim, şu öğeler tarafından belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="dc1ee-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="dc1ee-126">CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="dc1ee-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="dc1ee-127">CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="dc1ee-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="dc1ee-128">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="dc1ee-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="dc1ee-129">GroupBy (biçimi) için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="dc1ee-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="dc1ee-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="dc1ee-130">See Also</span></span>

[<span data-ttu-id="dc1ee-131">Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="dc1ee-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="dc1ee-132">CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="dc1ee-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="dc1ee-133">CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="dc1ee-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="dc1ee-134">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="dc1ee-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dc1ee-135">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="dc1ee-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dc1ee-136">Denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="dc1ee-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="dc1ee-137">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="dc1ee-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="dc1ee-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="dc1ee-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
