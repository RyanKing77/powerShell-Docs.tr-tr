---
title: TypeName öğesi için yapılandırma (biçimi) için denetimleri için SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845132"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="daffe-102">Yapılandırma Denetimleri için SelectionCondition TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="daffe-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="daffe-103">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="daffe-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="daffe-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="daffe-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="daffe-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin yapılandırma (biçimi) denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğe için denetimler için özel denetim için denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy CustomEntry için için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için yapılandırma (biçimi) CustomEntry öğesi SelectionCondition denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="daffe-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="daffe-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daffe-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="daffe-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="daffe-107">Attributes and Elements</span></span>

<span data-ttu-id="daffe-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="daffe-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="daffe-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="daffe-109">Attributes</span></span>

<span data-ttu-id="daffe-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="daffe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="daffe-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="daffe-111">Child Elements</span></span>

<span data-ttu-id="daffe-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="daffe-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="daffe-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="daffe-113">Parent Elements</span></span>

|<span data-ttu-id="daffe-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="daffe-114">Element</span></span>|<span data-ttu-id="daffe-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="daffe-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="daffe-116">İçin yapılandırma (biçimi) için CustomEntry için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="daffe-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="daffe-117">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="daffe-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="daffe-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="daffe-118">Text Value</span></span>

<span data-ttu-id="daffe-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="daffe-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="daffe-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="daffe-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="daffe-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="daffe-121">See Also</span></span>

[<span data-ttu-id="daffe-122">İçin yapılandırma (biçimi) için CustomEntry için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="daffe-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="daffe-123">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="daffe-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
