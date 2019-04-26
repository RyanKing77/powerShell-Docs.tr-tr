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
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064518"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="94e37-102">GroupBy için ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="94e37-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="94e37-103">Yeni bir grup değeri değiştiğinde başlatan betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="94e37-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="94e37-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) ScriptBlock öğesinin GroupBy (biçimi)</span><span class="sxs-lookup"><span data-stu-id="94e37-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94e37-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94e37-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94e37-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="94e37-106">Attributes and Elements</span></span>

<span data-ttu-id="94e37-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="94e37-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94e37-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="94e37-108">Attributes</span></span>

<span data-ttu-id="94e37-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="94e37-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94e37-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="94e37-110">Child Elements</span></span>

<span data-ttu-id="94e37-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="94e37-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94e37-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="94e37-112">Parent Elements</span></span>

|<span data-ttu-id="94e37-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="94e37-113">Element</span></span>|<span data-ttu-id="94e37-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94e37-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94e37-115">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="94e37-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="94e37-116">.NET nesne grubu nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94e37-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="94e37-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="94e37-117">Text Value</span></span>

<span data-ttu-id="94e37-118">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="94e37-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="94e37-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94e37-119">Remarks</span></span>

<span data-ttu-id="94e37-120">Bu betiğin değeri değiştiğinde yeni bir grup Windows PowerShell başlatır.</span><span class="sxs-lookup"><span data-stu-id="94e37-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="94e37-121">Bu öğe belirtildiğinde, belirtemezsiniz [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) yeni bir grup başlatmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="94e37-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="94e37-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="94e37-122">See Also</span></span>

[<span data-ttu-id="94e37-123">GroupBy (biçimi) için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="94e37-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="94e37-124">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="94e37-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="94e37-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="94e37-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
