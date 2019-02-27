---
title: Ad öğesi denetimi için denetimleri için yapılandırma (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849675"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="2a386-102">Yapılandırma Denetimleri için Denetim Ad Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="2a386-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2a386-103">Denetimin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a386-103">Specifies the name of the control.</span></span> <span data-ttu-id="2a386-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a386-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2a386-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi yapılandırma (biçimi) Name öğesi denetimi için yapılandırma (biçimi) için denetimleri için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="2a386-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a386-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a386-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a386-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a386-107">Attributes and Elements</span></span>

<span data-ttu-id="2a386-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Name` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2a386-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a386-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a386-109">Attributes</span></span>

<span data-ttu-id="2a386-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a386-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a386-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a386-111">Child Elements</span></span>

<span data-ttu-id="2a386-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a386-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a386-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a386-113">Parent Elements</span></span>

|<span data-ttu-id="2a386-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a386-114">Element</span></span>|<span data-ttu-id="2a386-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a386-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a386-116">Yapılandırma (biçimi) için denetimleri için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="2a386-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="2a386-117">Biçimlendirme dosya ve denetime başvurmak için kullanılan ad tüm görünümler tarafından kullanılan ortak bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a386-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2a386-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="2a386-118">Text Value</span></span>

<span data-ttu-id="2a386-119">Bu denetime başvurmak için kullanılan adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="2a386-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a386-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a386-120">Remarks</span></span>

<span data-ttu-id="2a386-121">Burada belirtilen adı aşağıdaki öğeleri, bu denetime başvurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a386-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="2a386-122">Oluştururken bir tablo, liste, geniş veya özel denetimi görünüm denetimi şu öğe tarafından belirtilebilir: [GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2a386-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="2a386-123">Bu denetim, başka bir ortak denetimi oluştururken şu öğe tarafından belirtilebilir: [İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="2a386-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="2a386-124">Denetim oluşturma görünümü tarafından kullanılabilir olduğunda bu denetimi şu öğe tarafından belirtilebilir: [ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2a386-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="2a386-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2a386-125">See Also</span></span>

[<span data-ttu-id="2a386-126">Yapılandırma (biçimi) için denetimleri için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="2a386-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="2a386-127">İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="2a386-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2a386-128">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="2a386-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2a386-129">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2a386-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2a386-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="2a386-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
