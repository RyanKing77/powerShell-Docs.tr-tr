---
ms.date: 08/25/2017
keywords: PowerShell cmdlet'i
title: ObjectModelRoot Nesnesi
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086791"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="1a07e-103">ObjectModelRoot Nesnesi</span><span class="sxs-lookup"><span data-stu-id="1a07e-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="1a07e-104">**$PsISE** asıl kök nesnesi içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) nesne Microsoft.PowerShell.Host.ISE.ObjectModelRoot sınıfı bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="1a07e-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="1a07e-105">Bu konuda özellikleri açıklanmıştır **ObjectModelRoot** nesne.</span><span class="sxs-lookup"><span data-stu-id="1a07e-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="1a07e-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1a07e-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="1a07e-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="1a07e-107">CurrentFile</span></span>

> <span data-ttu-id="1a07e-108">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1a07e-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1a07e-109">O anda odağı içeren bu konak nesnesi ile ilişkili dosya salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a07e-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="1a07e-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="1a07e-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="1a07e-111">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1a07e-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1a07e-112">Odaklanmış PowerShell sekme salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a07e-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="1a07e-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="1a07e-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="1a07e-114">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1a07e-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1a07e-115">Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği Düzenleyicisi altındaki yatay araç bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1a07e-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="1a07e-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="1a07e-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="1a07e-117">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1a07e-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1a07e-118">Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği, düzenleyicinin sağ taraftaki dikey aracı bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1a07e-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="1a07e-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1a07e-119">Options</span></span>

> <span data-ttu-id="1a07e-120">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1a07e-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1a07e-121">Çeşitli seçenekler, salt okunur özelliği Windows PowerShell ıse'de ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a07e-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="1a07e-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="1a07e-122">PowerShellTabs</span></span>

> <span data-ttu-id="1a07e-123">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1a07e-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1a07e-124">Windows PowerShell ISE'de açık olan PowerShell sekme koleksiyon salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a07e-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="1a07e-125">Varsayılan olarak, bu nesne bir PowerShell sekmesi içerir. Ancak, betikleri kullanarak veya Windows PowerShell ISE'de menülerini kullanarak bu nesne için daha fazla PowerShell sekme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a07e-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a07e-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1a07e-126">See Also</span></span>

- [<span data-ttu-id="1a07e-127">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="1a07e-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1a07e-128">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="1a07e-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)