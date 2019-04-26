---
title: Bir Windows PowerShell komut dosyası kullanarak bir iş akışı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080382"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="96848-102">Windows PowerShell Betiği Kullanarak İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96848-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="96848-103">Bir Windows PowerShell komut dosyasını yazmayarak bir iş akışı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96848-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="96848-104">Bir iş akışı oluşturmak için betik gövdesi önce iş akışı için bir ad tarafından izlenen iş akışı anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="96848-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="96848-105">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="96848-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="96848-106">İş akışı, herhangi bir Windows PowerShell komutu olduğu aynı şekilde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96848-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="96848-107">Paralel ve sıralı uygulama</span><span class="sxs-lookup"><span data-stu-id="96848-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="96848-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) paralel etkinliklerin yürütülmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="96848-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="96848-109">Bu özellik bir Windows PowerShell komut dosyası uygulamak `parallel` anahtar sözcüğü bir betik bloğu önünde.</span><span class="sxs-lookup"><span data-stu-id="96848-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="96848-110">Ayrıca `foreach -parallel` paralel nesnelerden oluşan bir koleksiyon üzerinden yineleme yapmak için yapı.</span><span class="sxs-lookup"><span data-stu-id="96848-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="96848-111">Bir grup etkinlik paralel bloğu içinde sırayla yürütmek için betik bloğunda etkinlikleri grubu alın ve blok dizisi anahtar sözcüğü ile koyun.</span><span class="sxs-lookup"><span data-stu-id="96848-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="96848-112">Bilgisayar bir etki alanına katma</span><span class="sxs-lookup"><span data-stu-id="96848-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="96848-113">Aşağıdaki betik, bir grup kullanıcı tarafından belirtilen bir bilgisayar etki alanı durumunu denetler, zaten birleştirilmemiş ve sonra durumu yeniden denetler bunları bir etki alanına katılan bir iş akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96848-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="96848-114">Bu, açıklandığı bir XAML iş akışı betiği sürümüdür [Windows PowerShell etkinlikleriyle iş akışı oluşturma](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="96848-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```