---
title: GroupBy (biçimi) için SelectionCondition için TypeName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083782"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="bed08-102">GroupBy SelectionCondition için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="bed08-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="bed08-103">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bed08-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="bed08-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bed08-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bed08-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) SelectionCondition öğesinin EntrySelectedBy GroupBy (biçimi) TypeName öğesinin SelectionCondition GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="bed08-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bed08-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bed08-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bed08-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="bed08-107">Attributes and Elements</span></span>

<span data-ttu-id="bed08-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bed08-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bed08-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bed08-109">Attributes</span></span>

<span data-ttu-id="bed08-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="bed08-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bed08-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="bed08-111">Child Elements</span></span>

<span data-ttu-id="bed08-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="bed08-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bed08-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="bed08-113">Parent Elements</span></span>

|<span data-ttu-id="bed08-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="bed08-114">Element</span></span>|<span data-ttu-id="bed08-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bed08-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bed08-116">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="bed08-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bed08-117">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bed08-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bed08-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="bed08-118">Text Value</span></span>

<span data-ttu-id="bed08-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="bed08-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bed08-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bed08-120">Remarks</span></span>

<span data-ttu-id="bed08-121">Bu öğe belirtildiğinde, belirtemezsiniz `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bed08-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="bed08-122">Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bed08-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bed08-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bed08-123">See Also</span></span>

[<span data-ttu-id="bed08-124">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="bed08-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bed08-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="bed08-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
