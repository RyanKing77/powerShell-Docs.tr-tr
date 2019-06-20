---
title: Windows PowerShell kavramlarını | Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263851"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="cfcbb-102">Windows PowerShell Kavramları</span><span class="sxs-lookup"><span data-stu-id="cfcbb-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="cfcbb-103">Bu bölümde, bir geliştiricinin bakış açısından PowerShell anlamanıza yardımcı olacak kavramsal bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="cfcbb-104">Konu adı</span><span class="sxs-lookup"><span data-stu-id="cfcbb-104">Topic Name</span></span>|<span data-ttu-id="cfcbb-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfcbb-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="cfcbb-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="cfcbb-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="cfcbb-107">PowerShell nesnelerini açıklaması.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-107">Description of PowerShell objects.</span></span> <span data-ttu-id="cfcbb-108">Daha fazla bilgi için [nesne oluşturma hakkında](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="cfcbb-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="cfcbb-109">Çalışma alanları oluşturma</span><span class="sxs-lookup"><span data-stu-id="cfcbb-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="cfcbb-110">Burada komutlar işlenir işletim ortamlarının.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="cfcbb-111">Daha fazla bilgi için [çalışma sınıfı](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="cfcbb-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="cfcbb-112">Çıkış nesnelerini genişletme</span><span class="sxs-lookup"><span data-stu-id="cfcbb-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="cfcbb-113">PowerShell nesnelerini genişletmek nasıl.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="cfcbb-114">Daha fazla bilgi için [Types.ps1xml hakkında](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="cfcbb-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="cfcbb-115">Cmdlet'leri kaydetme</span><span class="sxs-lookup"><span data-stu-id="cfcbb-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="cfcbb-116">Modüller ve ek bileşenler PowerShell'de kullanılabilir hale getirme.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="cfcbb-117">Daha fazla bilgi için [modüllerini ve ek bileşenler](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="cfcbb-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="cfcbb-118">Cmdlet'leri onay isteme</span><span class="sxs-lookup"><span data-stu-id="cfcbb-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="cfcbb-119">Bir eylem önce nasıl cmdlet'lerini ve sağlayıcıları geri bildirim kullanıcıdan isteyin.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="cfcbb-120">RuntimeDefinedParameter sınıfı</span><span class="sxs-lookup"><span data-stu-id="cfcbb-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="cfcbb-121">Çalışma zamanı parametre bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="cfcbb-122">System.Management.Automation Namespace</span><span class="sxs-lookup"><span data-stu-id="cfcbb-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="cfcbb-123">PowerShell API ad alanlarına genel bakış.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="cfcbb-124">Windows PowerShell sağlayıcısındaki genel bakış</span><span class="sxs-lookup"><span data-stu-id="cfcbb-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="cfcbb-125">Verilere erişmek için kullanılan PowerShell sağlayıcıları hakkında genel bakış depolar.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="cfcbb-126">PowerShell cmdlet'leri için Yardım yazma</span><span class="sxs-lookup"><span data-stu-id="cfcbb-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="cfcbb-127">PowerShell cmdlet Yardım yazma yapma.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="cfcbb-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-128">See also</span></span>

[<span data-ttu-id="cfcbb-129">PowerShell sınıfı</span><span class="sxs-lookup"><span data-stu-id="cfcbb-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="cfcbb-130">PowerShell Core API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cfcbb-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="cfcbb-131">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cfcbb-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="cfcbb-132">Windows PowerShell modülleri için Yardım yazma</span><span class="sxs-lookup"><span data-stu-id="cfcbb-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="cfcbb-133">Bir Windows Powershell sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="cfcbb-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="cfcbb-134">Windows PowerShell API'si başvurusu</span><span class="sxs-lookup"><span data-stu-id="cfcbb-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="cfcbb-135">Windows PowerShell başvurusu</span><span class="sxs-lookup"><span data-stu-id="cfcbb-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)