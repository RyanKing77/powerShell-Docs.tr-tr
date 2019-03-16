---
title: Cmdlet kod örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056269"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="ed706-102">Cmdlet Kodu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ed706-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="ed706-103">Bu bölümde, kendi cmdlet'leri yazmaya başlamak için kullanabileceğiniz cmdlet kod örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ed706-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed706-104">Cmdlet'leri yazmak için adım adım yönergeler isterseniz bkz [yazma cmdlet'leri için öğreticiler](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="ed706-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ed706-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ed706-105">In This Section</span></span>

<span data-ttu-id="ed706-106">[Basit bir Cmdlet yazma](./how-to-write-a-simple-cmdlet.md) Bu örnek cmdlet kod temel yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed706-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="ed706-107">[Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md) Bu örnekte, farklı türde parametreleri bildirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed706-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="ed706-108">[Parametre bildirmek ayarlar nasıl](./how-to-declare-parameter-sets.md) Bu örnek, bir cmdlet gerçekleştiren eylem değiştirebilirsiniz parametreleri kümelerini nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed706-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="ed706-109">[Parametresi giriş doğrulama için nasıl](./how-to-validate-parameter-input.md) Bu örnekler, parametre girişi doğrulama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed706-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="ed706-110">[Dinamik parametreleri bildirmek için nasıl](./how-to-declare-dynamic-parameters.md) Bu örnek, çalışma zamanında eklenen bir parametre bildirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed706-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="ed706-111">[Çağırma betikleri içinde bir cmdlet'e nasıl](./how-to-invoke-scripts-within-a-cmdlet.md) Bu örnek, bir cmdlet için sağlanan bir betik çağırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed706-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="ed706-112">[Giriş işleme yöntemleri geçersiz kılmak için nasıl](./how-to-override-input-processing-methods.md) Bu örnekler BeginProcessing ProcessRecord ve EndProcessing yöntemleri geçersiz kılmak için kullanılan temel yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed706-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="ed706-113">[Nasıl destek ShouldProcess çağrısı](./how-to-request-confirmations.md) Bu örnek gösterir nasıl [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntem bir cmdlet çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed706-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="ed706-114">[Destek işlemleri nasıl](./how-to-support-transactions.md) cmdlet işlemleri desteklediğini göstermek ve cmdlet bir işlem içinde kullanıldığında alınmış eylemi uygulamak Bu örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed706-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="ed706-115">[Destek işleri nasıl](./how-to-support-jobs.md) Bu örnek cmdlet yazdığınızda işleri desteklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed706-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="ed706-116">[Bir Cmdlet gelen içinde bir Cmdlet çağırmak nasıl](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) Bu örnek içinde geliştirdiğiniz cmdlet'e çağrılan cmdlet işlevselliğini eklemenizi sağlayan başka bir cmdlet cmdlet'inden çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed706-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed706-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ed706-117">See Also</span></span>

[<span data-ttu-id="ed706-118">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="ed706-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
