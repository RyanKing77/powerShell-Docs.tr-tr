---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Out Cmdlet’leri ile Verileri Yeniden Yönlendirme
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321018"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="4e871-103">Out - ile verileri yeniden yönlendirme \* cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="4e871-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="4e871-104">Windows PowerShell doğrudan çıkış veri denetlemenize olanak sağlayan birçok cmdlet sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e871-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="4e871-105">Bu cmdlet'ler iki önemli özellikleri paylaşır.</span><span class="sxs-lookup"><span data-stu-id="4e871-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="4e871-106">İlk olarak, bunlar genellikle bazı metin biçimindeki verilere dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="4e871-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="4e871-107">Bunlar, metin girişi gerektiren sistem bileşenleri için veri çıktı çünkü bunlar bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e871-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="4e871-108">Bu nesnelerin metin olarak göstermek ihtiyaç duydukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4e871-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="4e871-109">Bu nedenle, bir Windows PowerShell konsol penceresi gördüğünüz gibi metin biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4e871-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="4e871-110">İkinci olarak, bu cmdlet'ler Windows PowerShell fiili kullanın **kullanıma** çünkü bunlar bilgileri Windows Powershell'den başka bir yere için gönderin.</span><span class="sxs-lookup"><span data-stu-id="4e871-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="4e871-111">**Dışarı konak** cmdlet'tir hiçbir özel durum: Windows PowerShell dışında ana penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4e871-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="4e871-112">Bu önemlidir, çünkü Windows PowerShell dışında veri gönderildiğinde, aslında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4e871-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="4e871-113">Bu sayfa verileri ana penceresi için bir işlem hattı oluşturmayı deneyin ve ardından bir liste olarak biçimlendirmek burada gösterildiği gibi çalışır, bu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4e871-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="4e871-114">İşlem bilgileri sayfaların liste biçiminde görüntülemek için komut bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e871-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="4e871-115">Bunun yerine, varsayılan Tablo listesini görüntüler:</span><span class="sxs-lookup"><span data-stu-id="4e871-115">Instead, it displays the default tabular list:</span></span>

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

<span data-ttu-id="4e871-116">**Dışarı konak** cmdlet verileri doğrudan konsola gönderir böylece **Format-List** komutu hiçbir zaman aldığı biçimlendirmek için herhangi bir şey.</span><span class="sxs-lookup"><span data-stu-id="4e871-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="4e871-117">Bu komut yapısı doğru şekilde eklemektir **dışarı konak** cmdlet'ini aşağıda gösterildiği gibi işlem hattının sonunda.</span><span class="sxs-lookup"><span data-stu-id="4e871-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="4e871-118">Bu, disk belleği ve görüntülenen önce listesindeki Biçimlendirilecek verilerini işleme neden olur.</span><span class="sxs-lookup"><span data-stu-id="4e871-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

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

