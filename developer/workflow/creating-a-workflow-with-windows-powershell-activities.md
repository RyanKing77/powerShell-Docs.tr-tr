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
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845041"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="14c01-102">Windows PowerShell Etkinlikleri ile İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="14c01-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="14c01-103">Bir Windows PowerShell iş akışı etkinlikleri Visual Studio araç kutusundan seçip iş akışı Tasarımcısı penceresine sürükleyerek oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14c01-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="14c01-104">Windows PowerShell etkinlikler Visual Studio araç kutusuna ekleme hakkında daha fazla bilgi için bkz: [ekleyerek Windows PowerShell etkinlikler Visual Studio araç kutusu](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="14c01-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="14c01-105">Aşağıdaki yordamlar, kullanıcı tarafından belirtilen bilgisayarlar etki alanı durumunu denetler, zaten birleştirilmemiş ve sonra durumu yeniden denetler bunları bir etki alanına katılan bir iş akışının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="14c01-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="14c01-106">Projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="14c01-106">Setting up the Project</span></span>

1. <span data-ttu-id="14c01-107">Verilen yordamı izleyin [ekleyerek Windows PowerShell etkinlikler Visual Studio araç kutusu](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) bir iş akışı projesi oluşturun ve etkinlikler eklemek için [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) ve [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) araç kutusu derlemeler.</span><span class="sxs-lookup"><span data-stu-id="14c01-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="14c01-108">System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities ve Microsoft.PowerShell.Commands.Management proje için başvuru bütünleştirilmiş kodları olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c01-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="14c01-109">İş akışına etkinlikler ekleme</span><span class="sxs-lookup"><span data-stu-id="14c01-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="14c01-110">Ekleme bir **dizisi** iş akışı için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="14c01-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="14c01-111">Adlandırılmış bağımsız değişken oluşturma `ComputerName` türünde bir bağımsız değişken ile `String[]`.</span><span class="sxs-lookup"><span data-stu-id="14c01-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="14c01-112">Bu bağımsız değişken denetleyip katılmak için bilgisayarların adlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14c01-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="14c01-113">Adlandırılmış bağımsız değişken oluşturma `DomainCred` türü [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="14c01-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="14c01-114">Bu bağımsız değişken, bir bilgisayarın etki alanına katılmasını sağlamak için yetkili bir etki alanı hesabı etki alanı kimlik bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14c01-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="14c01-115">Adlandırılmış bağımsız değişken oluşturma `MachineCred` türü [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="14c01-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="14c01-116">Bu bağımsız değişken denetleyip katılmak için bilgisayarlarda yönetici kimlik bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14c01-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="14c01-117">Ekleme bir **ParallelForEach** etkinliği içinde **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="14c01-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="14c01-118">Girin `comp` ve `ComputerName` içinde döngü öğeleri yinelenir. böylece, metin kutuları `ComputerName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="14c01-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="14c01-119">Ekleme bir **dizisi** body etkinlik **ParallelForEach** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="14c01-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="14c01-120">Ayarlama **DisplayName** özelliği dizinin `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="14c01-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="14c01-121">Ekleme bir **GetWmiObject** etkinliğini **JoinDomain** dizisi.</span><span class="sxs-lookup"><span data-stu-id="14c01-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="14c01-122">Özelliklerini düzenlemek **GetWmiObject** etkinlik aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="14c01-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="14c01-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="14c01-123">Property</span></span>|<span data-ttu-id="14c01-124">Değer</span><span class="sxs-lookup"><span data-stu-id="14c01-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="14c01-125">**Sınıfı**</span><span class="sxs-lookup"><span data-stu-id="14c01-125">**Class**</span></span>|<span data-ttu-id="14c01-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="14c01-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="14c01-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="14c01-127">**PSComputerName**</span></span>|<span data-ttu-id="14c01-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="14c01-128">{comp}</span></span>|
   |<span data-ttu-id="14c01-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="14c01-129">**PSCredential**</span></span>|<span data-ttu-id="14c01-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="14c01-130">MachineCred</span></span>|

9. <span data-ttu-id="14c01-131">Ekleme bir **AddComputer** etkinliğini **JoinDomain** sonra sıra **GetWmiObject** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="14c01-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="14c01-132">Özelliklerini düzenlemek **AddComputer** etkinlik aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="14c01-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="14c01-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="14c01-133">Property</span></span>|<span data-ttu-id="14c01-134">Değer</span><span class="sxs-lookup"><span data-stu-id="14c01-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="14c01-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="14c01-135">**ComputerName**</span></span>|<span data-ttu-id="14c01-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="14c01-136">{comp}</span></span>|
    |<span data-ttu-id="14c01-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="14c01-137">**DomainCredential**</span></span>|<span data-ttu-id="14c01-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="14c01-138">DomainCred</span></span>|

11. <span data-ttu-id="14c01-139">Ekleme bir **RestartComputer** etkinliğini **JoinDomain** sonra sıra **AddComputer** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="14c01-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="14c01-140">Özelliklerini düzenlemek **RestartComputer** etkinlik aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="14c01-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="14c01-141">Özellik</span><span class="sxs-lookup"><span data-stu-id="14c01-141">Property</span></span>|<span data-ttu-id="14c01-142">Değer</span><span class="sxs-lookup"><span data-stu-id="14c01-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="14c01-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="14c01-143">**ComputerName**</span></span>|<span data-ttu-id="14c01-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="14c01-144">{comp}</span></span>|
    |<span data-ttu-id="14c01-145">**Kimlik bilgisi**</span><span class="sxs-lookup"><span data-stu-id="14c01-145">**Credential**</span></span>|<span data-ttu-id="14c01-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="14c01-146">MachineCred</span></span>|
    |<span data-ttu-id="14c01-147">**için**</span><span class="sxs-lookup"><span data-stu-id="14c01-147">**For**</span></span>|<span data-ttu-id="14c01-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="14c01-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="14c01-149">**Zorla**</span><span class="sxs-lookup"><span data-stu-id="14c01-149">**Force**</span></span>|<span data-ttu-id="14c01-150">True</span><span class="sxs-lookup"><span data-stu-id="14c01-150">True</span></span>|
    |<span data-ttu-id="14c01-151">bekleme</span><span class="sxs-lookup"><span data-stu-id="14c01-151">Wait</span></span>|<span data-ttu-id="14c01-152">True</span><span class="sxs-lookup"><span data-stu-id="14c01-152">True</span></span>|
    |<span data-ttu-id="14c01-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="14c01-153">PSComputerName</span></span>|<span data-ttu-id="14c01-154">{""}</span><span class="sxs-lookup"><span data-stu-id="14c01-154">{""}</span></span>|

13. <span data-ttu-id="14c01-155">Ekleme bir **GetWmiObject** etkinliğini **JoinDomain** sonra sıra **RestartComputer** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="14c01-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="14c01-156">Önceki olarak aynı olacak şekilde özelliklerini düzenleme **GetWmiObject** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="14c01-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="14c01-157">Yordamları tamamladıktan sonra iş akışı tasarım penceresini aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="14c01-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="14c01-158">![İş Akışı Tasarımcısı'nda JoinDomain XAML](../media/joindomainworkflow.png)
    ![JoinDomain XAML iş akışı Tasarımcısı'nda](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="14c01-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>