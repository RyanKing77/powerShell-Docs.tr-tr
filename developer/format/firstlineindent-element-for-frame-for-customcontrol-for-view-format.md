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
ms.openlocfilehash: 9ec6caedcb7cf20d4aab2216cd8a9707269d9452
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846084"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="c1586-102">Görünüm CustomControl için Çerçeve FirstLineIndent Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c1586-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="c1586-103">İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1586-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="c1586-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c1586-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c1586-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry CustomItem FirstLineIndent öğesi görünümü (biçimi) için özel denetim için çerçeve öğesinin CutomControlView (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c1586-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="c1586-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1586-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1586-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1586-107">Attributes and Elements</span></span>

<span data-ttu-id="c1586-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `FirstLineIndent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c1586-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1586-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1586-109">Attributes</span></span>

<span data-ttu-id="c1586-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1586-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1586-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1586-111">Child Elements</span></span>

<span data-ttu-id="c1586-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1586-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1586-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1586-113">Parent Elements</span></span>

|<span data-ttu-id="c1586-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1586-114">Element</span></span>|<span data-ttu-id="c1586-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1586-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1586-116">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="c1586-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="c1586-117">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c1586-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1586-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="c1586-118">Text Value</span></span>

<span data-ttu-id="c1586-119">Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="c1586-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1586-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1586-120">Remarks</span></span>

<span data-ttu-id="c1586-121">Bu öğe belirtilmezse belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="c1586-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1586-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c1586-122">See Also</span></span>

[<span data-ttu-id="c1586-123">FirstLineHanging öğesi görünümü (biçimi) için özel denetim için çerçeve için</span><span class="sxs-lookup"><span data-stu-id="c1586-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c1586-124">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="c1586-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c1586-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c1586-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
