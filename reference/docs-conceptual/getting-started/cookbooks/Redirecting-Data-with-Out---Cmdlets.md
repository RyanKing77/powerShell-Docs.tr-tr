---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Out Cmdlet’leri ile Verileri Yeniden Yönlendirme
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="e6522-103">Verilerle çıkış - yeniden yönlendirme \* cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="e6522-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="e6522-104">Windows PowerShell doğrudan çıktı veri denetlemenize olanak sağlayan birkaç cmdlet'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6522-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="e6522-105">Bu cmdlet'ler iki önemli özellikleri paylaşır.</span><span class="sxs-lookup"><span data-stu-id="e6522-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="e6522-106">İlk olarak, bunlar genellikle metin çeşit verileri dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="e6522-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="e6522-107">Metin girişi gerektiren sistem bileşenleri verileri çıktı çünkü bunu.</span><span class="sxs-lookup"><span data-stu-id="e6522-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="e6522-108">Bu metin olarak nesneleri temsil etmek ihtiyaç duydukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e6522-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="e6522-109">Bu nedenle, Windows PowerShell konsol penceresinde gördüğünüz metin biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e6522-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="e6522-110">İkinci olarak, bu cmdlet'ler Windows PowerShell fiil kullanın **çıkışı** bunlar bilgileri Windows Powershell'den başka bir yere için göndermek için.</span><span class="sxs-lookup"><span data-stu-id="e6522-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="e6522-111">**Dışarı konak** cmdlet'tir hiçbir özel durum: Windows PowerShell dışında ana penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e6522-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="e6522-112">Windows PowerShell dışında veri gönderildiğinde, aslında kaldırıldığı için bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e6522-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="e6522-113">Bir ardışık düzen konak penceresine bu sayfaları verileri oluşturmayı deneyin ve ardından bir liste olarak biçimlendirmek aşağıda gösterildiği gibi çalışır, bu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6522-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="e6522-114">İşlem bilgileri sayfaların listesi biçimde görüntülemek için komutu bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6522-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="e6522-115">Bunun yerine, varsayılan Tablo listesi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="e6522-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="e6522-116">**Dışarı konak** cmdlet verileri doğrudan konsola gönderir böylece **Format-List** komutu hiçbir zaman alan biçimlendirmek için herhangi bir şey.</span><span class="sxs-lookup"><span data-stu-id="e6522-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="e6522-117">Bu komut yapısı doğru yerleştirilecek yoludur **dışarı konak** cmdlet'ini aşağıda gösterildiği gibi ardışık düzen sonunda.</span><span class="sxs-lookup"><span data-stu-id="e6522-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="e6522-118">Bu, disk belleği olan ve görüntülenen önce listede Biçimlendirilecek işlem verileri neden olur.</span><span class="sxs-lookup"><span data-stu-id="e6522-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="e6522-119">Bu tümüne uygulanır **çıkışı** cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="e6522-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="e6522-120">Bir **çıkışı** cmdlet'inin ardışık düzen sonunda her zaman görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="e6522-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="e6522-121">Tüm **çıkışı** cmdlet'leri yürürlükte biçimlendirme satır uzunluğu sınırları dahil olmak üzere konsol penceresi için kullanarak bir metin olarak çıkış işleme.</span><span class="sxs-lookup"><span data-stu-id="e6522-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="e6522-122">Konsol çıktısı disk belleği (dışarı ana bilgisayar)</span><span class="sxs-lookup"><span data-stu-id="e6522-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="e6522-123">Varsayılan olarak, Windows PowerShell verileri tam olarak ne olduğunu konak penceresine gönderir cmdlet dışarı ana bilgisayar içermiyor.</span><span class="sxs-lookup"><span data-stu-id="e6522-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="e6522-124">Birincil kullanım dışarı konak cmdlet'tir disk belleği veri daha önce bahsedildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e6522-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="e6522-125">Örneğin, aşağıdaki komut kullandığı Get-Command cmdlet'i çıktısını sayfası dışarı ana bilgisayar:</span><span class="sxs-lookup"><span data-stu-id="e6522-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="e6522-126">Aynı zamanda **daha fazla** sayfa verilerine işlevi.</span><span class="sxs-lookup"><span data-stu-id="e6522-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="e6522-127">Windows PowerShell'de **daha fazla** çağıran bir işlev değil **dışarı ana bilgisayar-disk belleği**.</span><span class="sxs-lookup"><span data-stu-id="e6522-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="e6522-128">Aşağıdaki komutu kullanarak gösteren **daha fazla** işlevi Get-Command çıktısını sayfasında:</span><span class="sxs-lookup"><span data-stu-id="e6522-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="e6522-129">Daha fazla işlevi bağımsız değişken olarak bir veya daha fazla dosya adlarını dahil ederseniz, işlevi belirtilen dosyaları okuma ve içeriklerini ana sayfa:</span><span class="sxs-lookup"><span data-stu-id="e6522-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="e6522-130">Çıkış atma (dışarı Null)</span><span class="sxs-lookup"><span data-stu-id="e6522-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="e6522-131">**Dışarı Null** cmdlet hemen aldığı herhangi bir giriş atmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e6522-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="e6522-132">Bu, bir yan-bir komutu çalıştırmak, sonuç elde gereksiz verileri atılıyor için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e6522-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="e6522-133">Ne zaman aşağıdaki komutu yazın, herhangi bir şey komuttan ulaşırsınız değil:</span><span class="sxs-lookup"><span data-stu-id="e6522-133">When type the following command, you do not get anything back from the command:</span></span>

