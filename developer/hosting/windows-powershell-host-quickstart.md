---
title: Windows PowerShell konağı hızlı başlangıç | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 2c6a4bca03ee7f62371cbc296f854464167e5a62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847792"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell Konağı Hızlı Başlangıç

Windows PowerShell uygulamanızı barındırmak için kullandığınız [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) sınıfı. Bu sınıf, komutların bir işlem hattı oluşturursunuz ve bu komutları bir çalışma alanında yürüten yöntemleri sağlar. En basit yolu, bir ana bilgisayar uygulaması oluşturmak için varsayılan çalışma alanı kullanmaktır. Varsayılan çalışma alanı, tüm çekirdek Windows PowerShell komutlarını içerir. Uygulamanızı Windows PowerShell komutlarının yalnızca bir alt kullanıma sunmak istiyorsanız, özel bir çalışma alanı oluşturmanız gerekir.

## <a name="using-the-default-runspace"></a>Varsayılan çalışma alanı kullanma

Başlamak için biz varsayılan çalışma alanı kullanın ve yöntemlerini kullanın [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) komutlar, Parametreler, ifadeler ve betikleri ardışık düzenine eklemek için sınıfı.

### <a name="addcommand"></a>AddCommand

Kullandığınız [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) yöntemi [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) komutları ardışık düzenine eklemek için sınıfı. Örneğin, makinede çalışan işlemlerin listesini almak istediğinizi varsayalım. Bu komutu çalıştırmak için yol aşağıdaki gibidir.

1. Oluşturma bir [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) nesne.

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

Eğer [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) yöntemi çağırmadan önce birden fazla [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi, sonucu ilk komut, saniye ve benzeri cmdlet'iyle yönetilir. Bir komut için bir önceki komutun sonucuna ilişkin kanal istemiyorsanız çağırarak ekleme [System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yerine.

### <a name="addparameter"></a>AddParameter

Önceki örnekte, hiçbir parametre olmadan tek bir komutu yürütür. Kullanarak komutu parametreleri ekleyebilirsiniz [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) yöntemi örneğin, aşağıdaki kodu alır, tüm adlandırılmış işlemlerin listesini `PowerShell` çalıştırma Makine.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Çağırarak ek parametreler ekleyebilirsiniz [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) sürekli olarak.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

Çağırarak parametre adları ve değerleri sözlüğü ekleyebilirsiniz [System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) yöntemi.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Kullanarak toplu işleme benzetimi [System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yönteminin sonuna aşağıdaki kodu adıyla çalışan işlemlerin bir listesini alır işlem hattının başka bir deyimi ekler `PowerShell`ve ardından Hizmetleri çalıştıran listesini alır.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Çağırarak var olan bir betik çalıştırarak [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) yöntemi. Aşağıdaki örnek bir betik ardışık düzene ekler ve çalıştırır. Bu örnek adlı bir komut dosyası zaten var. varsayar `MyScript.ps1` adlı bir klasörde `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Bir sürümü de mevcuttur [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) adlı bir Boole parametresi alan yöntemi `useLocalScope`. Bu parametre ayarlanırsa `true`, sonra da betik yerel kapsama çalıştırılır. Aşağıdaki kod komut dosyası yerel kapsama çalıştırılır.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Özel bir çalışma alanı oluşturma

Önceki örneklerde kullanılan varsayılan çalışma alanı, tüm çekirdek Windows PowerShell komutları yüklenirken, yalnızca belirtilen alt tüm komutların yükleyen özel bir çalışma alanı oluşturabilirsiniz. Performansı artırmak için bunu isteyebilirsiniz (çok sayıda komutları yüklenirken değer bir performans düşüşüne) ya da işlemleri gerçekleştirmek için kullanıcı yeteneğini kısıtlamak için. Komutları yalnızca sınırlı sayıda sunan bir çalışma alanı, kısıtlı bir çalışma alanı adı verilir. Kısıtlı bir çalışma alanı oluşturmak için kullandığınız [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) ve [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) sınıfları.

### <a name="creating-an-initialsessionstate-object"></a>InitialSessionState nesne oluşturma

Özel bir çalışma alanı oluşturmak için önce oluşturmanız gerekir bir [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne. Aşağıdaki örnekte [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) varsayılan oluşturduktan sonra bir ruspace oluşturmak için [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Çalışma alanı sınırlama

Önceki örnekte, oluşturduğumuz bir varsayılan [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) tüm yerleşik Windows PowerShell çekirdek yükleyen bir nesne. Biz de aradınız [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) yöntemi yalnızca Mirosoft.PowerShell.Core komutlar yüklenir InitialSessionState nesneyi oluşturmak için ek bileşeni. Daha kısıtlı bir çalışma alanı oluşturmak için boş bir oluşturma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) çağırarak [ System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) yöntemi ve komutları için InitialSessionState ekleyin.

Belirttiğiniz komutları yükleyen bir çalışma alanı kullanarak önemli ölçüde iyileştirilmiş performans sağlar.

Yöntemlerinin kullandığınız [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) ilk oturum durumu için cmdlet'leri tanımlamak için sınıf. Aşağıdaki örnek, bir boş ilk oturum durumunu oluşturur sonra tanımlar ve ekler `Get-Command` ve `Import-Module` ilk oturum durumu için komutları. Biz sonra ilk oturum durumu tarafından kısıtlı bir çalışma alanı oluşturun ve bu çalışma alanında şu komutları çalıştırın.

İlk oturum durumu oluşturun.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Komutları için ilk oturum durumu ekleyin ve tanımlayın.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Oluşturma ve çalışma açın.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Bir komut yürütün ve sonucunu göstermektedir.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Çalıştırdığınızda, bu kodun çıktısı aşağıdaki gibi görünür.

```powershell
Get-Command
Import-Module
```
