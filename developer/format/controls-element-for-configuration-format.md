---
title: (Biçimi) için yapılandırma öğesi denetimlerini | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066881"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="3d308-102">Yapılandırma için Denetimler Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="3d308-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="3d308-103">Tüm biçimlendirme dosya görünümler tarafından kullanılabilen ortak denetimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3d308-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="3d308-104">Yapılandırma öğesi (biçimi) denetimleri öğesi yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3d308-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d308-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d308-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d308-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3d308-106">Attributes and Elements</span></span>

<span data-ttu-id="3d308-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Controls` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3d308-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d308-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d308-108">Attributes</span></span>

<span data-ttu-id="3d308-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="3d308-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d308-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3d308-110">Child Elements</span></span>

|<span data-ttu-id="3d308-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="3d308-111">Element</span></span>|<span data-ttu-id="3d308-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d308-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d308-113">Yapılandırma (biçimi) için denetimleri için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="3d308-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="3d308-114">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="3d308-114">Required element.</span></span><br /><br /> <span data-ttu-id="3d308-115">Tüm biçimlendirme dosya görünümler tarafından kullanılan ortak bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3d308-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d308-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3d308-116">Parent Elements</span></span>

|<span data-ttu-id="3d308-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3d308-117">Element</span></span>|<span data-ttu-id="3d308-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d308-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d308-119">Yapılandırma öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3d308-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="3d308-120">Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d308-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d308-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d308-121">Remarks</span></span>

<span data-ttu-id="3d308-122">Herhangi bir sayıda ortak denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d308-122">You can create any number of common controls.</span></span> <span data-ttu-id="3d308-123">Her denetim için Denetim ve denetim bileşenlerinin başvurmak için kullanılan adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d308-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d308-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3d308-124">See Also</span></span>

[<span data-ttu-id="3d308-125">Yapılandırma öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3d308-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="3d308-126">Yapılandırma (biçimi) için denetimleri için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="3d308-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="3d308-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="3d308-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
