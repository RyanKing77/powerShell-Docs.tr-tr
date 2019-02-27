---
title: GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845622"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="a6161-102">GroupBy ExpressionBinding için CustomControlName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a6161-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="a6161-103">Bir ortak denetimi veya bir görünüm denetimi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6161-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="a6161-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6161-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a6161-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) CustomItem öğesinin CustomEntry GroupBy (biçimi) ExpressionBinding öğesinin CustomItem GroupBy (biçimi) CustomControlName öğesinin ExpressionBinding GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="a6161-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6161-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6161-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6161-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6161-107">Attributes and Elements</span></span>

<span data-ttu-id="a6161-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControlName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a6161-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6161-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6161-109">Attributes</span></span>

<span data-ttu-id="a6161-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a6161-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6161-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6161-111">Child Elements</span></span>

<span data-ttu-id="a6161-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a6161-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6161-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6161-113">Parent Elements</span></span>

|<span data-ttu-id="a6161-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6161-114">Element</span></span>|<span data-ttu-id="a6161-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6161-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6161-116">GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="a6161-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="a6161-117">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a6161-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6161-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="a6161-118">Text Value</span></span>

<span data-ttu-id="a6161-119">Denetimin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a6161-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6161-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6161-120">Remarks</span></span>

<span data-ttu-id="a6161-121">Biçimlendirme bir dosyanın tüm görünümler tarafından kullanılabilen ortak denetimleri oluşturabilirsiniz ve belirli bir görünüm tarafından kullanılabilmesi için görünüm denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6161-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="a6161-122">Aşağıdaki öğeler bu denetimlerin adlarını belirtin:</span><span class="sxs-lookup"><span data-stu-id="a6161-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="a6161-123">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="a6161-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="a6161-124">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="a6161-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="a6161-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a6161-125">See Also</span></span>

[<span data-ttu-id="a6161-126">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="a6161-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a6161-127">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="a6161-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a6161-128">GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="a6161-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="a6161-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a6161-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
