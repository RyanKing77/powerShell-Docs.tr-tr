---
ms.date: 08/25/2017
keywords: PowerShell cmdlet'i
title: ObjectModelRoot Nesnesi
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954611"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="05aa7-103">ObjectModelRoot Nesnesi</span><span class="sxs-lookup"><span data-stu-id="05aa7-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="05aa7-104">**$PsISE** asıl kök nesnesi içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) olan nesne, Microsoft.PowerShell.Host.ISE.ObjectModelRoot sınıfının bir örneği değil.</span><span class="sxs-lookup"><span data-stu-id="05aa7-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="05aa7-105">Bu konuda, özelliklerini açıklar **ObjectModelRoot** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="05aa7-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="05aa7-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="05aa7-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="05aa7-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="05aa7-107">CurrentFile</span></span>

> <span data-ttu-id="05aa7-108">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05aa7-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="05aa7-109">Şu anda odağa sahip bu konağı nesnesi ile ilişkilendirilmiş dosya alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="05aa7-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="05aa7-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="05aa7-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="05aa7-111">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05aa7-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="05aa7-112">Odaklanmış PowerShell sekmesini alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="05aa7-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="05aa7-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="05aa7-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="05aa7-114">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05aa7-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="05aa7-115">Şu anda görünür Windows PowerShell ISE eklenti aracı alır salt okunur özellik düzenleyicisinin alt yatay aracı bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="05aa7-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="05aa7-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="05aa7-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="05aa7-117">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05aa7-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="05aa7-118">Şu anda görünür Windows PowerShell ISE eklenti aracı alır salt okunur özellik Düzenleyicisinin sağ taraftaki dikey aracı bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="05aa7-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="05aa7-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="05aa7-119">Options</span></span>

> <span data-ttu-id="05aa7-120">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05aa7-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="05aa7-121">Çeşitli seçenekler alır salt okunur özelliğini Windows PowerShell ISE ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05aa7-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="05aa7-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="05aa7-122">PowerShellTabs</span></span>

> <span data-ttu-id="05aa7-123">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05aa7-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="05aa7-124">Windows PowerShell ISE açık PowerShell sekmeler koleksiyonunu alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="05aa7-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="05aa7-125">Varsayılan olarak, bu nesne bir PowerShell sekme içerir. Ancak, komut dosyalarını kullanarak veya Windows PowerShell ISE menüleri kullanarak bu nesne için daha fazla PowerShell sekmeler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05aa7-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="05aa7-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="05aa7-126">See Also</span></span>

- [<span data-ttu-id="05aa7-127">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="05aa7-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="05aa7-128">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="05aa7-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)