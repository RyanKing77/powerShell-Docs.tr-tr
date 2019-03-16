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
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059686"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="081d0-102">Windows PowerShell Konağı Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="081d0-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="081d0-103">Windows PowerShell uygulamanızı barındırmak için kullandığınız [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="081d0-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span> <span data-ttu-id="081d0-104">Bu sınıf, komutların bir işlem hattı oluşturursunuz ve bu komutları bir çalışma alanında yürüten yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="081d0-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span> <span data-ttu-id="081d0-105">En basit yolu, bir ana bilgisayar uygulaması oluşturmak için varsayılan çalışma alanı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="081d0-105">The simplest way to create a host application is to use the default runspace.</span></span> <span data-ttu-id="081d0-106">Varsayılan çalışma alanı, tüm çekirdek Windows PowerShell komutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="081d0-106">The default runspace contains all of the core Windows PowerShell commands.</span></span> <span data-ttu-id="081d0-107">Uygulamanızı Windows PowerShell komutlarının yalnızca bir alt kullanıma sunmak istiyorsanız, özel bir çalışma alanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="081d0-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="081d0-108">Varsayılan çalışma alanı kullanma</span><span class="sxs-lookup"><span data-stu-id="081d0-108">Using the default runspace</span></span>

<span data-ttu-id="081d0-109">Başlamak için biz varsayılan çalışma alanı kullanın ve yöntemlerini kullanın [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) komutlar, Parametreler, ifadeler ve betikleri ardışık düzenine eklemek için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="081d0-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="081d0-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="081d0-110">AddCommand</span></span>

<span data-ttu-id="081d0-111">Kullandığınız [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) yöntemi [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) komutları ardışık düzenine eklemek için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="081d0-111">You use the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands to the pipeline.</span></span> <span data-ttu-id="081d0-112">Örneğin, makinede çalışan işlemlerin listesini almak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="081d0-112">For example, suppose you want to get the list of running processes on the machine.</span></span> <span data-ttu-id="081d0-113">Bu komutu çalıştırmak için yol aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="081d0-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="081d0-114">Oluşturma bir [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) nesne.</span><span class="sxs-lookup"><span data-stu-id="081d0-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="081d0-115">Yürütmek istediğiniz komut ekleyin.</span><span class="sxs-lookup"><span data-stu-id="081d0-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="081d0-116">Komutunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="081d0-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="081d0-117">Eğer [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) yöntemi çağırmadan önce birden fazla [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi, sonucu ilk komut, saniye ve benzeri cmdlet'iyle yönetilir.</span><span class="sxs-lookup"><span data-stu-id="081d0-117">If you call the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="081d0-118">Bir komut için bir önceki komutun sonucuna ilişkin kanal istemiyorsanız çağırarak ekleme [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yerine.</span><span class="sxs-lookup"><span data-stu-id="081d0-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="081d0-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="081d0-119">AddParameter</span></span>

<span data-ttu-id="081d0-120">Önceki örnekte, hiçbir parametre olmadan tek bir komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="081d0-120">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="081d0-121">Kullanarak komutu parametreleri ekleyebilirsiniz [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) yöntemi örneğin, aşağıdaki kodu alır, tüm adlandırılmış işlemlerin listesini `PowerShell` çalıştırma Makine.</span><span class="sxs-lookup"><span data-stu-id="081d0-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="081d0-122">Çağırarak ek parametreler ekleyebilirsiniz [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) sürekli olarak.</span><span class="sxs-lookup"><span data-stu-id="081d0-122">You can add additional parameters by calling [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="081d0-123">Çağırarak parametre adları ve değerleri sözlüğü ekleyebilirsiniz [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="081d0-123">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="081d0-124">AddStatement</span><span class="sxs-lookup"><span data-stu-id="081d0-124">AddStatement</span></span>

<span data-ttu-id="081d0-125">Kullanarak toplu işleme benzetimi [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yönteminin sonuna aşağıdaki kodu adıyla çalışan işlemlerin bir listesini alır işlem hattının başka bir deyimi ekler `PowerShell`ve ardından Hizmetleri çalıştıran listesini alır.</span><span class="sxs-lookup"><span data-stu-id="081d0-125">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="081d0-126">AddScript</span><span class="sxs-lookup"><span data-stu-id="081d0-126">AddScript</span></span>

<span data-ttu-id="081d0-127">Çağırarak var olan bir betik çalıştırarak [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="081d0-127">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="081d0-128">Aşağıdaki örnek bir betik ardışık düzene ekler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="081d0-128">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="081d0-129">Bu örnek adlı bir komut dosyası zaten var. varsayar `MyScript.ps1` adlı bir klasörde `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="081d0-129">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="081d0-130">Bir sürümü de mevcuttur [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) adlı bir Boole parametresi alan yöntemi `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="081d0-130">There is also a version of the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="081d0-131">Bu parametre ayarlanırsa `true`, sonra da betik yerel kapsama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="081d0-131">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="081d0-132">Aşağıdaki kod komut dosyası yerel kapsama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="081d0-132">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="081d0-133">Özel bir çalışma alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="081d0-133">Creating a custom runspace</span></span>

<span data-ttu-id="081d0-134">Önceki örneklerde kullanılan varsayılan çalışma alanı, tüm çekirdek Windows PowerShell komutları yüklenirken, yalnızca belirtilen alt tüm komutların yükleyen özel bir çalışma alanı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="081d0-134">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span> <span data-ttu-id="081d0-135">Performansı artırmak için bunu isteyebilirsiniz (çok sayıda komutları yüklenirken değer bir performans düşüşüne) ya da işlemleri gerçekleştirmek için kullanıcı yeteneğini kısıtlamak için.</span><span class="sxs-lookup"><span data-stu-id="081d0-135">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span> <span data-ttu-id="081d0-136">Komutları yalnızca sınırlı sayıda sunan bir çalışma alanı, kısıtlı bir çalışma alanı adı verilir.</span><span class="sxs-lookup"><span data-stu-id="081d0-136">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span> <span data-ttu-id="081d0-137">Kısıtlı bir çalışma alanı oluşturmak için kullandığınız [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) ve [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="081d0-137">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="081d0-138">InitialSessionState nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="081d0-138">Creating an InitialSessionState object</span></span>

<span data-ttu-id="081d0-139">Özel bir çalışma alanı oluşturmak için önce oluşturmanız gerekir bir [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="081d0-139">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span> <span data-ttu-id="081d0-140">Aşağıdaki örnekte [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) varsayılan oluşturduktan sonra bir çalışma alanı oluşturmak için [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="081d0-140">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="081d0-141">Çalışma alanı sınırlama</span><span class="sxs-lookup"><span data-stu-id="081d0-141">Constraining the runspace</span></span>

<span data-ttu-id="081d0-142">Önceki örnekte, oluşturduğumuz bir varsayılan [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) tüm yerleşik Windows PowerShell çekirdek yükleyen bir nesne.</span><span class="sxs-lookup"><span data-stu-id="081d0-142">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span> <span data-ttu-id="081d0-143">Biz de aradınız [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) yöntemi yalnızca Microsoft.PowerShell.Core komutlar yüklenir InitialSessionState nesneyi oluşturmak için ek bileşeni.</span><span class="sxs-lookup"><span data-stu-id="081d0-143">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span> <span data-ttu-id="081d0-144">Daha kısıtlı bir çalışma alanı oluşturmak için boş bir oluşturma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) çağırarak [ System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) yöntemi ve komutları için InitialSessionState ekleyin.</span><span class="sxs-lookup"><span data-stu-id="081d0-144">To create a more constrained runspace, you must create an empty [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="081d0-145">Belirttiğiniz komutları yükleyen bir çalışma alanı kullanarak önemli ölçüde iyileştirilmiş performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="081d0-145">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="081d0-146">Yöntemlerinin kullandığınız [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) ilk oturum durumu için cmdlet'leri tanımlamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="081d0-146">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span> <span data-ttu-id="081d0-147">Aşağıdaki örnek, bir boş ilk oturum durumunu oluşturur sonra tanımlar ve ekler `Get-Command` ve `Import-Module` ilk oturum durumu için komutları.</span><span class="sxs-lookup"><span data-stu-id="081d0-147">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span> <span data-ttu-id="081d0-148">Biz sonra ilk oturum durumu tarafından kısıtlı bir çalışma alanı oluşturun ve bu çalışma alanında şu komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="081d0-148">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="081d0-149">İlk oturum durumu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="081d0-149">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="081d0-150">Komutları için ilk oturum durumu ekleyin ve tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="081d0-150">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="081d0-151">Oluşturma ve çalışma açın.</span><span class="sxs-lookup"><span data-stu-id="081d0-151">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="081d0-152">Bir komut yürütün ve sonucunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="081d0-152">Execute a command and show the result.</span></span>

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

<span data-ttu-id="081d0-153">Çalıştırdığınızda, bu kodun çıktısı aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="081d0-153">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
