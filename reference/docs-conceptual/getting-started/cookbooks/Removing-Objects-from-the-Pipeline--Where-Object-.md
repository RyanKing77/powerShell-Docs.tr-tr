---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ardışık düzen tarafından nesneleri kaldırılıyor burada nesnesi
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 2d89defdb1b234a9d0021fc06e1f05a95bb1bce9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="8c7fc-103">Ardışık Düzen (Where-Object) nesneleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="8c7fc-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="8c7fc-104">Windows PowerShell'de, genellikle oluşturmak ve istediğinizden daha daha çok nesneyi ardışık düzene geçirin.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="8c7fc-105">Kullanarak görüntülemek için belirli nesnelerin özelliklerini belirtebilirsiniz **biçimi** cmdlet'leri, ancak bu yardımcı görüntüden tüm nesneleri kaldırmanın sorunlu.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="8c7fc-106">Yalnızca bir alt kümesini başlangıçta oluşturulan nesneler üzerinde eylemleri gerçekleştirebilirsiniz nesneleri bir ardışık düzen sonundan önce Filtre isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="8c7fc-107">Windows PowerShell içeren bir **Where-Object** her nesne ardışık düzeninde test ve yalnızca belirli test koşulu karşılıyorsa ardışık düzeni iletmektir izin veren cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-107">Windows PowerShell includes a **Where-Object** cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="8c7fc-108">Test geçmeyin nesneler ardışık düzen tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="8c7fc-109">Test durumu değeri olarak sağladığınız **nereye ObjectFilterScript** parametresi.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-109">You supply the test condition as the value of the **Where-ObjectFilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="8c7fc-110">Where-Object ile basit testleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="8c7fc-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="8c7fc-111">Değeri **FilterScript** olan bir *betik bloğu* - köşeli ayraçları {} tarafından bir veya daha fazla Windows PowerShell komutlarını -, hesaplar true veya false.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="8c7fc-112">Bu komut dosyası blokları çok basit olabilir, ancak bunları oluşturmak için başka bir Windows PowerShell kavram hakkında Karşılaştırma işleçleri bilerek gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="8c7fc-113">Bir karşılaştırma işleci bunu her bir tarafta görüntülenen öğeleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="8c7fc-114">Karşılaştırma işleçleri ile başlar bir '-' karakteri ve bir ad tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="8c7fc-115">Temel Karşılaştırma işleçleri neredeyse her türlü nesnesi üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="8c7fc-116">Daha gelişmiş Karşılaştırma işleçleri yalnızca metin veya diziler üzerinde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="8c7fc-117">Metin ile çalışırken, varsayılan olarak, Windows PowerShell Karşılaştırma işleçleri büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="8c7fc-118">Dikkat edilecek noktalar ayrıştırma nedeniyle <> gibi simgeler ve = Karşılaştırma işleçleri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="8c7fc-119">Bunun yerine, Karşılaştırma işleçleri harfini oluşur.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="8c7fc-120">Temel Karşılaştırma işleçleri aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="8c7fc-121">Karşılaştırma işleci</span><span class="sxs-lookup"><span data-stu-id="8c7fc-121">Comparison Operator</span></span>|<span data-ttu-id="8c7fc-122">Anlamı</span><span class="sxs-lookup"><span data-stu-id="8c7fc-122">Meaning</span></span>|<span data-ttu-id="8c7fc-123">Örnek (true verir)</span><span class="sxs-lookup"><span data-stu-id="8c7fc-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="8c7fc-124">-eq</span><span class="sxs-lookup"><span data-stu-id="8c7fc-124">-eq</span></span>|<span data-ttu-id="8c7fc-125">eşittir</span><span class="sxs-lookup"><span data-stu-id="8c7fc-125">is equal to</span></span>|<span data-ttu-id="8c7fc-126">1 - eq 1</span><span class="sxs-lookup"><span data-stu-id="8c7fc-126">1 -eq 1</span></span>|
|<span data-ttu-id="8c7fc-127">-ne</span><span class="sxs-lookup"><span data-stu-id="8c7fc-127">-ne</span></span>|<span data-ttu-id="8c7fc-128">Eşit değil</span><span class="sxs-lookup"><span data-stu-id="8c7fc-128">Is not equal to</span></span>|<span data-ttu-id="8c7fc-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="8c7fc-129">1 -ne 2</span></span>|
|<span data-ttu-id="8c7fc-130">-lt</span><span class="sxs-lookup"><span data-stu-id="8c7fc-130">-lt</span></span>|<span data-ttu-id="8c7fc-131">Olan küçüktür</span><span class="sxs-lookup"><span data-stu-id="8c7fc-131">Is less than</span></span>|<span data-ttu-id="8c7fc-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="8c7fc-132">1 -lt 2</span></span>|
|<span data-ttu-id="8c7fc-133">-le</span><span class="sxs-lookup"><span data-stu-id="8c7fc-133">-le</span></span>|<span data-ttu-id="8c7fc-134">Küçük veya eşittir</span><span class="sxs-lookup"><span data-stu-id="8c7fc-134">Is less than or equal to</span></span>|<span data-ttu-id="8c7fc-135">1 - le 2</span><span class="sxs-lookup"><span data-stu-id="8c7fc-135">1 -le 2</span></span>|
|<span data-ttu-id="8c7fc-136">-gt</span><span class="sxs-lookup"><span data-stu-id="8c7fc-136">-gt</span></span>|<span data-ttu-id="8c7fc-137">Değerinden büyük</span><span class="sxs-lookup"><span data-stu-id="8c7fc-137">Is greater than</span></span>|<span data-ttu-id="8c7fc-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="8c7fc-138">2 -gt 1</span></span>|
|<span data-ttu-id="8c7fc-139">-ge</span><span class="sxs-lookup"><span data-stu-id="8c7fc-139">-ge</span></span>|<span data-ttu-id="8c7fc-140">Büyüktür veya eşittir</span><span class="sxs-lookup"><span data-stu-id="8c7fc-140">Is greater than or equal to</span></span>|<span data-ttu-id="8c7fc-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="8c7fc-141">2 -ge 1</span></span>|
|<span data-ttu-id="8c7fc-142">-gibi</span><span class="sxs-lookup"><span data-stu-id="8c7fc-142">-like</span></span>|<span data-ttu-id="8c7fc-143">(Metni için joker karakter karşılaştırma) benzer</span><span class="sxs-lookup"><span data-stu-id="8c7fc-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="8c7fc-144">"dosyam.doc"-gibi "f\*.yoğun?"</span><span class="sxs-lookup"><span data-stu-id="8c7fc-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="8c7fc-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="8c7fc-145">-notlike</span></span>|<span data-ttu-id="8c7fc-146">(Metni için joker karakter karşılaştırma) gibi değil</span><span class="sxs-lookup"><span data-stu-id="8c7fc-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="8c7fc-147">"dosyam.doc"-notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="8c7fc-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="8c7fc-148">-içerir</span><span class="sxs-lookup"><span data-stu-id="8c7fc-148">-contains</span></span>|<span data-ttu-id="8c7fc-149">içerir</span><span class="sxs-lookup"><span data-stu-id="8c7fc-149">Contains</span></span>|<span data-ttu-id="8c7fc-150">1,2,3 - 1 içerir</span><span class="sxs-lookup"><span data-stu-id="8c7fc-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="8c7fc-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="8c7fc-151">-notcontains</span></span>|<span data-ttu-id="8c7fc-152">İçermiyor</span><span class="sxs-lookup"><span data-stu-id="8c7fc-152">Does not contain</span></span>|<span data-ttu-id="8c7fc-153">1,2,3 - notcontains 4</span><span class="sxs-lookup"><span data-stu-id="8c7fc-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="8c7fc-154">WHERE-Object komut dosyası blokları özel değişkeni '$_' ardışık düzeninde geçerli nesneye başvurma kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-154">Where-Object script blocks use the special variable '$_' to refer to the current object in the pipeline.</span></span> <span data-ttu-id="8c7fc-155">Burada, nasıl çalıştığına ilişkin bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-155">Here is an example of how it works.</span></span> <span data-ttu-id="8c7fc-156">Sayıdan oluşan bir liste varsa ve yalnızca 3'ten az olan ayarlara dönmek isterseniz, Where-Object yazarak sayıları filtrelemek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c7fc-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="8c7fc-157">Nesne özellikleri bağlı filtreleme</span><span class="sxs-lookup"><span data-stu-id="8c7fc-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="8c7fc-158">$_ Geçerli ardışık düzen nesnesine başvuruyor beri özelliklerini testlerimiz için erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-158">Since $_ refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="8c7fc-159">Örnek olarak, biz WMI Win32_SystemDriver sınıfında bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="8c7fc-160">Belirli bir sistemi üzerinde sistem sürücüleri yüzlerce olabilir, ancak yalnızca sistem sürücüleri, çalıştırmakta olduğunuz olanlar gibi belirli bir dizi ilginizi çekebilir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="8c7fc-161">Win32_SystemDriver üyeleri görüntülemek için Get-üye kullanıyorsanız (**Get-WmiObject-sınıfı Win32_SystemDriver | Get-Member - MemberType özelliği**) durumudur ilgili özellik ve sürücü çalıştırırken "Çalışır" bir değere sahip olduğundan görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="8c7fc-162">Sistem sürücüleri yalnızca çalışan olanları yazarak seçerek filtreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c7fc-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="8c7fc-163">Bu hala uzun bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-163">This still produces a long list.</span></span> <span data-ttu-id="8c7fc-164">Yalnızca StartMode değer de test ederek otomatik olarak başlayacak şekilde ayarlayın sürücüleri seçmek için filtre isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c7fc-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

