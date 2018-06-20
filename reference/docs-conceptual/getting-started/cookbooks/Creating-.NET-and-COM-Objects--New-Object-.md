---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: .NET ve COM nesnelerini yeni nesne oluşturma
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953397"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="5215c-103">.NET ve COM nesnelerini (nesne yeni) oluşturma</span><span class="sxs-lookup"><span data-stu-id="5215c-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="5215c-104">Yazılım bileşenleri birçok sistem yönetim görevlerini gerçekleştirmenize olanak sağlayan .NET Framework ve COM arabirimleri ile vardır.</span><span class="sxs-lookup"><span data-stu-id="5215c-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="5215c-105">Windows PowerShell cmdlet'lerini kullanarak gerçekleştirdiği görevleri sınırlı olduklarından bu bileşenlerin kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5215c-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="5215c-106">Birçok ilk sürümünde Windows PowerShell cmdlet'lerini uzak bilgisayarlarda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="5215c-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="5215c-107">Olay günlükleri .NET Framework kullanarak yönetirken bu sınırlamaya geçici almak göstereceğiz **System.Diagnostics.EventLog** Windows powershell'den doğrudan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5215c-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

### <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="5215c-108">Yeni nesne olay günlüğüne erişimi için kullanma</span><span class="sxs-lookup"><span data-stu-id="5215c-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="5215c-109">.NET Framework sınıf kitaplığı adlı bir sınıf içerir **System.Diagnostics.EventLog** olay günlüklerini yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="5215c-110">.NET Framework sınıfının yeni bir örneğini kullanarak oluşturabileceğiniz **New-Object** cmdlet'iyle **TypeName** parametresi.</span><span class="sxs-lookup"><span data-stu-id="5215c-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="5215c-111">Örneğin, aşağıdaki komut, bir olay günlüğü başvuru oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5215c-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="5215c-112">Örnek komut EventLog sınıfının bir örneği oluşturdu ancak herhangi bir veri içermez.</span><span class="sxs-lookup"><span data-stu-id="5215c-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="5215c-113">Belirli bir olay günlüğü belirtmedi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5215c-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="5215c-114">Gerçek bir olay günlüğü nasıl alıyorum?</span><span class="sxs-lookup"><span data-stu-id="5215c-114">How do you get a real event log?</span></span>

#### <a name="using-constructors-with-new-object"></a><span data-ttu-id="5215c-115">Yeni-nesnesiyle oluşturucular kullanma</span><span class="sxs-lookup"><span data-stu-id="5215c-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="5215c-116">Belirli bir olay günlüğü'ne başvurun için günlük adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5215c-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="5215c-117">**Yeni nesne** sahip bir **bağımsızdeğişkenListesi** parametresi.</span><span class="sxs-lookup"><span data-stu-id="5215c-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="5215c-118">Bu parametre için değerler olarak geçirdiğiniz bağımsız değişkenler nesnesi özel başlangıç yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5215c-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="5215c-119">Çağrılan yöntemi bir *Oluşturucusu* çünkü nesnesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5215c-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="5215c-120">Örneğin, uygulama günlüğüne bir başvuru almak için 'Uygulaması' dize bağımsız değişken olarak belirtin:</span><span class="sxs-lookup"><span data-stu-id="5215c-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="5215c-121">.NET Framework temel sınıfları çoğunu System ad alanında bulunan olduğundan, Windows PowerShell belirttiğiniz typename yönelik bir eşleşme bulamazsanız System ad alanında belirtin sınıfları bulmak otomatik olarak çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="5215c-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="5215c-122">Başka bir deyişle, System.Diagnostics.EventLog yerine Diagnostics.EventLog belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5215c-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

#### <a name="storing-objects-in-variables"></a><span data-ttu-id="5215c-123">Nesne değişkenleri depolanması</span><span class="sxs-lookup"><span data-stu-id="5215c-123">Storing Objects in Variables</span></span>

