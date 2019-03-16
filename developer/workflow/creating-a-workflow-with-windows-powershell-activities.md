---
title: Windows PowerShell etkinlikleriyle iş akışı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055436"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="2e490-102">Windows PowerShell Etkinlikleri ile İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e490-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="2e490-103">Bir Windows PowerShell iş akışı etkinlikleri Visual Studio araç kutusundan seçip iş akışı Tasarımcısı penceresine sürükleyerek oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e490-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="2e490-104">Windows PowerShell etkinlikler Visual Studio araç kutusuna ekleme hakkında daha fazla bilgi için bkz: [ekleyerek Windows PowerShell etkinlikler Visual Studio araç kutusu](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="2e490-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="2e490-105">Aşağıdaki yordamlar, kullanıcı tarafından belirtilen bilgisayarlar etki alanı durumunu denetler, zaten birleştirilmemiş ve sonra durumu yeniden denetler bunları bir etki alanına katılan bir iş akışının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e490-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="2e490-106">Projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="2e490-106">Setting up the Project</span></span>

1. <span data-ttu-id="2e490-107">Verilen yordamı izleyin [ekleyerek Windows PowerShell etkinlikler Visual Studio araç kutusu](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) bir iş akışı projesi oluşturun ve etkinlikler eklemek için [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) ve [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) araç kutusu derlemeler.</span><span class="sxs-lookup"><span data-stu-id="2e490-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="2e490-108">System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities ve Microsoft.PowerShell.Commands.Management proje için başvuru bütünleştirilmiş kodları olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e490-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="2e490-109">İş akışına etkinlikler ekleme</span><span class="sxs-lookup"><span data-stu-id="2e490-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="2e490-110">Ekleme bir **dizisi** iş akışı için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2e490-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="2e490-111">Adlandırılmış bağımsız değişken oluşturma `ComputerName` türünde bir bağımsız değişken ile `String[]`.</span><span class="sxs-lookup"><span data-stu-id="2e490-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="2e490-112">Bu bağımsız değişken denetleyip katılmak için bilgisayarların adlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e490-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="2e490-113">Adlandırılmış bağımsız değişken oluşturma `DomainCred` türü [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="2e490-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="2e490-114">Bu bağımsız değişken, bir bilgisayarın etki alanına katılmasını sağlamak için yetkili bir etki alanı hesabı etki alanı kimlik bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e490-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="2e490-115">Adlandırılmış bağımsız değişken oluşturma `MachineCred` türü [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="2e490-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="2e490-116">Bu bağımsız değişken denetleyip katılmak için bilgisayarlarda yönetici kimlik bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e490-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="2e490-117">Ekleme bir **ParallelForEach** etkinliği içinde **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2e490-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="2e490-118">Girin `comp` ve `ComputerName` içinde döngü öğeleri yinelenir. böylece, metin kutuları `ComputerName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="2e490-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="2e490-119">Ekleme bir **dizisi** body etkinlik **ParallelForEach** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2e490-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="2e490-120">Ayarlama **DisplayName** özelliği dizinin `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="2e490-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="2e490-121">Ekleme bir **GetWmiObject** etkinliğini **JoinDomain** dizisi.</span><span class="sxs-lookup"><span data-stu-id="2e490-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="2e490-122">Özelliklerini düzenlemek **GetWmiObject** etkinlik aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="2e490-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="2e490-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="2e490-123">Property</span></span>|<span data-ttu-id="2e490-124">Değer</span><span class="sxs-lookup"><span data-stu-id="2e490-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="2e490-125">**Sınıfı**</span><span class="sxs-lookup"><span data-stu-id="2e490-125">**Class**</span></span>|<span data-ttu-id="2e490-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="2e490-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="2e490-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="2e490-127">**PSComputerName**</span></span>|<span data-ttu-id="2e490-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="2e490-128">{comp}</span></span>|
   |<span data-ttu-id="2e490-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="2e490-129">**PSCredential**</span></span>|<span data-ttu-id="2e490-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="2e490-130">MachineCred</span></span>|

9. <span data-ttu-id="2e490-131">Ekleme bir **AddComputer** etkinliğini **JoinDomain** sonra sıra **GetWmiObject** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2e490-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="2e490-132">Özelliklerini düzenlemek **AddComputer** etkinlik aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="2e490-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="2e490-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="2e490-133">Property</span></span>|<span data-ttu-id="2e490-134">Değer</span><span class="sxs-lookup"><span data-stu-id="2e490-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="2e490-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="2e490-135">**ComputerName**</span></span>|<span data-ttu-id="2e490-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="2e490-136">{comp}</span></span>|
    |<span data-ttu-id="2e490-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="2e490-137">**DomainCredential**</span></span>|<span data-ttu-id="2e490-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="2e490-138">DomainCred</span></span>|

11. <span data-ttu-id="2e490-139">Ekleme bir **RestartComputer** etkinliğini **JoinDomain** sonra sıra **AddComputer** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2e490-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="2e490-140">Özelliklerini düzenlemek **RestartComputer** etkinlik aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="2e490-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="2e490-141">Özellik</span><span class="sxs-lookup"><span data-stu-id="2e490-141">Property</span></span>|<span data-ttu-id="2e490-142">Değer</span><span class="sxs-lookup"><span data-stu-id="2e490-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="2e490-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="2e490-143">**ComputerName**</span></span>|<span data-ttu-id="2e490-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="2e490-144">{comp}</span></span>|
    |<span data-ttu-id="2e490-145">**Kimlik bilgisi**</span><span class="sxs-lookup"><span data-stu-id="2e490-145">**Credential**</span></span>|<span data-ttu-id="2e490-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="2e490-146">MachineCred</span></span>|
    |<span data-ttu-id="2e490-147">**için**</span><span class="sxs-lookup"><span data-stu-id="2e490-147">**For**</span></span>|<span data-ttu-id="2e490-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e490-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="2e490-149">**Zorla**</span><span class="sxs-lookup"><span data-stu-id="2e490-149">**Force**</span></span>|<span data-ttu-id="2e490-150">True</span><span class="sxs-lookup"><span data-stu-id="2e490-150">True</span></span>|
    |<span data-ttu-id="2e490-151">bekleme</span><span class="sxs-lookup"><span data-stu-id="2e490-151">Wait</span></span>|<span data-ttu-id="2e490-152">True</span><span class="sxs-lookup"><span data-stu-id="2e490-152">True</span></span>|
    |<span data-ttu-id="2e490-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="2e490-153">PSComputerName</span></span>|<span data-ttu-id="2e490-154">{""}</span><span class="sxs-lookup"><span data-stu-id="2e490-154">{""}</span></span>|

13. <span data-ttu-id="2e490-155">Ekleme bir **GetWmiObject** etkinliğini **JoinDomain** sonra sıra **RestartComputer** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2e490-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="2e490-156">Önceki olarak aynı olacak şekilde özelliklerini düzenleme **GetWmiObject** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2e490-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="2e490-157">Yordamları tamamladıktan sonra iş akışı tasarım penceresini aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="2e490-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="2e490-158">![İş Akışı Tasarımcısı'nda JoinDomain XAML](../media/joindomainworkflow.png)
    ![JoinDomain XAML iş akışı Tasarımcısı'nda](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="2e490-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>