---
title: GetProcessSample03 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068054"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="f0539-102">GetProcessSample03 Örneği</span><span class="sxs-lookup"><span data-stu-id="f0539-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="f0539-103">Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0539-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="f0539-104">Sağladığı bir `Name` ardışık düzendeki bir nesne veya özellik adı parametre adı ile aynı olan bir nesnenin bir özelliğine bir değer alabilen bir parametre.</span><span class="sxs-lookup"><span data-stu-id="f0539-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="f0539-105">Bu cmdlet, Basitleştirilmiş bir sürümüdür `Get-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="f0539-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="f0539-106">Visual Studio kullanarak örneği oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="f0539-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="f0539-107">Windows PowerShell 2.0 yüklü SDK ile GetProcessSample03 klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="f0539-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="f0539-108">C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03 varsayılan konumdur.</span><span class="sxs-lookup"><span data-stu-id="f0539-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="f0539-109">Çözüm (.sln) dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f0539-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="f0539-110">Bu örnek projeyi Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="f0539-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="f0539-111">İçinde **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="f0539-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="f0539-112">Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f0539-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="f0539-113">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f0539-113">How to run the sample</span></span>

1. <span data-ttu-id="f0539-114">Aşağıdaki modül klasörü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f0539-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="f0539-115">Örnek derleme modülü klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f0539-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="f0539-116">Windows PowerShell’i başlatın.</span><span class="sxs-lookup"><span data-stu-id="f0539-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="f0539-117">Windows PowerShell içinde derlemesini yüklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f0539-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="f0539-118">Cmdlet'i çalıştırmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f0539-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="f0539-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0539-119">Requirements</span></span>

<span data-ttu-id="f0539-120">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f0539-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f0539-121">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="f0539-121">Demonstrates</span></span>

<span data-ttu-id="f0539-122">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0539-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="f0539-123">Cmdlet özniteliğini kullanarak cmdlet'i sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="f0539-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="f0539-124">Parametre özniteliği kullanarak bir cmdlet parametresi bildirme.</span><span class="sxs-lookup"><span data-stu-id="f0539-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="f0539-125">Parametre konumu belirtme.</span><span class="sxs-lookup"><span data-stu-id="f0539-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="f0539-126">Parametresi ardışık düzen tarafından giriş alan belirtilmesi.</span><span class="sxs-lookup"><span data-stu-id="f0539-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="f0539-127">Giriş bir nesne veya bir parametre adı ile aynı özellik adı olan bir nesnenin bir özellik değerinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="f0539-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="f0539-128">Giriş parametresi için bir doğrulama özniteliği bildirme.</span><span class="sxs-lookup"><span data-stu-id="f0539-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="f0539-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0539-129">Example</span></span>

<span data-ttu-id="f0539-130">Bu örnek, Get-Proc cmdlet'inin içeren bir uygulama gösterir. bir `Name` ardışık düzendeki girişi kabul eden bir parametre.</span><span class="sxs-lookup"><span data-stu-id="f0539-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="f0539-131">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f0539-131">See Also</span></span>

[<span data-ttu-id="f0539-132">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="f0539-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
