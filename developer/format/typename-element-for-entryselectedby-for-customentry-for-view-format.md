---
title: TypeName öğesi görünümü (biçimi) için CustomEntry için EntrySelectedBy için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848800"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="02fc9-102">Görünüm CustomEntry için EntrySelectedBy TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="02fc9-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="02fc9-103">Özel denetim görünümün bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="02fc9-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="02fc9-104">Bir tanımı için belirtilebilen türleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="02fc9-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="02fc9-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries EntrySelectedBy görünümü (biçimi) için özel denetim için Öğe için CustomEntry TypeName öğesinin EntrySelectedBy CustomEntry görünümü (biçimi) için View (biçimi)</span><span class="sxs-lookup"><span data-stu-id="02fc9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="02fc9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02fc9-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="02fc9-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02fc9-107">Attributes and Elements</span></span>

<span data-ttu-id="02fc9-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="02fc9-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="02fc9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02fc9-109">Attributes</span></span>

<span data-ttu-id="02fc9-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="02fc9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="02fc9-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02fc9-111">Child Elements</span></span>

<span data-ttu-id="02fc9-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="02fc9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="02fc9-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02fc9-113">Parent Elements</span></span>

|<span data-ttu-id="02fc9-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="02fc9-114">Element</span></span>|<span data-ttu-id="02fc9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02fc9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02fc9-116">İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="02fc9-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="02fc9-117">Bu özel denetimi görünüm tanımını kullanma .NET türleri veya bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02fc9-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="02fc9-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="02fc9-118">Text Value</span></span>

<span data-ttu-id="02fc9-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="02fc9-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="02fc9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02fc9-120">Remarks</span></span>

<span data-ttu-id="02fc9-121">Her özel denetim görünüm tanımı, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="02fc9-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="02fc9-122">Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetimler oluşturma](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="02fc9-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02fc9-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="02fc9-123">See Also</span></span>

[<span data-ttu-id="02fc9-124">Özel denetimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="02fc9-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="02fc9-125">İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="02fc9-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="02fc9-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="02fc9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
