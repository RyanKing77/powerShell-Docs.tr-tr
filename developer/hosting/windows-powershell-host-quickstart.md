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
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530612"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="31e1b-102">Windows PowerShell Konağı Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="31e1b-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="31e1b-103">Windows PowerShell uygulamanızı barındırmak için kullandığınız [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31e1b-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="31e1b-104">Bu sınıf, komutların bir işlem hattı oluşturursunuz ve bu komutları bir çalışma alanında yürüten yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="31e1b-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="31e1b-105">En basit yolu, bir ana bilgisayar uygulaması oluşturmak için varsayılan çalışma alanı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="31e1b-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="31e1b-106">Varsayılan çalışma alanı, tüm çekirdek Windows PowerShell komutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="31e1b-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="31e1b-107">Uygulamanızı Windows PowerShell komutlarının yalnızca bir alt kullanıma sunmak istiyorsanız, özel bir çalışma alanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31e1b-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="31e1b-108">Varsayılan çalışma alanı kullanma</span><span class="sxs-lookup"><span data-stu-id="31e1b-108">Using the default runspace</span></span>

<span data-ttu-id="31e1b-109">Başlamak için biz varsayılan çalışma alanı kullanın ve yöntemlerini kullanın [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) komutlar, Parametreler, ifadeler ve betikleri ardışık düzenine eklemek için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31e1b-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="31e1b-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="31e1b-110">AddCommand</span></span>

<span data-ttu-id="31e1b-111">Kullandığınız [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) komutları ardışık düzenine eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31e1b-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="31e1b-112">Örneğin, makinede çalışan işlemlerin listesini almak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="31e1b-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="31e1b-113">Bu komutu çalıştırmak için yol aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="31e1b-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="31e1b-114">Oluşturma bir [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) nesne.</span><span class="sxs-lookup"><span data-stu-id="31e1b-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="31e1b-115">Yürütmek istediğiniz komut ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31e1b-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="31e1b-116">Komutunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="31e1b-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="31e1b-117">Çağırmadan önce AddCommand yöntemi birden çok kez çağrı yaparsanız [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) yöntemi, ilk komutun sonucuna ilişkin ikinci ve benzeri yöneltilen.</span><span class="sxs-lookup"><span data-stu-id="31e1b-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="31e1b-118">Bir komut için bir önceki komutun sonucuna ilişkin kanal istemiyorsanız çağırarak ekleme [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yerine.</span><span class="sxs-lookup"><span data-stu-id="31e1b-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="31e1b-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="31e1b-119">AddParameter</span></span>

<span data-ttu-id="31e1b-120">Önceki örnekte, hiçbir parametre olmadan tek bir komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="31e1b-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="31e1b-121">Kullanarak komutu parametreleri ekleyebilirsiniz [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31e1b-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="31e1b-122">Örneğin, aşağıdaki kod tüm adlandırılmış işlemlerin bir listesini alır `PowerShell` makine üzerinde çalışan.</span><span class="sxs-lookup"><span data-stu-id="31e1b-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="31e1b-123">Art arda AddParameter yöntemi çağırarak ek parametreler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31e1b-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="31e1b-124">Çağırarak parametre adları ve değerleri sözlüğü ekleyebilirsiniz [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31e1b-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="31e1b-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="31e1b-125">AddStatement</span></span>

<span data-ttu-id="31e1b-126">Kullanarak toplu işleme benzetimi [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) yöntemi ek bir ifade, işlem hattı sonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="31e1b-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="31e1b-127">Aşağıdaki kod adı ile çalışan işlemlerin bir listesi alır `PowerShell`ve ardından Hizmetleri çalıştıran listesini alır.</span><span class="sxs-lookup"><span data-stu-id="31e1b-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="31e1b-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="31e1b-128">AddScript</span></span>

<span data-ttu-id="31e1b-129">Çağırarak var olan bir betik çalıştırarak [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31e1b-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="31e1b-130">Aşağıdaki örnek bir betik ardışık düzene ekler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="31e1b-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="31e1b-131">Bu örnek adlı bir komut dosyası zaten var. varsayar `MyScript.ps1` adlı bir klasörde `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="31e1b-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="31e1b-132">Adlı bir boolean parametresini alan AddScript yöntemi bir sürümü de mevcuttur `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="31e1b-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="31e1b-133">Bu parametre ayarlanırsa `true`, sonra da betik yerel kapsama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="31e1b-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="31e1b-134">Aşağıdaki kod komut dosyası yerel kapsama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="31e1b-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="31e1b-135">Özel bir çalışma alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="31e1b-135">Creating a custom runspace</span></span>

<span data-ttu-id="31e1b-136">Önceki örneklerde kullanılan varsayılan çalışma alanı, tüm çekirdek Windows PowerShell komutları yüklenirken, yalnızca belirtilen alt tüm komutların yükleyen özel bir çalışma alanı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31e1b-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="31e1b-137">Performansı artırmak için bunu isteyebilirsiniz (çok sayıda komutları yüklenirken değer bir performans düşüşüne) ya da işlemleri gerçekleştirmek için kullanıcı yeteneğini kısıtlamak için.</span><span class="sxs-lookup"><span data-stu-id="31e1b-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="31e1b-138">Komutları yalnızca sınırlı sayıda sunan bir çalışma alanı, kısıtlı bir çalışma alanı adı verilir.</span><span class="sxs-lookup"><span data-stu-id="31e1b-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="31e1b-139">Kısıtlı bir çalışma alanı oluşturmak için kullandığınız [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) ve [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="31e1b-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="31e1b-140">InitialSessionState nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="31e1b-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="31e1b-141">Özel bir çalışma alanı oluşturmak için önce oluşturmanız gerekir bir [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="31e1b-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="31e1b-142">Aşağıdaki örnekte [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) varsayılan InitialSessionState nesnesini oluşturduktan sonra bir çalışma alanı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="31e1b-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="31e1b-143">Çalışma alanı sınırlama</span><span class="sxs-lookup"><span data-stu-id="31e1b-143">Constraining the runspace</span></span>

<span data-ttu-id="31e1b-144">Önceki örnekte, oluşturduğumuz bir varsayılan [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) tüm yerleşik Windows PowerShell çekirdek yükleyen bir nesne.</span><span class="sxs-lookup"><span data-stu-id="31e1b-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="31e1b-145">Biz de aradınız [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) yöntemi yalnızca Microsoft.PowerShell.Core komutlar yüklenir InitialSessionState nesneyi oluşturmak için ek bileşeni.</span><span class="sxs-lookup"><span data-stu-id="31e1b-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="31e1b-146">Daha kısıtlı bir çalışma alanı oluşturmak için boş bir InitialSessionState nesne çağırarak oluşturmalısınız [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) yöntemi ve ardından komutlarını ekleyin InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="31e1b-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="31e1b-147">Belirttiğiniz komutları yükleyen bir çalışma alanı kullanarak önemli ölçüde iyileştirilmiş performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="31e1b-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="31e1b-148">Yöntemlerinin kullandığınız [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) ilk oturum durumu için cmdlet'leri tanımlamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="31e1b-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="31e1b-149">Aşağıdaki örnek, bir boş ilk oturum durumunu oluşturur sonra tanımlar ve ekler `Get-Command` ve `Import-Module` ilk oturum durumu için komutları.</span><span class="sxs-lookup"><span data-stu-id="31e1b-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="31e1b-150">Biz sonra ilk oturum durumu tarafından kısıtlı bir çalışma alanı oluşturun ve bu çalışma alanında şu komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="31e1b-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="31e1b-151">İlk oturum durumu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="31e1b-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="31e1b-152">Komutları için ilk oturum durumu ekleyin ve tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="31e1b-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="31e1b-153">Oluşturma ve çalışma açın.</span><span class="sxs-lookup"><span data-stu-id="31e1b-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="31e1b-154">Bir komut yürütün ve sonucunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="31e1b-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="31e1b-155">Çalıştırdığınızda, bu kodun çıktısı aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="31e1b-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
