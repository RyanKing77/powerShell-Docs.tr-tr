---
ms.date: 08/25/2017
keywords: PowerShell cmdlet'i
title: ObjectModelRoot Nesnesi
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406032"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="f46c6-103">ObjectModelRoot Nesnesi</span><span class="sxs-lookup"><span data-stu-id="f46c6-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="f46c6-104">**$PsISE** asıl kök nesnesi içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) nesne Microsoft.PowerShell.Host.ISE.ObjectModelRoot sınıfı bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f46c6-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="f46c6-105">Bu konuda özellikleri açıklanmıştır **ObjectModelRoot** nesne.</span><span class="sxs-lookup"><span data-stu-id="f46c6-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="f46c6-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f46c6-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="f46c6-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="f46c6-107">CurrentFile</span></span>

> <span data-ttu-id="f46c6-108">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f46c6-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f46c6-109">O anda odağı içeren bu konak nesnesi ile ilişkili dosya salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="f46c6-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="f46c6-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="f46c6-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="f46c6-111">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f46c6-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f46c6-112">Odaklanmış PowerShell sekme salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="f46c6-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="f46c6-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="f46c6-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="f46c6-114">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f46c6-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f46c6-115">Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği Düzenleyicisi altındaki yatay araç bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f46c6-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="f46c6-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="f46c6-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="f46c6-117">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f46c6-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f46c6-118">Şu anda görünür Windows PowerShell ISE eklenti aracı, salt okunur özelliği, düzenleyicinin sağ taraftaki dikey aracı bölmesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f46c6-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="f46c6-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f46c6-119">Options</span></span>

> <span data-ttu-id="f46c6-120">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f46c6-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f46c6-121">Çeşitli seçenekler, salt okunur özelliği Windows PowerShell ıse'de ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46c6-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="f46c6-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="f46c6-122">PowerShellTabs</span></span>

> <span data-ttu-id="f46c6-123">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f46c6-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f46c6-124">Windows PowerShell ISE'de açık olan PowerShell sekme koleksiyon salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="f46c6-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="f46c6-125">Varsayılan olarak, bu nesne bir PowerShell sekmesi içerir. Ancak, betikleri kullanarak veya Windows PowerShell ISE'de menülerini kullanarak bu nesne için daha fazla PowerShell sekme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46c6-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="f46c6-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f46c6-126">See Also</span></span>

- [<span data-ttu-id="f46c6-127">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="f46c6-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f46c6-128">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="f46c6-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)