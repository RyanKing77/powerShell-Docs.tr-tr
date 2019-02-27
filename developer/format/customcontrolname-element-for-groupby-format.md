---
title: GroupBy (biçimi) için CustomControlName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849829"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="1dfe9-102">GroupBy için CustomControlName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="1dfe9-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="1dfe9-103">Yeni grubunu görüntülemek için kullanılan özel bir denetimin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="1dfe9-104">Bu öğe, bir tablo, liste, geniş veya özel denetimi görünüm tanımlarken, kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="1dfe9-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) CustomControlName GroupBy (biçimde) bir öğe için</span><span class="sxs-lookup"><span data-stu-id="1dfe9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1dfe9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dfe9-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1dfe9-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dfe9-107">Attributes and Elements</span></span>

<span data-ttu-id="1dfe9-108">Aşağıdaki bölümlerde, öznitelikler, alt ve üst öğeleri açıklayan `CustomControlName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1dfe9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1dfe9-109">Attributes</span></span>

<span data-ttu-id="1dfe9-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1dfe9-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dfe9-111">Child Elements</span></span>

<span data-ttu-id="1dfe9-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1dfe9-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dfe9-113">Parent Elements</span></span>

|<span data-ttu-id="1dfe9-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1dfe9-114">Element</span></span>|<span data-ttu-id="1dfe9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dfe9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1dfe9-116">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="1dfe9-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="1dfe9-117">Windows PowerShell yeni bir grup nesnelerin biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1dfe9-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="1dfe9-118">Text Value</span></span>

<span data-ttu-id="1dfe9-119">Yeni bir grup görüntülemek için kullanılan özel denetimin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="1dfe9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dfe9-120">Remarks</span></span>

<span data-ttu-id="1dfe9-121">Biçimlendirme bir dosyanın tüm görünümler tarafından kullanılabilen ortak denetimleri oluşturabilirsiniz ve belirli bir görünüm tarafından kullanılabilmesi için görünüm denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1dfe9-122">Aşağıdaki öğeler bu özel denetimlerin adlarını belirtin:</span><span class="sxs-lookup"><span data-stu-id="1dfe9-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="1dfe9-123">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="1dfe9-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1dfe9-124">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="1dfe9-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1dfe9-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1dfe9-125">See Also</span></span>

[<span data-ttu-id="1dfe9-126">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="1dfe9-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="1dfe9-127">Name öğesi denetimi için yapılandırma (biçimi) için denetimler</span><span class="sxs-lookup"><span data-stu-id="1dfe9-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1dfe9-128">Name öğesi denetimi için Görünüm (biçimi) için denetimleri</span><span class="sxs-lookup"><span data-stu-id="1dfe9-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1dfe9-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="1dfe9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
