---
title: TypeName öğesi ViewSelectedBy (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083765"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="8a931-102">ViewSelectedBy için TypeName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="8a931-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="8a931-103">Görünüm tarafından görüntülenen bir .NET nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a931-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="8a931-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ViewSelectedBy öğesi (biçimi) TypeName öğesi ViewSelectedBy (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="8a931-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8a931-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a931-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8a931-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="8a931-106">Attributes and Elements</span></span>

<span data-ttu-id="8a931-107">Aşağıdaki öznitelikler, alt ve üst öğelerinin bölümlerde `TypeName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8a931-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8a931-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8a931-108">Attributes</span></span>

<span data-ttu-id="8a931-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="8a931-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8a931-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="8a931-110">Child Elements</span></span>

<span data-ttu-id="8a931-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="8a931-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8a931-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="8a931-112">Parent Elements</span></span>

|<span data-ttu-id="8a931-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a931-113">Element</span></span>|<span data-ttu-id="8a931-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a931-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8a931-115">ViewSelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8a931-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="8a931-116">Görünüm tarafından görüntülenen .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8a931-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8a931-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="8a931-117">Text Value</span></span>

<span data-ttu-id="8a931-118">.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="8a931-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a931-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a931-119">Remarks</span></span>

<span data-ttu-id="8a931-120">Bu öğe farklı görünümleri nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md), [bir liste görünümü oluşturma](./creating-a-list-view.md), [geniş bir görünüm oluşturma](./creating-a-wide-view.md), ve [ Özel Görünüm bileşenleri](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8a931-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="8a931-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a931-121">Example</span></span>

<span data-ttu-id="8a931-122">Aşağıdaki örnek nasıl belirtileceğini gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne için bir liste görünümü.</span><span class="sxs-lookup"><span data-stu-id="8a931-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="8a931-123">Aynı şemayı, tablo, geniş ve özel görünümleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a931-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="8a931-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8a931-124">See Also</span></span>

[<span data-ttu-id="8a931-125">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a931-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8a931-126">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a931-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8a931-127">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a931-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8a931-128">Özel denetimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a931-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8a931-129">ViewSelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8a931-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="8a931-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="8a931-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
