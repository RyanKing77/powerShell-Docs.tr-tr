---
title: Özel denetim öğesi görünümü (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066677"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="01315-102">Görünüm için CustomControl Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="01315-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="01315-103">Görünüm için bir özel denetim biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01315-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="01315-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="01315-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="01315-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01315-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01315-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="01315-106">Attributes and Elements</span></span>

<span data-ttu-id="01315-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControl` öğesi.</span><span class="sxs-lookup"><span data-stu-id="01315-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="01315-108">Bir alt öğe belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="01315-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="01315-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01315-109">Attributes</span></span>

<span data-ttu-id="01315-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="01315-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="01315-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="01315-111">Child Elements</span></span>

|<span data-ttu-id="01315-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="01315-112">Element</span></span>|<span data-ttu-id="01315-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01315-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01315-114">CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="01315-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="01315-115">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="01315-115">Required element.</span></span><br /><br /> <span data-ttu-id="01315-116">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="01315-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="01315-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="01315-117">Parent Elements</span></span>

|<span data-ttu-id="01315-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="01315-118">Element</span></span>|<span data-ttu-id="01315-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01315-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01315-120">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="01315-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="01315-121">Bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01315-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01315-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01315-122">Remarks</span></span>

<span data-ttu-id="01315-123">Çoğu durumda, yalnızca bir tanımı için her denetim görünüm gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı görünümde kullanmak istiyorsanız birden çok tanım sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="01315-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="01315-124">Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="01315-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="01315-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="01315-125">See Also</span></span>

[<span data-ttu-id="01315-126">CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="01315-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="01315-127">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="01315-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="01315-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="01315-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
