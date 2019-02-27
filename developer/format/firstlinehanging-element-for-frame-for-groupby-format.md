---
title: GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846546"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="e3627-102">GroupBy Çerçevesi için FirstLineHanging Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e3627-102">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="e3627-103">Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3627-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="e3627-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3627-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e3627-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi Özel denetim GroupBy (biçimi) CustomItem öğesinin CustomEntry CustomItem GroupBy (biçimi) FirstLineHanging öğesinin GroupBy (biçimi) için çerçeve çerçeve öğesinin GroupBy (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e3627-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3627-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3627-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3627-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3627-107">Attributes and Elements</span></span>

<span data-ttu-id="e3627-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `FirstLineHanging` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e3627-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3627-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3627-109">Attributes</span></span>

<span data-ttu-id="e3627-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3627-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3627-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3627-111">Child Elements</span></span>

<span data-ttu-id="e3627-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3627-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3627-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3627-113">Parent Elements</span></span>

|<span data-ttu-id="e3627-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3627-114">Element</span></span>|<span data-ttu-id="e3627-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3627-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3627-116">GroupBy (biçimi) için CustomItem için çerçeve öğesi</span><span class="sxs-lookup"><span data-stu-id="e3627-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e3627-117">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3627-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3627-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="e3627-118">Text Value</span></span>

<span data-ttu-id="e3627-119">Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3627-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3627-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3627-120">Remarks</span></span>

<span data-ttu-id="e3627-121">Bu öğe belirtilmezse belirtemezsiniz [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="e3627-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3627-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e3627-122">See Also</span></span>

[<span data-ttu-id="e3627-123">GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="e3627-123">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e3627-124">GroupBy (biçimi) için CustomItem için çerçeve öğesi</span><span class="sxs-lookup"><span data-stu-id="e3627-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e3627-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e3627-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
