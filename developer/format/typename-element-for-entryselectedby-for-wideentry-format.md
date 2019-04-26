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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083935"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="38472-102">WideEntry EntrySelectedBy için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="38472-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="38472-103">Tanımı bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="38472-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="38472-104">Bu nesne görüntülenen her tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38472-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="38472-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi WideEntry (TypeName öğesinin WideEntry (biçimi) Biçimi)</span><span class="sxs-lookup"><span data-stu-id="38472-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38472-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38472-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38472-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="38472-107">Attributes and Elements</span></span>

<span data-ttu-id="38472-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="38472-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38472-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38472-109">Attributes</span></span>

<span data-ttu-id="38472-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="38472-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38472-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="38472-111">Child Elements</span></span>

<span data-ttu-id="38472-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="38472-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="38472-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="38472-113">Parent Elements</span></span>

|<span data-ttu-id="38472-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="38472-114">Element</span></span>|<span data-ttu-id="38472-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38472-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38472-116">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="38472-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="38472-117">Bu geniş bir girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38472-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="38472-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="38472-118">Text Value</span></span>

<span data-ttu-id="38472-119">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="38472-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="38472-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38472-120">Remarks</span></span>

<span data-ttu-id="38472-121">Her geniş bir girdi, bir veya daha fazla .NET türleri, seçim kümesi veya tanımı kullanılmak üzere mevcut olmalıdır seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="38472-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="38472-122">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="38472-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38472-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="38472-123">See Also</span></span>

[<span data-ttu-id="38472-124">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="38472-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="38472-125">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="38472-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="38472-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="38472-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
