---
title: GetProcessSample01 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849500"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="0842e-102">GetProcessSample01 Örneği</span><span class="sxs-lookup"><span data-stu-id="0842e-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="0842e-103">Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0842e-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="0842e-104">Bu cmdlet, Basitleştirilmiş bir sürümüdür `Get-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0842e-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="0842e-105">Visual Studio kullanarak örneği oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="0842e-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="0842e-106">Windows PowerShell 2.0 yüklü SDK ile GetProcessSample01 klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="0842e-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="0842e-107">C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01 varsayılan konumdur.</span><span class="sxs-lookup"><span data-stu-id="0842e-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="0842e-108">Çözüm (.sln) dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0842e-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="0842e-109">Bu örnek projeyi Microsoft Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="0842e-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="0842e-110">İçinde **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="0842e-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="0842e-111">Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0842e-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="0842e-112">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0842e-112">How to run the sample</span></span>

1. <span data-ttu-id="0842e-113">Bir Komut İstemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="0842e-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="0842e-114">Örnek .dll dosyasını içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="0842e-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="0842e-115">InstallUtil "GetProcessSample01.dll" çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0842e-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="0842e-116">Windows PowerShell’i başlatın.</span><span class="sxs-lookup"><span data-stu-id="0842e-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="0842e-117">Shell ek bileşenini eklemek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0842e-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="0842e-118">Cmdlet'i çalıştırmak için aşağıdaki komutu girin.</span><span class="sxs-lookup"><span data-stu-id="0842e-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="0842e-119">Aşağıdaki adımları sonuçları bir örnek çıktı budur.</span><span class="sxs-lookup"><span data-stu-id="0842e-119">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="0842e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0842e-120">Requirements</span></span>

<span data-ttu-id="0842e-121">Bu örnek, Windows PowerShell 1.0 veya üstü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0842e-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0842e-122">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="0842e-122">Demonstrates</span></span>

<span data-ttu-id="0842e-123">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="0842e-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0842e-124">Temel örnek bir cmdlet oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="0842e-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="0842e-125">Cmdlet'i bir sınıf Cmdlet özniteliği kullanılarak tanımlama.</span><span class="sxs-lookup"><span data-stu-id="0842e-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="0842e-126">Windows PowerShell 1.0 ve Windows PowerShell 2.0 ile çalışan bir ek bileşenini oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="0842e-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="0842e-127">Bunlar Windows PowerShell 2.0 gerektirir böylece sonraki örnekleri modülleri ek bileşenler yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="0842e-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="0842e-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="0842e-128">Example</span></span>

<span data-ttu-id="0842e-129">Bu örnek, basit bir cmdlet ve ek bileşenini nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0842e-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="0842e-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0842e-130">See Also</span></span>

[<span data-ttu-id="0842e-131">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="0842e-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)