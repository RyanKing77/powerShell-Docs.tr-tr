---
title: Geçersiz kılma yöntemleri işleme giriş | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846756"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="2626d-102">Giriş İşleme Yöntemlerini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="2626d-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="2626d-103">Bu örnekler, bir cmdlet yöntemlerinde işleme giriş üzerine gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2626d-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="2626d-104">Bu yöntemleri aşağıdaki işlemleri gerçekleştirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="2626d-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="2626d-105">[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi, cmdlet tarafından işlenen tüm nesneleri için geçerli olan tek seferlik başlatma işlemlerini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2626d-105">The [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="2626d-106">Windows PowerShell çalışma zamanı bu yöntemi yalnızca bir defa çağırır.</span><span class="sxs-lookup"><span data-stu-id="2626d-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="2626d-107">[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi cmdlet'e geçirilen nesneleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2626d-107">The [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="2626d-108">Windows PowerShell çalışma zamanı, cmdlet'e geçirilen her nesne için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="2626d-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="2626d-109">[System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi, tek seferlik post işlemleri gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2626d-109">The [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="2626d-110">Windows PowerShell çalışma zamanı bu yöntemi yalnızca bir defa çağırır.</span><span class="sxs-lookup"><span data-stu-id="2626d-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="2626d-111">BeginProcessing yöntemi geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="2626d-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="2626d-112">Korumalı bir geçersiz kılma bildirmek [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2626d-112">Declare a protected override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="2626d-113">Aşağıdaki sınıftan bir örnek ileti yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2626d-113">The following class prints a sample message.</span></span> <span data-ttu-id="2626d-114">Bu sınıf kullanmak için fiil ve isim cmdlet'i özniteliğinde, yeni fiil ve isim yansıtmak için sınıfın adını değiştirmek ve ihtiyaç duyduğunuz işlevsellik için geçersiz kılmasını eklersiniz [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2626d-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="2626d-115">ProcessRecord yöntemi geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="2626d-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="2626d-116">Korumalı bir geçersiz kılma bildirmek [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2626d-116">Declare a protected override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="2626d-117">Aşağıdaki sınıftan bir örnek ileti yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2626d-117">The following class prints a sample message.</span></span> <span data-ttu-id="2626d-118">Bu sınıf kullanmak için fiil ve isim cmdlet'i özniteliğinde, yeni fiil ve isim yansıtmak için sınıfın adını değiştirmek ve ihtiyaç duyduğunuz işlevsellik için geçersiz kılmasını eklersiniz [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2626d-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="2626d-119">EndProcessing yöntemi geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="2626d-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="2626d-120">Korumalı bir geçersiz kılma bildirmek [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2626d-120">Declare a protected override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="2626d-121">Aşağıdaki sınıftan bir örnek yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2626d-121">The following class prints a sample.</span></span> <span data-ttu-id="2626d-122">Bu sınıf kullanmak için fiil ve isim cmdlet'i özniteliğinde, yeni fiil ve isim yansıtmak için sınıfın adını değiştirmek ve ihtiyaç duyduğunuz işlevsellik için geçersiz kılmasını eklersiniz [System.Management.Automation.Cmdlet.Endprocessing\* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2626d-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="2626d-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2626d-123">See Also</span></span>

[<span data-ttu-id="2626d-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="2626d-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="2626d-125">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="2626d-125">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="2626d-126">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="2626d-126">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="2626d-127">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="2626d-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)