<span data-ttu-id="4e871-119">Bu tümüne uygulanır **kullanıma** cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="4e871-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="4e871-120">Bir **kullanıma** cmdlet'i her zaman ardışık düzen sonunda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="4e871-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="4e871-121">Tüm **kullanıma** cmdlet'leri işleme çıkış metin olarak geçerli satırı uzunluk sınırları dahil olmak üzere, konsol penceresi için biçimlendirme kullanma.</span><span class="sxs-lookup"><span data-stu-id="4e871-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="4e871-122">Konsol çıktısı sayfalama (dışarı barındırma)</span><span class="sxs-lookup"><span data-stu-id="4e871-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="4e871-123">Varsayılan olarak, Windows PowerShell verileri tam olarak ne olduğunu ana penceresine gönderir cmdlet dışarı konak yapar.</span><span class="sxs-lookup"><span data-stu-id="4e871-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="4e871-124">Birincil kullanım dışarı konak cmdlet'tir verilerini sayfalama daha önce bahsedildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4e871-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="4e871-125">Örneğin, aşağıdaki komutu kullanır Get-Command cmdlet'in çıktısı, sayfa için dışarı barındırın:</span><span class="sxs-lookup"><span data-stu-id="4e871-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="4e871-126">Ayrıca **daha fazla** sayfa verilerine işlevi.</span><span class="sxs-lookup"><span data-stu-id="4e871-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="4e871-127">Windows PowerShell'de **daha fazla** çağıran bir işlev, **dışarı ana-disk belleği**.</span><span class="sxs-lookup"><span data-stu-id="4e871-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="4e871-128">Aşağıdaki komutu kullanarak gösterir **daha fazla** işlevini alma komutunun çıktısı sayfasında:</span><span class="sxs-lookup"><span data-stu-id="4e871-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="4e871-129">Daha fazla işlev bağımsız değişkenleri olarak bir veya daha fazla dosya adlarını dahil ederseniz, işlev belirtilen dosyaları okur ve içeriklerini ana sayfasında:</span><span class="sxs-lookup"><span data-stu-id="4e871-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="4e871-130">Çıkış atma (dışarı Null)</span><span class="sxs-lookup"><span data-stu-id="4e871-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="4e871-131">**Dışarı Null** cmdlet'i hemen aldığı herhangi bir giriş atmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4e871-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="4e871-132">Bu, yan komutu çalıştırmanın etkisi size gereksiz verileri atılıyor için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="4e871-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="4e871-133">Aşağıdaki komutu yazın, hiçbir şey komuttan ulaşırsınız değil:</span><span class="sxs-lookup"><span data-stu-id="4e871-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="4e871-134">**Dışarı Null** cmdlet'i hata çıkış atma değil.</span><span class="sxs-lookup"><span data-stu-id="4e871-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="4e871-135">Örneğin, aşağıdaki komutu girin, bir ileti Windows PowerShell 'Olan NotACommand' tanımıyor bildiren görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="4e871-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="4e871-136">Yazdırma veri (Out-yazıcı)</span><span class="sxs-lookup"><span data-stu-id="4e871-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="4e871-137">Kullanarak verileri yazdırabilirsiniz **Out-yazıcı** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4e871-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="4e871-138">**Out-yazıcı** cmdlet'i bir yazıcının adı belirtmezseniz varsayılan yazıcıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e871-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="4e871-139">Görüntü adı belirterek herhangi bir Windows tabanlı yazıcı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e871-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="4e871-140">Her türden yazıcı bağlantı noktası eşlemesi ya da gerçek fiziksel bir yazıcı için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e871-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="4e871-141">Yüklü Microsoft Office belge görüntüleme araçları varsa, örneğin, verileri bir görüntü dosyasına yazarak gönderebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4e871-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="4e871-142">Verileri kaydetme (dışarı dosya)</span><span class="sxs-lookup"><span data-stu-id="4e871-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="4e871-143">Kullanarak bir dosyaya konsol penceresinde yerine çıkış gönderebilirsiniz **dışarı dosya** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4e871-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="4e871-144">Aşağıdaki komut satırını işlemlerin bir listesi için dosya gönderir. **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="4e871-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="4e871-145">Kullanarak sonuçları **dışarı dosya** cmdlet'i geleneksel çıktı yeniden yönlendirme için kullanılan beklediğiniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4e871-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="4e871-146">Davranışını anlamak için hangi bağlamda bilmeniz gerekir **dışarı dosya** cmdlet'i çalışır.</span><span class="sxs-lookup"><span data-stu-id="4e871-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="4e871-147">Varsayılan olarak, **dışarı dosya** cmdlet'i bir Unicode dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4e871-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="4e871-148">Bu en iyi uzun vadede varsayılandır ancak ASCII dosyalarını beklediğiniz araçları ile varsayılan çıkış biçimini düzgün çalışmaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4e871-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="4e871-149">Varsayılan çıkış biçimini kullanarak ASCII'ye değiştirebilirsiniz **kodlama** parametresi:</span><span class="sxs-lookup"><span data-stu-id="4e871-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="4e871-150">**Dosya Dışarı** dosya biçimleri gibi konsol çıktısı aramak için içeriği.</span><span class="sxs-lookup"><span data-stu-id="4e871-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="4e871-151">Bu, çoğu durumda bir konsol penceresi içinde olduğu gibi kesilecek çıkış neden olur.</span><span class="sxs-lookup"><span data-stu-id="4e871-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="4e871-152">Örneğin aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4e871-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="4e871-153">Çıkış şuna benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="4e871-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="4e871-154">Ekran genişliği eşleştirilecek satırı sarar zorlamaz çıktısını almak için kullanabileceğiniz **genişliği** çizgi genişliği belirtmek için parametre.</span><span class="sxs-lookup"><span data-stu-id="4e871-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="4e871-155">Çünkü **genişliği** bir 32 bit tam sayı parametresi sahip olabilir en büyük değer 2147483647'dir.</span><span class="sxs-lookup"><span data-stu-id="4e871-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="4e871-156">Çizgi genişliği bu maksimum değeri ayarlamak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="4e871-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="4e871-157">**Dışarı dosya** cmdlet'tir en kullanışlı konsolda görüntülenen gibi çıkış kaydetmek istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="4e871-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="4e871-158">Çıkış biçimi üzerinde daha hassas denetim için daha gelişmiş araçlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e871-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="4e871-159">Nesne düzenlemesini hakkında ayrıntılarla birlikte sonraki bölümde de atacağız.</span><span class="sxs-lookup"><span data-stu-id="4e871-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>