---
ms.date: 08/25/2017
keywords: PowerShell cmdlet'i
title: ObjectModelRoot Nesnesi
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684377"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="ae9d4-103">ObjectModelRoot Nesnesi</span><span class="sxs-lookup"><span data-stu-id="ae9d4-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="ae9d4-104">**$PsISE** asıl kök nesnesi içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) nesne Microsoft.PowerShell.Host.ISE.ObjectModelRoot sınıfı bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="ae9d4-105">Bu konuda özellikleri açıklanmıştır **ObjectModelRoot** nesne.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="ae9d4-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ae9d4-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="ae9d4-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="ae9d4-107">CurrentFile</span></span>

> <span data-ttu-id="ae9d4-108">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ae9d4-109">O anda odağı içeren bu konak nesnesi ile ilişkili dosya salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="ae9d4-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="ae9d4-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="ae9d4-111">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ae9d4-112">Odaklanmış PowerShell sekme salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="ae9d4-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="ae9d4-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="ae9d4-114">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ae9d4-115">Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği Düzenleyicisi altındaki yatay araç bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="ae9d4-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="ae9d4-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="ae9d4-117">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ae9d4-118">Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği, düzenleyicinin sağ taraftaki dikey aracı bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="ae9d4-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ae9d4-119">Options</span></span>

> <span data-ttu-id="ae9d4-120">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ae9d4-121">Çeşitli seçenekler, salt okunur özelliği Windows PowerShell ıse'de ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="ae9d4-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="ae9d4-122">PowerShellTabs</span></span>

> <span data-ttu-id="ae9d4-123">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ae9d4-124">Windows PowerShell ISE'de açık olan PowerShell sekme koleksiyon salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="ae9d4-125">Varsayılan olarak, bu nesne bir PowerShell sekmesi içerir. Ancak, betikleri kullanarak veya Windows PowerShell ISE'de menülerini kullanarak bu nesne için daha fazla PowerShell sekme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae9d4-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae9d4-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ae9d4-126">See Also</span></span>

- [<span data-ttu-id="ae9d4-127">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="ae9d4-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ae9d4-128">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="ae9d4-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)