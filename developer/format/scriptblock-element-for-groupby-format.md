---
title: GroupBy (biçimi) için ScriptBlock öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229305"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="a683f-102">GroupBy için ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a683f-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="a683f-103">Yeni bir grup değeri değiştiğinde başlatan betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="a683f-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="a683f-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) ScriptBlock öğesinin GroupBy (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a683f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a683f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a683f-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a683f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a683f-106">Attributes and Elements</span></span>

<span data-ttu-id="a683f-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a683f-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a683f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a683f-108">Attributes</span></span>

<span data-ttu-id="a683f-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a683f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a683f-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a683f-110">Child Elements</span></span>

<span data-ttu-id="a683f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="a683f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a683f-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a683f-112">Parent Elements</span></span>

|<span data-ttu-id="a683f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="a683f-113">Element</span></span>|<span data-ttu-id="a683f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a683f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a683f-115">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a683f-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a683f-116">.NET nesne grubu nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a683f-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a683f-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="a683f-117">Text Value</span></span>

<span data-ttu-id="a683f-118">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="a683f-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a683f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a683f-119">Remarks</span></span>

<span data-ttu-id="a683f-120">Bu betiğin değeri değiştiğinde yeni bir grup PowerShell başlatır.</span><span class="sxs-lookup"><span data-stu-id="a683f-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="a683f-121">Bu öğe belirtildiğinde, belirtemezsiniz [PropertyName](propertyname-element-for-groupby-format.md) yeni bir grup başlatmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="a683f-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="a683f-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a683f-122">See Also</span></span>

[<span data-ttu-id="a683f-123">GroupBy (biçimi) için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="a683f-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="a683f-124">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a683f-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="a683f-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a683f-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
