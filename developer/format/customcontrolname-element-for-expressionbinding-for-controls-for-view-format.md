---
title: CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066660"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="62360-102">Görünüm Denetimleri için ExpressionBinding CustomControlName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="62360-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="62360-103">Bir ortak denetimi veya bir görünüm denetimi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62360-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="62360-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62360-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="62360-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry CustomItem görünümü (biçimi) CustomControlName denetimleri için görüntüleme (biçimi) ExpressionBinding öğesinin denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi) Öğesi görünümü (biçimi) için denetimleri için ExpressionBindine için</span><span class="sxs-lookup"><span data-stu-id="62360-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62360-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62360-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62360-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="62360-107">Attributes and Elements</span></span>

<span data-ttu-id="62360-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControlName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="62360-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62360-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62360-109">Attributes</span></span>

<span data-ttu-id="62360-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="62360-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62360-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="62360-111">Child Elements</span></span>

<span data-ttu-id="62360-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="62360-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="62360-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="62360-113">Parent Elements</span></span>

|<span data-ttu-id="62360-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="62360-114">Element</span></span>|<span data-ttu-id="62360-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62360-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62360-116">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="62360-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="62360-117">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62360-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="62360-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="62360-118">Text Value</span></span>

<span data-ttu-id="62360-119">Denetimin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="62360-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="62360-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62360-120">Remarks</span></span>

<span data-ttu-id="62360-121">Biçimlendirme bir dosyanın tüm görünümler tarafından kullanılabilen ortak denetimleri oluşturabilirsiniz ve belirli bir görünüm tarafından kullanılabilmesi için görünüm denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62360-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="62360-122">Aşağıdaki öğeler bu denetimlerin adlarını belirtin:</span><span class="sxs-lookup"><span data-stu-id="62360-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="62360-123">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="62360-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="62360-124">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="62360-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="62360-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="62360-125">See Also</span></span>

[<span data-ttu-id="62360-126">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="62360-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="62360-127">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="62360-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="62360-128">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="62360-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="62360-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="62360-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
