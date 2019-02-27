---
title: Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineHanging öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850550"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="5d39a-102">Yapılandırma Denetimleri için Çerçeve FirstLineHanging Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="5d39a-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5d39a-103">Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d39a-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="5d39a-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d39a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5d39a-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem çerçevesi için yapılandırma (biçimi) FirstLineHanging öğe için denetimler için yapılandırma çerçeve öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi Denetimler için yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5d39a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5d39a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d39a-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d39a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d39a-107">Attributes and Elements</span></span>

<span data-ttu-id="5d39a-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `FirstLineHanging` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5d39a-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d39a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5d39a-109">Attributes</span></span>

<span data-ttu-id="5d39a-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d39a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d39a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d39a-111">Child Elements</span></span>

<span data-ttu-id="5d39a-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d39a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d39a-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d39a-113">Parent Elements</span></span>

|<span data-ttu-id="5d39a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d39a-114">Element</span></span>|<span data-ttu-id="5d39a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d39a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d39a-116">Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="5d39a-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="5d39a-117">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d39a-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5d39a-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="5d39a-118">Text Value</span></span>

<span data-ttu-id="5d39a-119">Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="5d39a-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d39a-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d39a-120">Remarks</span></span>

<span data-ttu-id="5d39a-121">Bu öğe belirtilmezse belirtemezsiniz `FirstLineIndent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5d39a-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d39a-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5d39a-122">See Also</span></span>

[<span data-ttu-id="5d39a-123">Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="5d39a-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5d39a-124">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="5d39a-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
