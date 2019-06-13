---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: .NET ve COM nesneleri yeni nesne oluşturma
ms.openlocfilehash: 8bb0326d350be634a50897bdcd432e13ec93450c
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030258"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="f0bbd-103">.NET ve COM nesneleri (New-Object) oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="f0bbd-104">Birçok sistem yönetim görevlerini gerçekleştirmenize olanak tanıyan .NET Framework ve COM arabirimleri ile yazılım bileşenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="f0bbd-105">Windows PowerShell cmdlet'lerini kullanarak gerçekleştirilen görevler için sınırlı olmadıklarından bu bileşenlerin kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="f0bbd-106">İlk sürümde Windows PowerShell cmdlet'lerinin birçoğunu uzak bilgisayarlarda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="f0bbd-107">Biz bu sınırlamayı olay günlükleri, .NET Framework kullanarak yönetirken almak nasıl sürdürebileceğiniz gösterilecek **System.Diagnostics.EventLog** Windows powershell'den doğrudan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="f0bbd-108">Yeni nesne için olay günlüğüne erişimi kullanma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="f0bbd-109">.NET Framework sınıf kitaplığı adlı bir sınıf içeren **System.Diagnostics.EventLog** olay günlüklerini yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="f0bbd-110">Kullanarak bir .NET Framework sınıfının yeni bir örneğini oluşturabilirsiniz **New-Object** cmdlet'iyle **TypeName** parametresi.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="f0bbd-111">Örneğin, aşağıdaki komut, bir olay günlüğü başvuru oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="f0bbd-112">Komutu EventLog sınıfının bir örneği oluşturdu ancak örneği hiçbir veri içermez.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="f0bbd-113">Belirli bir olay günlüğü belirtmedi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="f0bbd-114">Gerçek bir olay günlüğü nasıl alır?</span><span class="sxs-lookup"><span data-stu-id="f0bbd-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="f0bbd-115">Nesne ile yeni oluşturucular kullanma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="f0bbd-116">Belirli bir olay günlüğüne başvurmak için günlüğün adını belirtmenize gerek.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="f0bbd-117">**Yeni nesne** sahip bir **ArgumentList** parametresi.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="f0bbd-118">Bu parametre için değer olarak geçirdiğiniz bağımsız değişkenleri, bir nesnenin özel başlangıç yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="f0bbd-119">Çağrılan yöntemi bir *Oluşturucusu* nesneyi oluşturmak için kullanıldığından.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="f0bbd-120">Örneğin, uygulama günlüğüne bir başvuru almak için 'Uygulama' dize bağımsız değişken olarak belirtin:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="f0bbd-121">.NET Framework temel sınıf çoğunu System ad alanında bulunan olduğundan, Windows PowerShell otomatik olarak belirttiğiniz tür adı için bir eşleşme bulamazsa System ad alanında, belirttiğiniz sınıfları bulmayı dener.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="f0bbd-122">Bu, Diagnostics.EventLog System.Diagnostics.EventLog yerine belirtebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="f0bbd-123">Değişkenleri nesneler depolanıyor</span><span class="sxs-lookup"><span data-stu-id="f0bbd-123">Storing Objects in Variables</span></span>