<span data-ttu-id="8c7fc-165">Bu bize, çok sayıda sürücülerin çalışmakta olduğunu biliyoruz çünkü artık ihtiyacımız bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="8c7fc-166">Aslında, büyük olasılıkla bu noktada ihtiyacımız yalnızca bilgilerdir adı ve görünen ad.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="8c7fc-167">Aşağıdaki komutu kadar basit çıktısında kaynaklanan yalnızca bu iki özellik içerir:</span><span class="sxs-lookup"><span data-stu-id="8c7fc-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="8c7fc-168">Yukarıdaki komutta iki Where-Object öğesi vardır, ancak bunlar içinde tek bir Where-Object öğesi kullanılarak ifade edilebilir ve bu gibi mantıksal işleç:</span><span class="sxs-lookup"><span data-stu-id="8c7fc-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="8c7fc-169">Standart mantıksal işleçleri aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c7fc-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="8c7fc-170">Mantıksal işleci</span><span class="sxs-lookup"><span data-stu-id="8c7fc-170">Logical Operator</span></span>|<span data-ttu-id="8c7fc-171">Anlamı</span><span class="sxs-lookup"><span data-stu-id="8c7fc-171">Meaning</span></span>|<span data-ttu-id="8c7fc-172">Örnek (true verir)</span><span class="sxs-lookup"><span data-stu-id="8c7fc-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="8c7fc-173">- ve</span><span class="sxs-lookup"><span data-stu-id="8c7fc-173">-and</span></span>|<span data-ttu-id="8c7fc-174">Mantıksal ve; Her iki tarafında da doğru olduğunda true</span><span class="sxs-lookup"><span data-stu-id="8c7fc-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="8c7fc-175">(1 - eq 1) - ve (2 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="8c7fc-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="8c7fc-176">- veya</span><span class="sxs-lookup"><span data-stu-id="8c7fc-176">-or</span></span>|<span data-ttu-id="8c7fc-177">Mantıksal veya; Her iki taraf doğru ise true</span><span class="sxs-lookup"><span data-stu-id="8c7fc-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="8c7fc-178">(1 - eq 1) - veya (1 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="8c7fc-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="8c7fc-179">-değil</span><span class="sxs-lookup"><span data-stu-id="8c7fc-179">-not</span></span>|<span data-ttu-id="8c7fc-180">Mantıksal değil; çevirmelerinin true ve false</span><span class="sxs-lookup"><span data-stu-id="8c7fc-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="8c7fc-181">-değil (1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="8c7fc-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="8c7fc-182">Mantıksal değil; çevirmelerinin true ve false</span><span class="sxs-lookup"><span data-stu-id="8c7fc-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="8c7fc-183">\!(1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="8c7fc-183">\!(1 -eq 2)</span></span>|