---
title: GetProcessSample02 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068088"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="849a3-102">GetProcessSample02 Örneği</span><span class="sxs-lookup"><span data-stu-id="849a3-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="849a3-103">Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="849a3-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="849a3-104">Sağladığı bir `Name` alınacak işlemleri belirtmek için kullanılan parametre.</span><span class="sxs-lookup"><span data-stu-id="849a3-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="849a3-105">Bu cmdlet, Basitleştirilmiş bir sürümüdür `Get-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="849a3-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="849a3-106">Visual Studio kullanarak örneği oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="849a3-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="849a3-107">Windows PowerShell 2.0 yüklü SDK ile GetProcessSample02 klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="849a3-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="849a3-108">C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02 varsayılan konumdur.</span><span class="sxs-lookup"><span data-stu-id="849a3-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="849a3-109">Çözüm (.sln) dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="849a3-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="849a3-110">Bu örnek projeyi Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="849a3-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="849a3-111">İçinde **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="849a3-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="849a3-112">Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="849a3-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="849a3-113">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="849a3-113">How to run the sample</span></span>

1. <span data-ttu-id="849a3-114">Aşağıdaki modül klasörü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="849a3-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="849a3-115">Örnek derleme modülü klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="849a3-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="849a3-116">Windows PowerShell’i başlatın.</span><span class="sxs-lookup"><span data-stu-id="849a3-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="849a3-117">Windows PowerShell içinde derlemesini yüklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="849a3-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="849a3-118">Cmdlet'i çalıştırmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="849a3-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="849a3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="849a3-119">Requirements</span></span>

<span data-ttu-id="849a3-120">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="849a3-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="849a3-121">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="849a3-121">Demonstrates</span></span>

<span data-ttu-id="849a3-122">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="849a3-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="849a3-123">Cmdlet özniteliğini kullanarak cmdlet'i sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="849a3-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="849a3-124">Parametre özniteliği kullanarak bir cmdlet parametresi bildirme.</span><span class="sxs-lookup"><span data-stu-id="849a3-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="849a3-125">Parametre konumu belirtme.</span><span class="sxs-lookup"><span data-stu-id="849a3-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="849a3-126">Giriş parametresi için bir doğrulama özniteliği bildirme.</span><span class="sxs-lookup"><span data-stu-id="849a3-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="849a3-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="849a3-127">Example</span></span>

<span data-ttu-id="849a3-128">Bu örnek, Get-Proc cmdlet'inin içeren bir uygulama gösterir. bir `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="849a3-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

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
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
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
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="849a3-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="849a3-129">See Also</span></span>

[<span data-ttu-id="849a3-130">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="849a3-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