```powreshell
Get-Command | Out-Null
```

<span data-ttu-id="e6522-134">**Dışarı Null** cmdlet hata çıkış atma değil.</span><span class="sxs-lookup"><span data-stu-id="e6522-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="e6522-135">Örneğin, aşağıdaki komutu girin, bir ileti Windows PowerShell 'Olan NotACommand' tanımıyor bildiren görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="e6522-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="e6522-136">Yazdırma veri (Out-yazıcı)</span><span class="sxs-lookup"><span data-stu-id="e6522-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="e6522-137">Kullanarak verileri yazdırabilirsiniz **Out-yazıcı** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e6522-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="e6522-138">**Out-yazıcı** cmdlet'i bir yazıcı adı belirtmezseniz, varsayılan yazıcı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6522-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="e6522-139">Görünen adını belirterek herhangi bir Windows tabanlı yazıcıyı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6522-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="e6522-140">Yazıcı bağlantı noktası eşlemesi veya hatta gerçek fiziksel yazıcı herhangi bir tür için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e6522-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="e6522-141">Yüklü Microsoft Office belge görüntü oluşturma araçlarının varsa, örneğin, verileri bir görüntü dosyasına yazarak gönderebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6522-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="e6522-142">Verileri kaydetme (out-File)</span><span class="sxs-lookup"><span data-stu-id="e6522-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="e6522-143">Kullanarak bir dosyaya konsol penceresi yerine çıktı gönderebilirsiniz **out-File** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e6522-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="e6522-144">Aşağıdaki komut satırını işlemlerin listesini dosyasına gönderir **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="e6522-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="e6522-145">Kullanarak sonuçlarını **out-File** cmdlet geleneksel çıktı yeniden yönlendirme için kullanılıyorsa, beklediğiniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e6522-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="e6522-146">Davranışını anlamak için bağlamı bilmeniz gerekir **out-File** cmdlet'i çalışır.</span><span class="sxs-lookup"><span data-stu-id="e6522-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="e6522-147">Varsayılan olarak, **out-File** cmdlet'i bir Unicode dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6522-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="e6522-148">Bu en iyi uzun vadede varsayılandır ancak ASCII dosyalarını beklediğiniz araçları ile varsayılan çıkış biçimi düzgün çalışmaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e6522-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="e6522-149">Varsayılan çıkış biçimi için ASCII kullanarak değiştirebileceğiniz **kodlama** parametre:</span><span class="sxs-lookup"><span data-stu-id="e6522-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="e6522-150">**Out-File** dosya biçimleri gibi konsol çıktısı aramak için içeriği.</span><span class="sxs-lookup"><span data-stu-id="e6522-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="e6522-151">Bu, çoğu durumda konsol penceresinde olduğu gibi kesilecek çıkış neden olur.</span><span class="sxs-lookup"><span data-stu-id="e6522-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="e6522-152">Örneğin aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e6522-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="e6522-153">Çıktı şuna benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="e6522-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="e6522-154">Ekran genişliği eşleşecek şekilde satır sarmalayan zorlamaz çıkış almak için kullanabileceğiniz **genişliği** çizgi genişliğini belirlemek için parametre.</span><span class="sxs-lookup"><span data-stu-id="e6522-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="e6522-155">Çünkü **genişliği** 32 bit tamsayı parametresi sahip olabilir en fazla 2147483647 değerdir.</span><span class="sxs-lookup"><span data-stu-id="e6522-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="e6522-156">Çizgi genişliği bu maksimum değere ayarlamak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="e6522-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="e6522-157">**Out-File** konsolda görüntülenen gibi çıkışı kaydetmek istediğinizde cmdlet en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e6522-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="e6522-158">Çıktı biçimi üzerinde daha hassas denetim için daha gelişmiş araçlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6522-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="e6522-159">Sonraki bölümde nesnesi düzenleme hakkında ayrıntılarla birlikte de ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="e6522-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>