---
title: CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849920"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="c22ed-102">Görünüm CustomControl için ExpressionBinding CustomControlName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c22ed-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="c22ed-103">Bir ortak denetimi veya bir görünüm denetimi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c22ed-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="c22ed-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c22ed-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c22ed-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) özel denetim öğesi görünümü (biçimi) CustomEntries öğesinin özel denetim için View (biçimi) CustomItem CustomEntries CustomEntry öğesinin görünümü (biçimi) Öğe için CustomEntry CustomItem (biçimi) için ifade bağlama CustomItem (biçimi) CustomControlName öğesinin ExpressionBinding öğesi görünümü (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="c22ed-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c22ed-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c22ed-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c22ed-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c22ed-107">Attributes and Elements</span></span>

<span data-ttu-id="c22ed-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControlName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c22ed-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c22ed-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c22ed-109">Attributes</span></span>

<span data-ttu-id="c22ed-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c22ed-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c22ed-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c22ed-111">Child Elements</span></span>

<span data-ttu-id="c22ed-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c22ed-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c22ed-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c22ed-113">Parent Elements</span></span>

|<span data-ttu-id="c22ed-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c22ed-114">Element</span></span>|<span data-ttu-id="c22ed-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c22ed-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c22ed-116">ExpressionBinding öğesi CustomItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="c22ed-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="c22ed-117">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c22ed-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c22ed-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="c22ed-118">Text Value</span></span>

<span data-ttu-id="c22ed-119">Denetimin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="c22ed-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c22ed-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c22ed-120">Remarks</span></span>

<span data-ttu-id="c22ed-121">Biçimlendirme bir dosyanın tüm görünümler tarafından kullanılabilen ortak denetimleri oluşturabilirsiniz ve belirli bir görünüm tarafından kullanılabilmesi için görünüm denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c22ed-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="c22ed-122">Bu denetimlerin adlarını aşağıdaki öğeleri tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c22ed-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="c22ed-123">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="c22ed-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="c22ed-124">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="c22ed-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="c22ed-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c22ed-125">See Also</span></span>

[<span data-ttu-id="c22ed-126">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="c22ed-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="c22ed-127">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="c22ed-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c22ed-128">ExpressionBinding öğesi CustomItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="c22ed-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="c22ed-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c22ed-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)