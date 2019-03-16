---
title: FirstLineHanging öğesi görünümü (biçimi) için özel denetim için çerçeve için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054229"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="34e25-102">Görünüm CustomControl için Çerçeve FirstLineHanging Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="34e25-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="34e25-103">Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="34e25-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="34e25-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34e25-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="34e25-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry CustomItem çerçeve Görünüm (biçimi) için özel denetim için View (biçimi) FirstLineHanging öğesinin özel denetim için çerçeve öğesinin CustomControlView (biçimi)</span><span class="sxs-lookup"><span data-stu-id="34e25-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34e25-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34e25-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34e25-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34e25-107">Attributes and Elements</span></span>

<span data-ttu-id="34e25-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `FirstLineHanging` öğesi.</span><span class="sxs-lookup"><span data-stu-id="34e25-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34e25-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34e25-109">Attributes</span></span>

<span data-ttu-id="34e25-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="34e25-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34e25-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34e25-111">Child Elements</span></span>

<span data-ttu-id="34e25-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="34e25-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34e25-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34e25-113">Parent Elements</span></span>

|<span data-ttu-id="34e25-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="34e25-114">Element</span></span>|<span data-ttu-id="34e25-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34e25-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34e25-116">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="34e25-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="34e25-117">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34e25-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34e25-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="34e25-118">Text Value</span></span>

<span data-ttu-id="34e25-119">Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="34e25-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="34e25-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34e25-120">Remarks</span></span>

<span data-ttu-id="34e25-121">Bu öğe belirtilmezse belirtemezsiniz [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="34e25-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="34e25-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="34e25-122">See Also</span></span>

[<span data-ttu-id="34e25-123">FirstLineIndent öğesi görünümü (biçimi) için özel denetim için çerçeve için</span><span class="sxs-lookup"><span data-stu-id="34e25-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="34e25-124">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="34e25-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="34e25-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="34e25-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