<span data-ttu-id="5215c-124">Geçerli Kabuğu'nda kullanabilmeniz için bir nesneye başvuru depolamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5215c-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="5215c-125">Windows PowerShell, çok sayıda ardışık çalışmak yapmak değişkenleri gereksinimini lessening olanak tanır ancak bazen nesnelerin referansları değişkenleri depolamak, bu nesneleri işlemek daha kullanışlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="5215c-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="5215c-126">Windows PowerShell, aslında nesneler adlandırılmış değişkenleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5215c-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="5215c-127">Geçerli bir Windows PowerShell komut çıkışı bir değişkene depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="5215c-128">Değişken adları, her zaman $ ile başlar.</span><span class="sxs-lookup"><span data-stu-id="5215c-128">Variable names always begin with $.</span></span> <span data-ttu-id="5215c-129">Uygulama günlüğü başvurusu $AppLog adlı bir değişkende depolamak istiyorsanız adını yazın değişkeni ve ardından bir eşittir işareti ve uygulama günlüğü nesnesi oluşturmak için kullanılan komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="5215c-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="5215c-130">Ardından $AppLog yazarsanız, uygulama günlüğüne içerdiği görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5215c-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="5215c-131">Yeni nesne ile bir uzak olay günlüğü erişme</span><span class="sxs-lookup"><span data-stu-id="5215c-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="5215c-132">Önceki bölümde kullanılan komutlar yerel bilgisayarı hedef; **Get-EventLog** cmdlet, yapabilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="5215c-133">Uzak bir bilgisayarda uygulama günlüğüne erişmek için hem günlük adını ve bir bilgisayar adı (veya IP adresi) bağımsız değişken olarak sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5215c-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="5215c-134">Biz $RemoteAppLog değişkeninde depolanan bir olay günlüğü başvuru sahip olduğunuza göre hangi görevleri biz üzerinde gerçekleştirebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="5215c-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

#### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="5215c-135">Bir olay günlüğü nesne yöntemleri ile temizleme</span><span class="sxs-lookup"><span data-stu-id="5215c-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="5215c-136">Nesneler genelde görevleri gerçekleştirmek için çağrılan yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="5215c-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="5215c-137">Kullanabileceğiniz **Get-üye** bir nesneyle ilişkilendirilmiş yöntemlerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="5215c-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="5215c-138">Seçilen çıkış ve aşağıdaki komutu bazı olay günlüğüne sınıfı yöntemlerinin göster:</span><span class="sxs-lookup"><span data-stu-id="5215c-138">The following command and selected output show some the methods of the EventLog class:</span></span>

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

