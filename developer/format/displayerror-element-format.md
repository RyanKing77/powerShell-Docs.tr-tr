---
title: DisplayError öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066269"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="6f72c-102">DisplayError Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="6f72c-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="6f72c-103">Bir hata oluştuğunda bir veri parçasını görüntüleme dizesi #ERR görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f72c-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="6f72c-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) DisplayError öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6f72c-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6f72c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f72c-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f72c-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6f72c-106">Attributes and Elements</span></span>

<span data-ttu-id="6f72c-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `DisplayError` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6f72c-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f72c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f72c-108">Attributes</span></span>

<span data-ttu-id="6f72c-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f72c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f72c-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6f72c-110">Child Elements</span></span>

<span data-ttu-id="6f72c-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f72c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6f72c-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6f72c-112">Parent Elements</span></span>

|<span data-ttu-id="6f72c-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f72c-113">Element</span></span>|<span data-ttu-id="6f72c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f72c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f72c-115">DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6f72c-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="6f72c-116">Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f72c-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6f72c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f72c-117">Remarks</span></span>

<span data-ttu-id="6f72c-118">Varsayılan olarak, bir veri parçasını görüntülemeye çalışırken bir hata oluştuğunda verilerin konumu boş bırakılır.</span><span class="sxs-lookup"><span data-stu-id="6f72c-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="6f72c-119">Bu öğe #ERR dize true olarak ayarlandığında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f72c-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f72c-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6f72c-120">See Also</span></span>

[<span data-ttu-id="6f72c-121">DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6f72c-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="6f72c-122">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6f72c-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
