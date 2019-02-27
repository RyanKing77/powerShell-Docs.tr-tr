---
title: GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850781"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="c05dc-102">GroupBy EntrySelectedBy için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c05dc-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="c05dc-103">Özel denetimin bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c05dc-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="c05dc-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c05dc-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c05dc-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) TypeName öğesinin EntrySelectedBy GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="c05dc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c05dc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c05dc-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c05dc-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c05dc-107">Attributes and Elements</span></span>

<span data-ttu-id="c05dc-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c05dc-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c05dc-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c05dc-109">Attributes</span></span>

<span data-ttu-id="c05dc-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c05dc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c05dc-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c05dc-111">Child Elements</span></span>

<span data-ttu-id="c05dc-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c05dc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c05dc-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c05dc-113">Parent Elements</span></span>

|<span data-ttu-id="c05dc-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c05dc-114">Element</span></span>|<span data-ttu-id="c05dc-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c05dc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c05dc-116">GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="c05dc-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="c05dc-117">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c05dc-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c05dc-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="c05dc-118">Text Value</span></span>

<span data-ttu-id="c05dc-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="c05dc-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c05dc-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c05dc-120">Remarks</span></span>

<span data-ttu-id="c05dc-121">Her denetim tanımı en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c05dc-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c05dc-122">Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetimler oluşturma](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c05dc-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c05dc-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c05dc-123">See Also</span></span>

[<span data-ttu-id="c05dc-124">Özel denetimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="c05dc-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c05dc-125">GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="c05dc-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="c05dc-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c05dc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
