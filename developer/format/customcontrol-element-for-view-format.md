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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850494"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="2bb78-102">Görünüm için CustomControl Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="2bb78-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="2bb78-103">Görünüm için bir özel denetim biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="2bb78-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2bb78-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2bb78-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bb78-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bb78-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bb78-106">Attributes and Elements</span></span>

<span data-ttu-id="2bb78-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControl` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2bb78-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="2bb78-108">Bir alt öğe belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bb78-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2bb78-109">Attributes</span></span>

<span data-ttu-id="2bb78-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="2bb78-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2bb78-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bb78-111">Child Elements</span></span>

|<span data-ttu-id="2bb78-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="2bb78-112">Element</span></span>|<span data-ttu-id="2bb78-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bb78-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bb78-114">CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="2bb78-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="2bb78-115">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="2bb78-115">Required element.</span></span><br /><br /> <span data-ttu-id="2bb78-116">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2bb78-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bb78-117">Parent Elements</span></span>

|<span data-ttu-id="2bb78-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="2bb78-118">Element</span></span>|<span data-ttu-id="2bb78-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bb78-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bb78-120">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2bb78-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="2bb78-121">Bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2bb78-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2bb78-122">Remarks</span></span>

<span data-ttu-id="2bb78-123">Çoğu durumda, yalnızca bir tanımı için her denetim görünüm gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı görünümde kullanmak istiyorsanız birden çok tanım sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2bb78-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="2bb78-124">Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bb78-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2bb78-125">See Also</span></span>

[<span data-ttu-id="2bb78-126">CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="2bb78-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2bb78-127">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2bb78-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="2bb78-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="2bb78-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
