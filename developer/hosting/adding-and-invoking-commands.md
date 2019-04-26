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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083034"
---
# <a name="adding-and-invoking-commands"></a>Komut ekleme ve çağırma

Bir çalışma alanı oluşturduktan sonra Windows PowerShellcommands ve komut dosyaları için bir işlem hattı ekleyin ve ardından işlem hattını zaman uyumlu veya zaman uyumsuz olarak çağırma.

## <a name="creating-a-pipeline"></a>Bir işlem hattı oluşturma

 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) sınıfı işlem hattının komutlar, parametreler ve betikler eklemek için çeşitli yöntemler sağlar. Bir aşırı yüklemesini çağırarak, zaman uyumlu bir işlem hattı çağırabilirsiniz [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi veya bir aşırı yüklemesini çağırarak zaman uyumsuz olarak [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) ardından [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) yöntemi.

### <a name="addcommand"></a>AddCommand

1. Oluşturma bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Yürütmek istediğiniz komut ekleyin.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Komutunu çağırın.

   ```csharp
   ps.Invoke();
   ```

 Eğer [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) yöntemi çağırmadan önce birden fazla [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi, sonucu ilk komut, saniye ve benzeri cmdlet'iyle yönetilir. Bir komut için bir önceki komutun sonucuna ilişkin kanal istemiyorsanız çağırarak ekleme [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yerine.

### <a name="addparameter"></a>AddParameter

 Önceki örnekte, hiçbir parametre olmadan tek bir komutu yürütür. Kullanarak komutu parametreleri ekleyebilirsiniz [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) yöntemi örneğin, aşağıdaki kodu alır, tüm adlandırılmış işlemlerin listesini `PowerShell` çalıştırma Makine.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Çağırarak ek parametreler ekleyebilirsiniz [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) sürekli olarak.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Çağırarak parametre adları ve değerleri sözlüğü ekleyebilirsiniz [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) yöntemi.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Kullanarak toplu işleme benzetimi [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yönteminin sonuna aşağıdaki kodu adıyla çalışan işlemlerin bir listesini alır işlem hattının başka bir deyimi ekler `PowerShell`ve ardından Hizmetleri çalıştıran listesini alır.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Çağırarak var olan bir betik çalıştırarak [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) yöntemi. Aşağıdaki örnek bir betik ardışık düzene ekler ve çalıştırır. Bu örnek adlı bir komut dosyası zaten var. varsayar `MyScript.ps1` adlı bir klasörde `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Bir sürümü de mevcuttur [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) adlı bir Boole parametresi alan yöntemi `useLocalScope`. Bu parametre ayarlanırsa `true`, sonra da betik yerel kapsama çalıştırılır. Aşağıdaki kod komut dosyası yerel kapsama çalıştırılır.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Bir işlem hattı zaman uyumlu çağırma

 Ardışık öğeleri ekledikten sonra onu çağırır. İşlem hattını eş zamanlı olarak çağırmak için bir aşırı yüklemesini çağırmak [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi. Aşağıdaki örnek, zaman uyumlu bir işlem hattını çağırmasını gösterilmektedir.

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

### <a name="invoking-a-pipeline-asynchronously"></a>Bir işlem hattı zaman uyumsuz olarak çağırma

 Bir işlem hattı zaman uyumsuz olarak bir aşırı yüklemesini çağırarak çağırmayı [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) oluşturmak için bir [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) nesnesi ve ardından arama [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) yöntemi.

 Aşağıdaki örnek, bir işlem hattı zaman uyumsuz olarak çağırma gösterilmektedir.

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

## <a name="see-also"></a>Ayrıca bkz:

 [Bir InitialSessionState oluşturma](./creating-an-initialsessionstate.md)

 [Kısıtlı bir çalışma alanı oluşturma](./creating-a-constrained-runspace.md)
