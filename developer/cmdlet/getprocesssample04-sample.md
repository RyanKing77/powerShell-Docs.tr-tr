---
title: GetProcessSample04 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068037"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="0fb08-102">GetProcessSample04 Örneği</span><span class="sxs-lookup"><span data-stu-id="0fb08-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="0fb08-103">Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0fb08-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="0fb08-104">Bir işlem alınırken bir hata oluşması halinde olmak üzere sonlandırmasız bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0fb08-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="0fb08-105">Bu cmdlet, Basitleştirilmiş bir sürümüdür `Get-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0fb08-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="0fb08-106">Visual Studio kullanarak örneği oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="0fb08-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="0fb08-107">Windows PowerShell 2.0 yüklü SDK ile GetProcessSample04 klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="0fb08-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="0fb08-108">C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04 varsayılan konumdur.</span><span class="sxs-lookup"><span data-stu-id="0fb08-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="0fb08-109">Çözüm (.sln) dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0fb08-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="0fb08-110">Bu örnek projeyi Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="0fb08-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="0fb08-111">İçinde **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="0fb08-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="0fb08-112">Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fb08-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="0fb08-113">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0fb08-113">How to run the sample</span></span>

1. <span data-ttu-id="0fb08-114">Aşağıdaki modül klasörü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0fb08-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="0fb08-115">Örnek derleme modülü klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0fb08-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="0fb08-116">Windows PowerShell’i başlatın.</span><span class="sxs-lookup"><span data-stu-id="0fb08-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="0fb08-117">Windows PowerShell içinde derlemesini yüklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0fb08-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="0fb08-118">Cmdlet'i çalıştırmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0fb08-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="0fb08-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0fb08-119">Requirements</span></span>

<span data-ttu-id="0fb08-120">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0fb08-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0fb08-121">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="0fb08-121">Demonstrates</span></span>

<span data-ttu-id="0fb08-122">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fb08-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0fb08-123">Cmdlet özniteliğini kullanarak cmdlet'i sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="0fb08-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="0fb08-124">Parametre özniteliği kullanarak bir cmdlet parametresi bildirme.</span><span class="sxs-lookup"><span data-stu-id="0fb08-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="0fb08-125">Parametre konumu belirtme.</span><span class="sxs-lookup"><span data-stu-id="0fb08-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="0fb08-126">Parametresi ardışık düzen tarafından giriş alan belirtilmesi.</span><span class="sxs-lookup"><span data-stu-id="0fb08-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="0fb08-127">Giriş bir nesne veya bir parametre adı ile aynı özellik adı olan bir nesnenin bir özellik değerinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="0fb08-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="0fb08-128">Giriş parametresi için bir doğrulama özniteliği bildirme.</span><span class="sxs-lookup"><span data-stu-id="0fb08-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="0fb08-129">Olmak üzere sonlandırmasız bir hata ve hata akışına bir hata iletisi yazmak.</span><span class="sxs-lookup"><span data-stu-id="0fb08-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="0fb08-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="0fb08-130">Example</span></span>

<span data-ttu-id="0fb08-131">Bu örnek, bir cmdlet'i olmak üzere sonlandırmasız hatalar işleme ve hata iletileri hata akışa Yazar oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0fb08-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="0fb08-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0fb08-132">See Also</span></span>

[<span data-ttu-id="0fb08-133">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="0fb08-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