<span data-ttu-id="f0bbd-124">Geçerli shell'de kullanabilmesi için bir nesneye bir başvuru depolamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="f0bbd-125">Windows PowerShell birçok iş işlem hatları ile yapmanıza gerek değişkenleri lessening sağlar. ancak, bazen nesnelere başvuru değişkenleri depolamak bu nesneleri işlemek daha kullanışlı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="f0bbd-126">Windows PowerShell, aslında nesneler adlandırılmış değişkenler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="f0bbd-127">Herhangi bir geçerli Windows PowerShell komutu çıkışı bir değişkene depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="f0bbd-128">Değişken adları, her zaman $ ile başlar.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-128">Variable names always begin with $.</span></span> <span data-ttu-id="f0bbd-129">Uygulama günlük başvurusu $AppLog adlı bir değişkende depolamak istiyorsanız adını yazın değişkeni bir eşittir işareti tarafından izlenen ve uygulama günlüğü nesnesi oluşturmak için kullanılan komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="f0bbd-130">Ardından $AppLog yazarsanız, uygulama günlüğüne içerdiğini görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="f0bbd-131">Yeni nesne ile bir uzak olay günlüğü erişme</span><span class="sxs-lookup"><span data-stu-id="f0bbd-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="f0bbd-132">Önceki bölümde kullanılan komutlar yerel bilgisayarı hedef; **Get-EventLog** cmdlet'i, yapabilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="f0bbd-133">Uzak bir bilgisayarda uygulama günlüğüne erişmek için hem günlük adını ve bir bilgisayar adı (veya IP adresi) bağımsız sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="f0bbd-134">Biz $RemoteAppLog değişkeninde depolanan bir olay günlüğüne bir başvurusu sahip olduğunuza göre hangi görevleri üzerinde gerçekleştirebiliriz?</span><span class="sxs-lookup"><span data-stu-id="f0bbd-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="f0bbd-135">Nesnesi yöntemleri ile bir olay günlüğü temizleme</span><span class="sxs-lookup"><span data-stu-id="f0bbd-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="f0bbd-136">Nesneler genellikle görevleri gerçekleştirmek için çağrılan yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="f0bbd-137">Kullanabileceğiniz **Get-Member** bir nesneyle ilişkili yöntemler görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="f0bbd-138">Aşağıdaki komut ve seçili çıkış bazı EventLog sınıfının yöntemlerini göster:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="f0bbd-139">**Clear()** yöntemi, olay günlüğünü temizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="f0bbd-140">Yöntem bağımsız değişkenleri gerektirmiyor olsa bile bir yöntemi çağırırken, her zaman yöntem adı parantez ile izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="f0bbd-141">Bu Windows PowerShell yöntemi ve olası bir özelliği aynı ada sahip arasında ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="f0bbd-142">Çağırmak için aşağıdaki komutu yazın **Temizle** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="f0bbd-143">Günlüğü görüntülemek için aşağıdakini yazın.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-143">Type the following to display the log.</span></span> <span data-ttu-id="f0bbd-144">Olay günlüğü temizlendi ve artık 262 yerine 0 girdi olduğunu görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="f0bbd-145">Nesnesi yeni ile COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="f0bbd-146">Kullanabileceğiniz **New-Object** Bileşen Nesne Modeli (COM) bileşenleri ile çalışmak için.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="f0bbd-147">Çoğu sistemde yüklü ActiveX uygulamalar Internet Explorer gibi Windows betik sistemi (WSH) dahil çeşitli kitaplıklara bileşenleri çeşitler barındırır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="f0bbd-148">**Yeni nesne** COM nesneleri çağırırken .NET Framework yapan onunla aynı sınırlamalara sahiptir, COM nesneleri oluşturmak için .NET Framework çalışma zamanı aranabilir sarmalayıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="f0bbd-149">Bir COM nesnesi oluşturmak için belirtmeniz gerekir **ComObject** programlı tanımlayıcı parametresi veya *ProgID* kullanmak istediğiniz COM sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="f0bbd-150">COM kullanımı ve ProgIDs bir sistemde kullanılabilir nelerdir belirleyen sınırlamaları hakkında kapsamlı bir açıklama, bu kullanıcının kılavuzun kapsamı dışındadır olmakla birlikte en iyi bilinen nesneleri ortamlarından WSH gibi Windows PowerShell içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="f0bbd-151">Bu progid'ler belirterek WSH nesneleri oluşturabilirsiniz: **WScript.Shell nesnesinin**, **WScript.Network**, **Scripting.Dictionary**, ve **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="f0bbd-152">Aşağıdaki komutlar bu nesneleri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="f0bbd-153">Bu sınıfların işlevselliğinin büyük kısmını yapılan olsa da başka şekillerde kullanılabilir Windows PowerShell'de, kısayol oluşturma gibi birkaç görev WSH sınıflarını kullanarak yapmak yine de kolaydır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="f0bbd-154">Bir masaüstü kısayolu wscript.Shell nesnesinin ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="f0bbd-155">Bir COM nesnesi ile kolayca gerçekleştirilebilir bir görev bir kısayol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="f0bbd-156">Bir kısayol masaüstünüzde giriş klasörü için bağlantılar için Windows PowerShell oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="f0bbd-157">Önce bir başvuru oluşturmak gereken **wscript.Shell nesnesinin**, hangi adlı bir değişkende depolarız **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="f0bbd-158">Get-Member COM nesneleriyle birlikte çalışarak yazarak bir nesnenin üyelerine keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="f0bbd-159">**Get-Member** isteğe sahip **Inputobject** yöneltme yerine Giriş sağlamak için kullanabileceğiniz bir parametre **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="f0bbd-160">Aynı komutu yerine kullanılan, yukarıda gösterildiği gibi çıkış elde edebileceğiniz **Get-Member - Inputobject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="f0bbd-161">Kullanırsanız **Inputobject**, tek bir öğe kendi bağımsız değişkeni değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="f0bbd-162">Çeşitli nesneleri değişkene varsa buna **Get-Member** bunları bir dizi nesne olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="f0bbd-163">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="f0bbd-164">**Wscript.Shell nesnesinin CreateShortcut** yöntemi tek bir değişken oluşturmak için kısayol dosyasının yolu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="f0bbd-165">Masaüstünde tam yolunu yazabilirsiniz, ancak daha kolay bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="f0bbd-166">Masaüstü genellikle geçerli kullanıcının giriş klasörü içinde Masaüstü adlı bir klasör temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="f0bbd-167">Windows PowerShell bir değişkene sahip **$Home** , bu klasörün yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="f0bbd-168">Biz bu değişkeni kullanarak giriş klasörünün yolunu belirtin ve Masaüstü klasörün adını ve kısayol tuşlarına basarak oluşturmak adını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="f0bbd-169">Çift tırnak içinde bir değişken adı şuna benzer bir şey kullandığınızda, Windows PowerShell, eşleşen bir değer yerine dener.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="f0bbd-170">Tek tırnak işareti kullanırsanız, değişken değeri yerine Windows PowerShell denemez.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="f0bbd-171">Örneğin, aşağıdaki komutları yazarak deneyin:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="f0bbd-172">Adlı bir değişken artık sahibiz **$lnk** , yeni bir kısayol başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="f0bbd-173">Üyelerini görmek istiyorsanız, kendisine iletebildiğiniz **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="f0bbd-174">Çıktıyı aşağıya bizim kısayol oluşturma işlemini kullanmak ihtiyacımız olan üyeleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="f0bbd-175">Belirtmek ihtiyacımız **TargetPath**, Windows PowerShell ve ardından kısayol kaydetme uygulama klasörü **$lnk** çağırarak **Kaydet** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="f0bbd-176">Windows PowerShell uygulama klasörü yolu değişkeninde depolanan **$PSHome**, yazarak bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="f0bbd-177">Windows powershell'den Internet Explorer'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="f0bbd-178">Birçok uygulama (Microsoft Office uygulamaları ve Internet Explorer ailesinin dahil) COM kullanılarak otomatikleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="f0bbd-179">Internet Explorer, bazı tipik teknikleri ve içinde COM tabanlı uygulamalar ile çalışma konuları gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="f0bbd-180">Internet Explorer ProgID, belirterek bir Internet Explorer örneği oluşturma **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="f0bbd-181">Bu komut, Internet Explorer'ı başlatır, ancak görünür yapmaz.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="f0bbd-182">Get-Process yazarsanız Iexplore adlı bir işlemin çalıştığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="f0bbd-183">Windows PowerShell betiğinden çıkın, aslında, işlem çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="f0bbd-184">Bilgisayarı yeniden başlatmanız gerekir ya da Iexplore işlemi sonlandırmak için bir aracı gibi Görev Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="f0bbd-185">Ayrı işlem başlatmak COM nesneleri yaygın olarak adlandırılan *ActiveX yürütülebilir dosyaları*, olabilir veya başlatma sırasında bir kullanıcı arabirimi pencere görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="f0bbd-186">Bir pencere oluşturma ancak Internet Explorer gibi görünür yapmayın odağı genellikle Windows masaüstüne taşınır ve pencerenin etkileşim görünür yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="f0bbd-187">Yazarak **$IE | Get-Member**, Internet Explorer için özellikleri ve yöntemleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="f0bbd-188">Internet Explorer penceresi görmek için yazarak Visible özelliğini $true olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="f0bbd-189">Ardından, Navigate yöntemi kullanarak belirli bir Web adresi gidebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="f0bbd-190">Diğer üyeleri Internet Explorer nesne modeli kullanarak Web sayfasında metin içeriğini almak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="f0bbd-191">Aşağıdaki komut, geçerli Web sayfasının gövdesinde HTML metni görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="f0bbd-192">PowerShell içinden Internet Explorer'ı kapatmak için kendi Quit() yöntemi çağırın:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="f0bbd-193">Bu, kapatmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-193">This will force it to close.</span></span> <span data-ttu-id="f0bbd-194">Olsa da hala bir COM nesnesi gibi görünüyor $IE değişken artık geçerli bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="f0bbd-195">Bunu kullanmayı denerseniz, bir Otomasyon hata alırsınız:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="f0bbd-196">Kalan başvuru $ gibi bir komutla IE kaldırabilir ya da $null = ya da tamamen değişken yazarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="f0bbd-197">ActiveX yürütülebilir dosyaları çıkmayın veya bir başvuru kaldırdığınızda çalışmaya devam hiçbir ortak standart yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="f0bbd-198">Uygulamanın görünür olup düzenlenmiş bir belge içinde kullanılıp kullanılmadığını ve hatta olup Windows PowerShell hala çalışıyor gibi durumlarda, bağlı olarak uygulama olabilir veya olmayan sonlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="f0bbd-199">Bu nedenle, her ActiveX Windows PowerShell'de kullanmak istediğiniz yürütülebilir için sonlandırma davranışı test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="f0bbd-200">.NET Framework sarılı bir COM nesneleri hakkında uyarılar alma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="f0bbd-201">Bazı durumlarda, bir COM nesnesi ilişkili bir .NET Framework olabilir *çalışma zamanı çağrılabilir sarmalayıcı* veya RCW ve bu işlem tarafından kullanılan **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="f0bbd-202">RCW davranışı, davranış normal COM nesnesinin farklı olabileceğinden **New-Object** sahip bir **katı** parametresi RCW erişimi hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="f0bbd-203">Belirtirseniz **katı** parametresi ve ardından bir RCW kullanan bir COM nesnesi oluşturur, bir uyarı iletisi alın:</span><span class="sxs-lookup"><span data-stu-id="f0bbd-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="f0bbd-204">Nesne hala oluşturulur, ancak standart bir COM nesnesi olmadığını uyarılırsınız.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>
