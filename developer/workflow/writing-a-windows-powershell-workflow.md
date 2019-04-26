---
title: Bir Windows PowerShell iş akışı yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080331"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="a8b22-102">Windows PowerShell İş Akışını Yazma</span><span class="sxs-lookup"><span data-stu-id="a8b22-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="a8b22-103">Bir XAML iş akışı etkinlikleri iş akışı Tasarımcısı'nda Visual Studio için Windows PowerShell derlemeler tarafından kullanıma sunulan ekleyerek oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8b22-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="a8b22-104">Aşağıdaki Windows PowerShell derlemeler, iş akışı etkin etkinlikleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a8b22-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8b22-105">Bir XAML iş akışı iş akışı için Yardım sağlamak istiyorsanız, bir modül olarak paketlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8b22-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="a8b22-106">Modüller hakkında daha fazla bilgi için bkz. [bir Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="a8b22-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="a8b22-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="a8b22-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="a8b22-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="a8b22-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="a8b22-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="a8b22-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="a8b22-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="a8b22-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="a8b22-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="a8b22-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="a8b22-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="a8b22-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="a8b22-113">Aşağıdaki konularda, Windows PowerShell etkinliklerini kullanarak bir iş akışı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8b22-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="a8b22-114">Windows PowerShell etkinlikler Visual Studio araç kutusuna ekleme</span><span class="sxs-lookup"><span data-stu-id="a8b22-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="a8b22-115">Windows PowerShell etkinlikleriyle iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8b22-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="a8b22-116">Bir Windows PowerShell komut dosyası kullanarak bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8b22-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="a8b22-117">İçeri aktarma ve bir Windows PowerShell iş akışı çağırma</span><span class="sxs-lookup"><span data-stu-id="a8b22-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="a8b22-118">Bir Windows PowerShell Cmdlet'inden bir iş akışı etkinliği oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8b22-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)