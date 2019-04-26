---
title: Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066493"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="bef36-102">Yapılandırma Denetimleri için CustomControl CustomEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="bef36-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bef36-103">Bir ortak denetimi tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bef36-103">Provides a definition of the common control.</span></span> <span data-ttu-id="bef36-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bef36-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bef36-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="bef36-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bef36-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bef36-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bef36-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="bef36-107">Attributes and Elements</span></span>

<span data-ttu-id="bef36-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bef36-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="bef36-109">Tanımına göre görüntülenen öğeler belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bef36-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="bef36-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bef36-110">Attributes</span></span>

<span data-ttu-id="bef36-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="bef36-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bef36-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="bef36-112">Child Elements</span></span>

|<span data-ttu-id="bef36-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="bef36-113">Element</span></span>|<span data-ttu-id="bef36-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bef36-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bef36-115">İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="bef36-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="bef36-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bef36-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bef36-117">Ortak denetim ya da bu denetim için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bef36-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="bef36-118">Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="bef36-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="bef36-119">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="bef36-119">Required element.</span></span><br /><br /> <span data-ttu-id="bef36-120">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bef36-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bef36-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="bef36-121">Parent Elements</span></span>

|<span data-ttu-id="bef36-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="bef36-122">Element</span></span>|<span data-ttu-id="bef36-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bef36-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bef36-124">Yapılandırma (biçimi) için özel denetim için CustomEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="bef36-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="bef36-125">Tanımları ortak denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bef36-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bef36-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bef36-126">Remarks</span></span>

<span data-ttu-id="bef36-127">Çoğu durumda, yalnızca bir tanımı için ortak her özel denetimi gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bef36-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="bef36-128">Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bef36-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="bef36-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bef36-129">See Also</span></span>

[<span data-ttu-id="bef36-130">Yapılandırma (biçimi) için özel denetim için CustomEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="bef36-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="bef36-131">Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="bef36-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="bef36-132">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="bef36-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
