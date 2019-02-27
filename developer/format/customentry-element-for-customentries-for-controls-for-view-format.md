---
title: CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848758"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="c352e-102">Görünüm Denetimleri için CustomEntries CustomEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c352e-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="c352e-103">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c352e-103">Provides a definition of the control.</span></span> <span data-ttu-id="c352e-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c352e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c352e-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Görünümü (biçimi) CustomEntry öğesinin CustomEntries Görünüm (biçimi) için denetimler için özel denetim</span><span class="sxs-lookup"><span data-stu-id="c352e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c352e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c352e-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c352e-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c352e-107">Attributes and Elements</span></span>

<span data-ttu-id="c352e-108">Aşağıdaki öznitelikler, alt ve üst öğelerinin bölümlerde `CustomEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c352e-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c352e-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c352e-109">Attributes</span></span>

<span data-ttu-id="c352e-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c352e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c352e-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c352e-111">Child Elements</span></span>

|<span data-ttu-id="c352e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="c352e-112">Element</span></span>|<span data-ttu-id="c352e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c352e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c352e-114">EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="c352e-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c352e-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c352e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c352e-116">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c352e-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="c352e-117">CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="c352e-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c352e-118">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="c352e-118">Required element.</span></span><br /><br /> <span data-ttu-id="c352e-119">Denetimin veri görüntüleme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c352e-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c352e-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c352e-120">Parent Elements</span></span>

|<span data-ttu-id="c352e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c352e-121">Element</span></span>|<span data-ttu-id="c352e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c352e-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c352e-123">CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="c352e-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="c352e-124">Denetim için tanımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c352e-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c352e-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c352e-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c352e-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c352e-126">See Also</span></span>

[<span data-ttu-id="c352e-127">CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="c352e-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c352e-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c352e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