<span data-ttu-id="5215c-139">**Clear()** yöntemi, olay günlüğü temizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="5215c-140">Yöntemin bağımsız değişkenleri gerektirmiyor olsa bile bir yöntem çağrılırken, her zaman yöntem adı parantez tarafından izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5215c-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="5215c-141">Bu Windows PowerShell yöntemi ve olası bir özellik aynı ada sahip arasında ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="5215c-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="5215c-142">Çağırmak için aşağıdaki komutu yazın **Temizle** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="5215c-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="5215c-143">Günlük görüntülemek için aşağıdakini yazın.</span><span class="sxs-lookup"><span data-stu-id="5215c-143">Type the following to display the log.</span></span> <span data-ttu-id="5215c-144">Olay günlüğü temizlendi ve şimdi 262 yerine 0 girişlerine sahip görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="5215c-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="5215c-145">Yeni nesne oluşturma COM nesneleri</span><span class="sxs-lookup"><span data-stu-id="5215c-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="5215c-146">Kullanabileceğiniz **New-Object** Bileşen Nesne Modeli (COM) bileşenleriyle çalışmak üzere.</span><span class="sxs-lookup"><span data-stu-id="5215c-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="5215c-147">Çoğu sistemde yüklü ActiveX uygulamalara Internet Explorer gibi Windows Komut Dosyası Sistemi'ni (WSH) dahil çeşitli kitaplıkları bileşenleri arasındadır.</span><span class="sxs-lookup"><span data-stu-id="5215c-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="5215c-148">**Yeni nesne** .NET Framework COM nesneleri çağrılırken mu aynı sınırlamalara sahiptir COM nesneleri oluşturmak için .NET Framework çalışma zamanı aranabilir sarmalayıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="5215c-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="5215c-149">Bir COM nesnesi oluşturmak için belirtmeniz gerekir **ComObject** program tanımlayıcısı parametresiyle veya *ProgID* kullanmak istediğiniz COM sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5215c-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="5215c-150">COM kullanın ve ProgID bir sistemde kullanılabilir nelerdir belirleme sınırlamaları tam bir irdelemesi ve bu kullanıcı kılavuzu kapsamında değildir, ancak en iyi bilinen nesneleri ortamlarından WSH gibi Windows PowerShell içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="5215c-151">Bu ProgID belirterek WSH nesneleri oluşturabilirsiniz: **wscript.Shell nesnesinin**, **WScript.Network**, **Scripting.Dictionary**, ve  **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="5215c-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="5215c-152">Aşağıdaki komutlar, bu nesnelerin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5215c-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="5215c-153">Bu sınıfların işlevselliğinin büyük kısmını yapıldığında rağmen başka şekillerde kullanılabilir Windows PowerShell içinde kısayol oluşturma gibi birkaç görevleri WSH sınıflarını kullanarak yapmak hala daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="5215c-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="5215c-154">Bir masaüstü kısayolu wscript.Shell nesnesinin ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="5215c-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="5215c-155">Bir COM nesnesi ile kolayca gerçekleştirilebilir bir görev bir kısayol oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5215c-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="5215c-156">Bir kısayol masaüstünüzde giriş klasörü bağlanan için Windows PowerShell oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="5215c-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="5215c-157">İlk olarak bir başvuru oluşturmanıza gerek **wscript.Shell nesnesinin**, hangi adlı bir değişkende depolayacak mı **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="5215c-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="5215c-158">Nesne üyeleri yazarak gözatabilirsiniz get-üye COM nesneleri ile çalışır:</span><span class="sxs-lookup"><span data-stu-id="5215c-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="5215c-159">**Get-üye** isteğe sahip **Inputobject** yerine yöneltme giriş sağlamak için kullanabileceğiniz parametre **Get-üye**.</span><span class="sxs-lookup"><span data-stu-id="5215c-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="5215c-160">Bunun yerine komutu kullandıysanız yukarıda gösterildiği gibi çıktı aynı elde edebileceğiniz **Get-üye - Inputobject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="5215c-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="5215c-161">Kullanırsanız **Inputobject**, bağımsız değişkeni tek bir öğe işler.</span><span class="sxs-lookup"><span data-stu-id="5215c-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="5215c-162">Bir değişkende birden fazla nesneniz varsa buna **Get-üye** nesnelerinin bir dizisi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="5215c-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="5215c-163">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5215c-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="5215c-164">**Wscript.Shell nesnesinin CreateShortcut** yöntemi tek bir değişken oluşturmak için kısayol dosyasının yolu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5215c-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="5215c-165">Masaüstü tam yolunu yazabilirsiniz, ancak daha kolay bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="5215c-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="5215c-166">Masaüstü normalde Masaüstü geçerli kullanıcının giriş klasörü içinde adlı bir klasör olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="5215c-167">Windows PowerShell sahip bir değişken **$Home** bu klasörün yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5215c-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="5215c-168">Biz bu değişkeni kullanarak giriş klasörü yolunu belirtin ve ardından Masaüstü klasörün adını ve yazarak oluşturmak kısayol için ad ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5215c-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="5215c-169">Bir değişken adı çift tırnak içine benzer bir şey kullandığınızda, Windows PowerShell eşleşen bir değer yerine dener.</span><span class="sxs-lookup"><span data-stu-id="5215c-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="5215c-170">Tek tırnak işareti kullanırsanız, Windows PowerShell değişken değerini değiştirmeyi denemez.</span><span class="sxs-lookup"><span data-stu-id="5215c-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="5215c-171">Örneğin, aşağıdaki komutları yazarak deneyin:</span><span class="sxs-lookup"><span data-stu-id="5215c-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="5215c-172">Şimdi adlı bir değişkene sahip olduğumuz **$lnk** yeni bir kısayol başvurusu içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5215c-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="5215c-173">Üyelerini görmek istiyorsanız, kendisine iletebildiğiniz **Get-üye**.</span><span class="sxs-lookup"><span data-stu-id="5215c-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="5215c-174">Çıktı bizim kısayol oluşturmayı tamamlamak için kullanılacak ihtiyacımız üyeler gösterir:</span><span class="sxs-lookup"><span data-stu-id="5215c-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

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

