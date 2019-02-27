---
title: CustomEntry öğesi görünümü (biçimi) için özel denetim için CustomEntries için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850886"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="63530-102">Görünüm CustomControl için CustomEntries CustomEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="63530-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="63530-103">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="63530-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="63530-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries Görünüm (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="63530-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63530-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63530-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63530-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="63530-106">Attributes and Elements</span></span>

<span data-ttu-id="63530-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="63530-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="63530-108">Tanımına göre görüntülenen öğeler belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="63530-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="63530-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="63530-109">Attributes</span></span>

<span data-ttu-id="63530-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="63530-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63530-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="63530-111">Child Elements</span></span>

|<span data-ttu-id="63530-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="63530-112">Element</span></span>|<span data-ttu-id="63530-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63530-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63530-114">İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="63530-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="63530-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="63530-115">Optional element.</span></span><br /><br /> <span data-ttu-id="63530-116">Özel denetim görünümü veya bu tanım için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="63530-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="63530-117">İçin görünümün (biçimi) CustomEntry CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="63530-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="63530-118">Özel denetim tanımı için bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="63530-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63530-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="63530-119">Parent Elements</span></span>

|<span data-ttu-id="63530-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="63530-120">Element</span></span>|<span data-ttu-id="63530-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63530-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63530-122">CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="63530-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="63530-123">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="63530-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="63530-124">Özel denetimin görünümü, bir veya daha fazla tanımları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="63530-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63530-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63530-125">Remarks</span></span>

<span data-ttu-id="63530-126">Çoğu durumda, sadece bir tanım her özel denetim görünüm için gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı görünümde kullanmak istiyorsanız birden çok tanım olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="63530-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="63530-127">Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="63530-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="63530-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="63530-128">See Also</span></span>

[<span data-ttu-id="63530-129">Özel denetim öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="63530-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="63530-130">İçin görünümün (biçimi) CustomEntry CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="63530-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="63530-131">İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="63530-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="63530-132">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="63530-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
