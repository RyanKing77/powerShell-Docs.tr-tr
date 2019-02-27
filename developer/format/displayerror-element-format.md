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
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846056"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="5d441-102">DisplayError Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="5d441-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="5d441-103">Bir hata oluştuğunda bir veri parçasını görüntüleme dizesi #ERR görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d441-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="5d441-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) DisplayError öğesi (Frmat)</span><span class="sxs-lookup"><span data-stu-id="5d441-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Frmat)</span></span>

## <a name="syntax"></a><span data-ttu-id="5d441-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d441-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d441-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d441-106">Attributes and Elements</span></span>

<span data-ttu-id="5d441-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `DisplayError` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5d441-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d441-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5d441-108">Attributes</span></span>

<span data-ttu-id="5d441-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d441-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d441-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d441-110">Child Elements</span></span>

<span data-ttu-id="5d441-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d441-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d441-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d441-112">Parent Elements</span></span>

|<span data-ttu-id="5d441-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d441-113">Element</span></span>|<span data-ttu-id="5d441-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d441-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d441-115">DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5d441-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="5d441-116">Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d441-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5d441-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d441-117">Remarks</span></span>

<span data-ttu-id="5d441-118">Varsayılan olarak, bir veri parçasını görüntülemeye çalışırken bir hata oluştuğunda verilerin konumu boş bırakılır.</span><span class="sxs-lookup"><span data-stu-id="5d441-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="5d441-119">Bu öğe #ERR dize true olarak ayarlandığında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5d441-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d441-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5d441-120">See Also</span></span>

[<span data-ttu-id="5d441-121">DefaultSettings öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5d441-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="5d441-122">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="5d441-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
