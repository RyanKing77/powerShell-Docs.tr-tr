---
title: Cmdlet yöntemleri işleme giriş | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059380"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="6259b-102">Cmdlet Giriş İşleme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6259b-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="6259b-103">Cmdlet'leri bir veya daha fazla işleme işlerini yapmak için bu konuda açıklanan yöntemlerden giriş geçersiz kılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6259b-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="6259b-104">Bu yöntemler, ön işleme işlemleri, giriş işleme ve sonrası işleme gerçekleştirmek cmdlet sağlar.</span><span class="sxs-lookup"><span data-stu-id="6259b-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="6259b-105">Bu yöntemleri Ayrıca, cmdlet işlemeyi durdur olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6259b-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="6259b-106">Ön işleme görevleri</span><span class="sxs-lookup"><span data-stu-id="6259b-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="6259b-107">Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) cmdlet tarafından işlenen daha sonra tüm kayıtlar için geçerli olan herhangi bir ön işleme işlemi eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6259b-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="6259b-108">Windows PowerShell komut işlem hattı işlediğinde, Windows PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="6259b-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="6259b-109">Nasıl Windows PowerShell komut işlem hattını çağıran hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="6259b-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="6259b-110">Aşağıdaki kod uygulanışı gösterilmektedir [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6259b-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="6259b-111">Nasıl kullanılacağı hakkında daha ayrıntılı bir örnek için [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) yöntemi bkz [SelectStr öğretici](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6259b-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="6259b-112">Bu öğreticide **seçin Str** cmdlet'ini kullanır [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) kayıtları işleme giriş aramak için kullanılan normal ifade oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6259b-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="6259b-113">Giriş işleme görevleri</span><span class="sxs-lookup"><span data-stu-id="6259b-113">Input Processing Tasks</span></span>

<span data-ttu-id="6259b-114">Cmdlet'leri geçersiz kılma [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) cmdlet'e gönderilen girişi işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6259b-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="6259b-115">Windows PowerShell komut işlem hattı işlediğinde, Windows PowerShell cmdlet tarafından işlenen her giriş kaydı için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="6259b-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="6259b-116">Nasıl Windows PowerShell komut işlem hattını çağıran hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="6259b-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="6259b-117">Aşağıdaki kod uygulanışı gösterilmektedir [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6259b-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="6259b-118">Nasıl kullanılacağı hakkında daha ayrıntılı bir örnek için [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi bkz [SelectStr öğretici](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6259b-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="6259b-119">İşlem Sonrası görevler</span><span class="sxs-lookup"><span data-stu-id="6259b-119">Post-Processing Tasks</span></span>

<span data-ttu-id="6259b-120">Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) cmdlet tarafından işlenen tüm kayıtlar için geçerli olan herhangi bir işlem sonrası işlemi eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6259b-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="6259b-121">Örneğin, nesne değişkenleri bittikten sonra temizleme cmdlet'inize olabilir işleme.</span><span class="sxs-lookup"><span data-stu-id="6259b-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="6259b-122">Windows PowerShell komut işlem hattı işlediğinde, Windows PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="6259b-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="6259b-123">Ancak, Windows PowerShell çalışma zamanı olmayan çağrı unutmamak gerekir [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) yöntemi cmdlet midway, giriş işleme üzerinden iptal edilir ya da bir sonlandırma, herhangi bir bölümünü cmdlet'i hata meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="6259b-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="6259b-124">Bu nedenle, nesne temizleme gerektiren bir cmdlet tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) desen, bir sonlandırıcı dahil olmak üzere çalışma zamanı, her ikisi de çağırabilirsiniz [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) ve [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) işleme sonunda yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6259b-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="6259b-125">Nasıl Windows PowerShell komut işlem hattını çağıran hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="6259b-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="6259b-126">Aşağıdaki kod uygulanışı gösterilmektedir [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6259b-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="6259b-127">Nasıl kullanılacağı hakkında daha ayrıntılı bir örnek için [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi bkz [SelectStr öğretici](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6259b-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6259b-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6259b-128">See Also</span></span>

[<span data-ttu-id="6259b-129">System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty tam adı =</span><span class="sxs-lookup"><span data-stu-id="6259b-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="6259b-130">System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty tam adı =</span><span class="sxs-lookup"><span data-stu-id="6259b-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="6259b-131">System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty tam adı =</span><span class="sxs-lookup"><span data-stu-id="6259b-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="6259b-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="6259b-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="6259b-133">Windows PowerShell Kabuk SDK'sı</span><span class="sxs-lookup"><span data-stu-id="6259b-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
