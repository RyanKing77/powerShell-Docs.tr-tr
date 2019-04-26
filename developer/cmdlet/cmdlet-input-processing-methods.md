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
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068496"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="a36df-102">Cmdlet Giriş İşleme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a36df-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="a36df-103">Cmdlet'leri bir veya daha fazla işleme işlerini yapmak için bu konuda açıklanan yöntemlerden giriş geçersiz kılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a36df-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="a36df-104">Bu yöntemler, ön işleme, giriş işleme ve sonrası işleme işlemlerini gerçekleştirmek cmdlet sağlar.</span><span class="sxs-lookup"><span data-stu-id="a36df-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="a36df-105">Bu yöntemleri Ayrıca, cmdlet işlemeyi durdur olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a36df-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="a36df-106">Bu yöntemleri kullanma hakkında daha ayrıntılı örnek için bkz [SelectStr öğretici](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a36df-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="a36df-107">Ön işleme işlemleri</span><span class="sxs-lookup"><span data-stu-id="a36df-107">Pre-Processing Operations</span></span>

<span data-ttu-id="a36df-108">Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cmdlet tarafından işlenen daha sonra tüm kayıtlar için geçerli olan herhangi bir ön işleme işlemi eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a36df-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="a36df-109">PowerShell komut işlem hattı işlediğinde, PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="a36df-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="a36df-110">PowerShell komut ardışık düzeni nasıl çağırır hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="a36df-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="a36df-111">Aşağıdaki kod, BeginProcessing yöntemi uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a36df-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="a36df-112">İşleme giriş</span><span class="sxs-lookup"><span data-stu-id="a36df-112">Input Processing Operations</span></span>

<span data-ttu-id="a36df-113">Cmdlet'leri geçersiz kılma [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet'e gönderilen girişi işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a36df-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="a36df-114">PowerShell komut işlem hattı işlediğinde, PowerShell cmdlet tarafından işlenen her giriş kaydı için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a36df-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="a36df-115">PowerShell komut ardışık düzeni nasıl çağırır hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="a36df-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="a36df-116">Aşağıdaki kod, ProcessRecord yöntemi uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a36df-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="a36df-117">İşlem Sonrası işlemleri</span><span class="sxs-lookup"><span data-stu-id="a36df-117">Post-Processing Operations</span></span>

<span data-ttu-id="a36df-118">Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet tarafından işlenen tüm kayıtlar için geçerli olan herhangi bir işlem sonrası işlemi eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a36df-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="a36df-119">Örneğin, nesne değişkenleri bittikten sonra temizleme cmdlet'inize olabilir işleme.</span><span class="sxs-lookup"><span data-stu-id="a36df-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="a36df-120">PowerShell komut işlem hattı işlediğinde, PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="a36df-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="a36df-121">Bununla birlikte, PowerShell çalışma zamanı EndProcessing yöntemi cmdlet midway kendi giriş işlemeden iptal edilirse veya herhangi bir bölümünü cmdlet'i bir sonlandırmalı hata oluşması durumunda çağırmayacaktır olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a36df-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="a36df-122">Bu nedenle, nesne temizleme gerektiren bir cmdlet tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) desen, bir sonlandırıcı dahil olmak üzere çalışma zamanı, her iki EndProcessing çağırabilirsiniz ve [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) işleme sonunda yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a36df-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="a36df-123">PowerShell komut ardışık düzeni nasıl çağırır hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="a36df-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="a36df-124">Aşağıdaki kod, EndProcessing yöntemi uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a36df-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="a36df-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a36df-125">See Also</span></span>

[<span data-ttu-id="a36df-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="a36df-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="a36df-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="a36df-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="a36df-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="a36df-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="a36df-129">SelectStr Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="a36df-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="a36df-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="a36df-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="a36df-131">Windows PowerShell Kabuk SDK'sı</span><span class="sxs-lookup"><span data-stu-id="a36df-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
