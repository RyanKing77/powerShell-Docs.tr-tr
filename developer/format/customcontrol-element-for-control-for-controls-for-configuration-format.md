---
title: Özel denetim öğesi denetimi için yapılandırma (biçimi) için denetimleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066745"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="3c07a-102">Yapılandırma Denetimleri için Denetim CustomControl Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="3c07a-102">CustomControl Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3c07a-103">Bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c07a-103">Defines a control.</span></span> <span data-ttu-id="3c07a-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c07a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3c07a-105">Yapılandırma öğesi (biçimi) denetimleri öğesi denetimler için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) için yapılandırma (biçimi) denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="3c07a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c07a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c07a-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c07a-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3c07a-107">Attributes and Elements</span></span>

<span data-ttu-id="3c07a-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `CustomControl` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3c07a-108">The following sections describe the attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="3c07a-109">Bu öğe en az bir alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c07a-109">This element must have at least one child element.</span></span> <span data-ttu-id="3c07a-110">Hiçbir belirtilebilir alt öğe sayısı üst sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="3c07a-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c07a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c07a-111">Attributes</span></span>

<span data-ttu-id="3c07a-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c07a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c07a-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3c07a-113">Child Elements</span></span>

|<span data-ttu-id="3c07a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c07a-114">Element</span></span>|<span data-ttu-id="3c07a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c07a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c07a-116">Yapılandırma (biçimi) için özel denetim için CustomEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="3c07a-116">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="3c07a-117">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="3c07a-117">Required element.</span></span><br /><br /> <span data-ttu-id="3c07a-118">Bir denetim tanımlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c07a-118">Provides the definitions of a control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c07a-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3c07a-119">Parent Elements</span></span>

|<span data-ttu-id="3c07a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c07a-120">Element</span></span>|<span data-ttu-id="3c07a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c07a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c07a-122">Yapılandırma (biçimi) için denetimleri için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="3c07a-122">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="3c07a-123">Biçimlendirme dosya ve denetime başvurmak için kullanılan ad tüm görünümler tarafından kullanılan ortak bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c07a-123">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c07a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c07a-124">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3c07a-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3c07a-125">See Also</span></span>

[<span data-ttu-id="3c07a-126">Yapılandırma (biçimi) için denetimleri için Denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="3c07a-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="3c07a-127">Yapılandırma (biçimi) için özel denetim için CustomEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="3c07a-127">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="3c07a-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="3c07a-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
