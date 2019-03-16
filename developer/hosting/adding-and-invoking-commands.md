---
title: Ekleme ve bunları çağırırken komutları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057663"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="5cfca-102">Komut ekleme ve çağırma</span><span class="sxs-lookup"><span data-stu-id="5cfca-102">Adding and invoking commands</span></span>

<span data-ttu-id="5cfca-103">Bir çalışma alanı oluşturduktan sonra Windows PowerShellcommands ve komut dosyaları için bir işlem hattı ekleyin ve ardından işlem hattını zaman uyumlu veya zaman uyumsuz olarak çağırma.</span><span class="sxs-lookup"><span data-stu-id="5cfca-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="5cfca-104">Bir işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cfca-104">Creating a pipeline</span></span>

 <span data-ttu-id="5cfca-105">[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) sınıfı işlem hattının komutlar, parametreler ve betikler eklemek için çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cfca-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="5cfca-106">Bir aşırı yüklemesini çağırarak, zaman uyumlu bir işlem hattı çağırabilirsiniz [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi veya bir aşırı yüklemesini çağırarak zaman uyumsuz olarak [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) ardından [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cfca-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="5cfca-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="5cfca-107">AddCommand</span></span>

1. <span data-ttu-id="5cfca-108">Oluşturma bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="5cfca-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="5cfca-109">Yürütmek istediğiniz komut ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cfca-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="5cfca-110">Komutunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="5cfca-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="5cfca-111">Eğer [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) yöntemi çağırmadan önce birden fazla [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi, sonucu ilk komut, saniye ve benzeri cmdlet'iyle yönetilir.</span><span class="sxs-lookup"><span data-stu-id="5cfca-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="5cfca-112">Bir komut için bir önceki komutun sonucuna ilişkin kanal istemiyorsanız çağırarak ekleme [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yerine.</span><span class="sxs-lookup"><span data-stu-id="5cfca-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="5cfca-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="5cfca-113">AddParameter</span></span>

 <span data-ttu-id="5cfca-114">Önceki örnekte, hiçbir parametre olmadan tek bir komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="5cfca-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="5cfca-115">Kullanarak komutu parametreleri ekleyebilirsiniz [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) yöntemi örneğin, aşağıdaki kodu alır, tüm adlandırılmış işlemlerin listesini `PowerShell` çalıştırma Makine.</span><span class="sxs-lookup"><span data-stu-id="5cfca-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="5cfca-116">Çağırarak ek parametreler ekleyebilirsiniz [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) sürekli olarak.</span><span class="sxs-lookup"><span data-stu-id="5cfca-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="5cfca-117">Çağırarak parametre adları ve değerleri sözlüğü ekleyebilirsiniz [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cfca-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="5cfca-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="5cfca-118">AddStatement</span></span>

 <span data-ttu-id="5cfca-119">Kullanarak toplu işleme benzetimi [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yönteminin sonuna aşağıdaki kodu adıyla çalışan işlemlerin bir listesini alır işlem hattının başka bir deyimi ekler `PowerShell`ve ardından Hizmetleri çalıştıran listesini alır.</span><span class="sxs-lookup"><span data-stu-id="5cfca-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="5cfca-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="5cfca-120">AddScript</span></span>

 <span data-ttu-id="5cfca-121">Çağırarak var olan bir betik çalıştırarak [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cfca-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="5cfca-122">Aşağıdaki örnek bir betik ardışık düzene ekler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5cfca-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="5cfca-123">Bu örnek adlı bir komut dosyası zaten var. varsayar `MyScript.ps1` adlı bir klasörde `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="5cfca-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="5cfca-124">Bir sürümü de mevcuttur [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) adlı bir Boole parametresi alan yöntemi `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="5cfca-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="5cfca-125">Bu parametre ayarlanırsa `true`, sonra da betik yerel kapsama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5cfca-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="5cfca-126">Aşağıdaki kod komut dosyası yerel kapsama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5cfca-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="5cfca-127">Bir işlem hattı zaman uyumlu çağırma</span><span class="sxs-lookup"><span data-stu-id="5cfca-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="5cfca-128">Ardışık öğeleri ekledikten sonra onu çağırır.</span><span class="sxs-lookup"><span data-stu-id="5cfca-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="5cfca-129">İşlem hattını eş zamanlı olarak çağırmak için bir aşırı yüklemesini çağırmak [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cfca-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="5cfca-130">Aşağıdaki örnek, zaman uyumlu bir işlem hattını çağırmasını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cfca-130">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="5cfca-131">Bir işlem hattı zaman uyumsuz olarak çağırma</span><span class="sxs-lookup"><span data-stu-id="5cfca-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="5cfca-132">Bir işlem hattı zaman uyumsuz olarak bir aşırı yüklemesini çağırarak çağırmayı [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) oluşturmak için bir [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) nesnesi ve ardından arama [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cfca-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="5cfca-133">Aşağıdaki örnek, bir işlem hattı zaman uyumsuz olarak çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cfca-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="5cfca-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5cfca-134">See Also</span></span>

 [<span data-ttu-id="5cfca-135">Bir InitialSessionState oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cfca-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="5cfca-136">Kısıtlı bir çalışma alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cfca-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
