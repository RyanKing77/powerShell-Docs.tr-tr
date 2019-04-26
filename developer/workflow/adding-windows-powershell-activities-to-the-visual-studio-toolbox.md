---
title: Windows PowerShell etkinlikler Visual Studio araç kutusuna ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080484"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="9833e-102">Visual Studio Toolbox’a Windows PowerShell Etkinlikleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="9833e-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="9833e-103">PowerShell iş akışı Tasarımcısı kullanarak iş akışı yazmadan önce araç kutusundan bir Visual Studio iş akışı konsol uygulaması projesi için önce PowerShell etkinlikleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9833e-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="9833e-104">Aşağıdaki yordam etkinlikleri Microsoft.PowerShell.Core.Activities derlemeden Visual Studio araç kutusuna ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="9833e-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="9833e-105">Windows PowerShell etkinlikler Araç Kutusu'na ekleme</span><span class="sxs-lookup"><span data-stu-id="9833e-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="9833e-106">Visual Studio'da yeni bir iş akışı konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9833e-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="9833e-107">Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="9833e-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="9833e-108">Araç kutusu içinde sağ tıklatıp araç kutusunda yeni bir sekme eklemek **Sekme Ekle**ve yeni sekmenin "PowerShell etkinlikleri" gibi bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="9833e-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="9833e-109">Bir sekme ekleme, PowerShell etkinlikler araç kutusundaki başka araçlar ayrı gruplamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9833e-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="9833e-110">Yeni araç kutusu sekmesine tıklayın **öğelerini Seç...** . **Araç kutusu öğelerini Seç** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9833e-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="9833e-111">İçinde **araç kutusu öğelerini Seç** iletişim kutusunda, tıklayın **System.Activities** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9833e-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="9833e-112">Tıklayın **Gözat**.</span><span class="sxs-lookup"><span data-stu-id="9833e-112">Click **Browse**.</span></span>

7. <span data-ttu-id="9833e-113">%WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e klasöre gidin ve Microsoft.PowerShell.Core.Activities.dll çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9833e-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="9833e-114">**Tamam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9833e-114">Click **OK**.</span></span> <span data-ttu-id="9833e-115">Microsoft.PowerShell.Core.Activities derlemesi tarafından tanımlanan etkinlikler araç kutusundan kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9833e-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="9833e-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9833e-116">See Also</span></span>

[<span data-ttu-id="9833e-117">Bir Windows PowerShell iş akışı yazma</span><span class="sxs-lookup"><span data-stu-id="9833e-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="9833e-118">Windows PowerShell etkinlikleriyle iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="9833e-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)