<span data-ttu-id="5215c-175">Belirtmek ihtiyacımız **TargetPath**, Windows PowerShell ve ardından kısayol kaydetme uygulama klasörü olduğu **$lnk** çağırarak **kaydetmek** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5215c-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="5215c-176">Windows PowerShell uygulama klasör yolu değişkende depolanır **$PSHome**, biz yazarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5215c-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="5215c-177">Windows PowerShell Internet Explorer'dan kullanma</span><span class="sxs-lookup"><span data-stu-id="5215c-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="5215c-178">Birçok uygulama (uygulamalar ve Internet Explorer'ın Microsoft Office ailesi dahil) COM kullanarak otomatikleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="5215c-179">Internet Explorer bazı tipik teknikleri ve COM tabanlı uygulamalarla çalışma ilgili sorunları gösterir.</span><span class="sxs-lookup"><span data-stu-id="5215c-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="5215c-180">Internet Explorer ProgID, belirterek bir Internet Explorer örneği oluşturma **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="5215c-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="5215c-181">Bu komut, Internet Explorer'ı başlatır, ancak görünür yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5215c-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="5215c-182">Get-Process yazarsanız, Iexplore adlı bir işlem çalıştığından görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5215c-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="5215c-183">Aslında, Windows PowerShell çıkarsanız işlemi çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="5215c-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="5215c-184">Bilgisayarı yeniden başlatın veya Iexplore işlemi sonlandırmak için bir aracı gibi Görev Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="5215c-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="5215c-185">Ayrı işlemler Başlat COM nesneleri genellikle adlı *ActiveX yürütülebilir dosyalar*başlatıldığında bir kullanıcı arabirimi penceresi görüntülenmeyebilir veya olabilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="5215c-186">Bir pencere oluşturma ancak Internet Explorer gibi görünür yapmayın odak genellikle Windows Masaüstü için taşınır ve penceresi ile etkileşim için görünür yapın.</span><span class="sxs-lookup"><span data-stu-id="5215c-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="5215c-187">Yazarak **$IE | Get-üye**, Internet Explorer için özellikleri ve yöntemleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5215c-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="5215c-188">Internet Explorer penceresi görmek için yazarak Vısıble özelliği $true olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5215c-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="5215c-189">Belirli bir Web adresine gidin yöntemini kullanarak sonra gidebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5215c-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="5215c-190">Internet Explorer nesne modeli diğer üyeleriyle kullanarak, Web sayfasından metin içeriği almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="5215c-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="5215c-191">Aşağıdaki komutu, geçerli Web sayfasının gövdesindeki HTML metin görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="5215c-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="5215c-192">Internet Explorer PowerShell içinden kapatmak için kendi Quit() yöntemini çağırırsınız:</span><span class="sxs-lookup"><span data-stu-id="5215c-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="5215c-193">Bu kapanmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="5215c-193">This will force it to close.</span></span> <span data-ttu-id="5215c-194">Hala bir COM nesnesi olarak görünen olsa bile IE değişken $ artık geçerli bir başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5215c-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="5215c-195">Bunu kullanmayı denerseniz, bir Otomasyon hatası alırsınız:</span><span class="sxs-lookup"><span data-stu-id="5215c-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="5215c-196">Kalan başvuru $ gibi bir komutla IE kaldırabilir ya da $null = ya da yazarak değişkeni tamamen kaldırın:</span><span class="sxs-lookup"><span data-stu-id="5215c-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="5215c-197">ActiveX yürütülebilir dosyalar çıkmak veya bir başvuru kaldırdığınızda çalışmaya devam için ortak bir standart yoktur.</span><span class="sxs-lookup"><span data-stu-id="5215c-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="5215c-198">Uygulamanın görünür olup, düzenlenen bir belge içine çalışıp çalışmadığını ve hatta Windows PowerShell hala çalışıp çalışmadığını gibi durumlarda, bağlı olarak uygulama olabilir veya değil sonlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5215c-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="5215c-199">Bu nedenle, Windows PowerShell içinde kullanmak istediğiniz yürütülebilir her ActiveX için sonlandırma davranışını test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5215c-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="5215c-200">.NET Framework Sarmalanan COM nesneleri hakkında uyarılar alma</span><span class="sxs-lookup"><span data-stu-id="5215c-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="5215c-201">Bazı durumlarda, ilişkili bir .NET Framework bir COM nesnesi olabilir *çalışma zamanı aranabilir sarmalayıcısı* veya RCW ve bu işlem tarafından kullanılan **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="5215c-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="5215c-202">RCW davranışını normal COM nesnesi davranışından farklı olabileceğinden **New-Object** sahip bir **Strıct** RCW erişimi hakkında uyarmak için parametre.</span><span class="sxs-lookup"><span data-stu-id="5215c-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="5215c-203">Belirtirseniz **Strıct** parametre ve ardından bir RCW kullanan bir COM nesnesi oluşturun, bir uyarı iletisi Al:</span><span class="sxs-lookup"><span data-stu-id="5215c-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

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

<span data-ttu-id="5215c-204">Nesne hala oluşturulur, ancak standart bir COM nesnesi olmadığını uyarılırsınız.</span><span class="sxs-lookup"><span data-stu-id="5215c-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>