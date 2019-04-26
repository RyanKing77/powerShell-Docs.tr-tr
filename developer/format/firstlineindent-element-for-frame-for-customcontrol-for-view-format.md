---
title: FirstLineIndent öğesi görünümü (biçimi) için özel denetim için çerçeve için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065878"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="d79d5-102">Görünüm CustomControl için Çerçeve FirstLineIndent Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="d79d5-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="d79d5-103">İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d79d5-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="d79d5-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d79d5-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d79d5-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry CustomItem FirstLineIndent öğesi görünümü (biçimi) için özel denetim için çerçeve öğesinin CustomControlView (biçimi)</span><span class="sxs-lookup"><span data-stu-id="d79d5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="d79d5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d79d5-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d79d5-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d79d5-107">Attributes and Elements</span></span>

<span data-ttu-id="d79d5-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `FirstLineIndent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d79d5-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d79d5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d79d5-109">Attributes</span></span>

<span data-ttu-id="d79d5-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="d79d5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d79d5-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d79d5-111">Child Elements</span></span>

<span data-ttu-id="d79d5-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="d79d5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d79d5-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d79d5-113">Parent Elements</span></span>

|<span data-ttu-id="d79d5-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="d79d5-114">Element</span></span>|<span data-ttu-id="d79d5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d79d5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d79d5-116">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="d79d5-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="d79d5-117">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d79d5-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d79d5-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="d79d5-118">Text Value</span></span>

<span data-ttu-id="d79d5-119">Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d79d5-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="d79d5-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d79d5-120">Remarks</span></span>

<span data-ttu-id="d79d5-121">Bu öğe belirtilmezse belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d79d5-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d79d5-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d79d5-122">See Also</span></span>

[<span data-ttu-id="d79d5-123">FirstLineHanging öğesi görünümü (biçimi) için özel denetim için çerçeve için</span><span class="sxs-lookup"><span data-stu-id="d79d5-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d79d5-124">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="d79d5-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d79d5-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="d79d5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
