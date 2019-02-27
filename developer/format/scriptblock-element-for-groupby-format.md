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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846959"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="7784a-102">GroupBy için ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="7784a-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="7784a-103">Yeni bir grup değeri değiştiğinde başlatan betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="7784a-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="7784a-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) ScriptBlock öğesinin GroupBy (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7784a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7784a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7784a-105">Syntax</span></span>

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7784a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7784a-106">Attributes and Elements</span></span>

<span data-ttu-id="7784a-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7784a-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7784a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7784a-108">Attributes</span></span>

<span data-ttu-id="7784a-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="7784a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7784a-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7784a-110">Child Elements</span></span>

<span data-ttu-id="7784a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="7784a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7784a-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7784a-112">Parent Elements</span></span>

|<span data-ttu-id="7784a-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="7784a-113">Element</span></span>|<span data-ttu-id="7784a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7784a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7784a-115">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7784a-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7784a-116">.NET nesne grubu nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7784a-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7784a-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="7784a-117">Text Value</span></span>

<span data-ttu-id="7784a-118">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="7784a-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7784a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7784a-119">Remarks</span></span>

<span data-ttu-id="7784a-120">Bu betiğin değeri değiştiğinde yeni bir grup Windows PowerShell başlatır.</span><span class="sxs-lookup"><span data-stu-id="7784a-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="7784a-121">Bu öğe belirtildiğinde, belirtemezsiniz [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) yeni bir grup başlatmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="7784a-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7784a-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7784a-122">See Also</span></span>

[<span data-ttu-id="7784a-123">GroupBy (biçimi) için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="7784a-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="7784a-124">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7784a-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7784a-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="7784a-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
