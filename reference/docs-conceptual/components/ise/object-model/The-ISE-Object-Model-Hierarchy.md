---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISE Nesne Modeli Hiyerarşisi
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405915"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="dbc67-103">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="dbc67-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="dbc67-104">Bu konu, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) kapsamındaki nesne hiyerarşisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbc67-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="dbc67-105">Windows PowerShell 3.0 ve Windows PowerShell 4.0, Windows PowerShell ISE dahildir.</span><span class="sxs-lookup"><span data-stu-id="dbc67-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="dbc67-106">Bir nesne tanımlayan nesne sınıfı için başvuru belgeleri için almak için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dbc67-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="dbc67-107">$psISE nesnesi</span><span class="sxs-lookup"><span data-stu-id="dbc67-107">$psISE Object</span></span>

<span data-ttu-id="dbc67-108">**$PsISE** nesnedir [kök nesnesi](The-ObjectModelRoot-Object.md) Windows PowerShell ISE nesne hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="dbc67-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="dbc67-109">En üst düzeyinde bulunan, aşağıdaki nesneler kullanılabilir komut dosyası için getirir:</span><span class="sxs-lookup"><span data-stu-id="dbc67-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="dbc67-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="dbc67-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="dbc67-111">**$PsISE.CurrentFile** nesnedir örneği [Isefile](The-ISEFile-Object.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc67-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="dbc67-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="dbc67-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="dbc67-113">**$PsISE.CurrentPowerShellTab** nesnedir örneği [PowerShellTab](The-PowerShellTab-Object.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc67-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="dbc67-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="dbc67-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="dbc67-115">**$PsISE.CurrentVisibleHorizontalTool** nesnedir örneği [Iseaddontool](The-ISEAddOnTool-Object.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc67-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="dbc67-116">Windows PowerShell ISE penceresi üst kenarına şu anda sabitlenmiş yüklü eklenti aracını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dbc67-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="dbc67-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="dbc67-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="dbc67-118">**$PsISE.CurrentVisibleHorizontalTool** nesnedir örneği [Iseaddontool](The-ISEAddOnTool-Object.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc67-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="dbc67-119">Windows PowerShell ISE penceresi sağ kenarına şu anda sabitlenmiş yüklü eklenti aracını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dbc67-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="dbc67-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="dbc67-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="dbc67-121">**$PsISE.Options** nesnedir örneği [Iseoptions](The-ISEOptions-Object.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc67-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="dbc67-122">Iseoptions nesnesi, çeşitli Windows PowerShell ISE ayarlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dbc67-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="dbc67-123">Microsoft.PowerShell.Host.ISE.ISEOptions sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="dbc67-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="dbc67-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="dbc67-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="dbc67-125">**$PsISE.PowerShellTabs** nesnedir örneği [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc67-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="dbc67-126">Yerel bilgisayarda veya uzak bilgisayarlarda bağlı ortamlarda çalıştırmanızı kullanılabilir Windows PowerShell temsil eden tüm açık PowerShell sekmeleri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="dbc67-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="dbc67-127">Koleksiyonda her üye örneğidir [PowerShellTab](The-PowerShellTab-Object.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc67-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbc67-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="dbc67-128">See Also</span></span>

- [<span data-ttu-id="dbc67-129">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="dbc67-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="dbc67-130">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="dbc67-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)