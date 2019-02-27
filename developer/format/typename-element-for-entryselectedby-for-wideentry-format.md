---
title: TypeName öğesi EntrySelectedBy WideEntry (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851467"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="a22cb-102">WideEntry EntrySelectedBy için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a22cb-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="a22cb-103">Tanımı bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a22cb-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="a22cb-104">Bu nesne görüntülenen her tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a22cb-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="a22cb-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi WideEntry (TypeName öğesinin WideEntry (biçimi) Biçimi)</span><span class="sxs-lookup"><span data-stu-id="a22cb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a22cb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a22cb-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a22cb-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a22cb-107">Attributes and Elements</span></span>

<span data-ttu-id="a22cb-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a22cb-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a22cb-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a22cb-109">Attributes</span></span>

<span data-ttu-id="a22cb-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a22cb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a22cb-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a22cb-111">Child Elements</span></span>

<span data-ttu-id="a22cb-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a22cb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a22cb-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a22cb-113">Parent Elements</span></span>

|<span data-ttu-id="a22cb-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a22cb-114">Element</span></span>|<span data-ttu-id="a22cb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a22cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a22cb-116">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a22cb-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="a22cb-117">Bu geniş bir girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a22cb-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a22cb-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="a22cb-118">Text Value</span></span>

<span data-ttu-id="a22cb-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="a22cb-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a22cb-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a22cb-120">Remarks</span></span>

<span data-ttu-id="a22cb-121">Her geniş bir girdi, bir veya daha fazla .NET türleri, seçim kümesi veya tanımı kullanılmak üzere mevcut olmalıdır seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a22cb-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="a22cb-122">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a22cb-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a22cb-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a22cb-123">See Also</span></span>

[<span data-ttu-id="a22cb-124">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="a22cb-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a22cb-125">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a22cb-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="a22cb-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a22cb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
