---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell Komut Zincirini Anlama
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="70337-103">Windows PowerShell Komut Zincirini Anlama</span><span class="sxs-lookup"><span data-stu-id="70337-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="70337-104">Yöneltme neredeyse her yerde Windows PowerShell içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="70337-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="70337-105">Ekranda metin karşın, Windows PowerShell komutları arasındaki metni kanal değil.</span><span class="sxs-lookup"><span data-stu-id="70337-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="70337-106">Bunun yerine, nesneleri geçirir.</span><span class="sxs-lookup"><span data-stu-id="70337-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="70337-107">İşlem hatları için kullanılan gösterimi benzer kullanan için diğer Kabukları, bu nedenle ilk bakışta, bunu Windows PowerShell yeni bir şey tanıtır belirgin olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="70337-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="70337-108">Örneğin, kullanırsanız **dışarı barındırmak** çıkış sayfa tarafından görüntüsünü başka bir komuttan çıkış görünüyor yalnızca zorlamak için cmdlet'i ister sayfalarına parçalanmış ekranda görüntülenen normal metin:</span><span class="sxs-lookup"><span data-stu-id="70337-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="70337-109">Out-Host-disk belleği komutu bir öğedir yararlı ardışık düzen yavaş görüntülemek istediğiniz uzun çıktıya sahip olduğunda.</span><span class="sxs-lookup"><span data-stu-id="70337-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="70337-110">İşlemi çok CPU-yoğun ise özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="70337-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="70337-111">İşleme için aktarıldığından cmdlet dışarı ana bilgisayar tam bir sayfa görüntülemek için hazır olduğunda, sonraki sayfaya çıktı kullanılabilir hale gelene kadar ardışık düzeninde koyun cmdlet'leri işlemi durdurmak.</span><span class="sxs-lookup"><span data-stu-id="70337-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="70337-112">Windows PowerShell CPU ve bellek kullanımı izlemek için Windows Görev Yöneticisi'ni kullanırsanız, bu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70337-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="70337-113">Aşağıdaki komutu çalıştırın: **Get-Childıtem C:\\Windows-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="70337-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="70337-114">Bu komut için CPU ve bellek kullanımı karşılaştırın: **Get-Childıtem C:\\Windows-Recurse | -Disk belleği dışarı konak**.</span><span class="sxs-lookup"><span data-stu-id="70337-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="70337-115">Metni ekranda görün, ancak konsol penceresinde metin olarak nesneleri temsil etmek gerekli olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="70337-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="70337-116">Bu nedir, yalnızca bir gösterimi olan Windows PowerShell içinde üzerinde gerçekten giderek.</span><span class="sxs-lookup"><span data-stu-id="70337-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="70337-117">Örneğin, Get-Location cmdlet göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="70337-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="70337-118">Yazarsanız **Get-Location** geçerli konumunuz C sürücüsünün kök olsa da, aşağıdaki çıktı görmeniz:</span><span class="sxs-lookup"><span data-stu-id="70337-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="70337-119">Windows PowerShell metin ardışık, bir komut gibi veren **Get-Location | Dışarı konak**, gelen geçip geçmeyeceğini **Get-Location** için **dışarı konak** bunlar görüntülenir ekranda sırayla karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="70337-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="70337-120">Diğer bir deyişle, başlık bilgilerinin olsaydı **dışarı konak** ilk karakter alacağı '**C'**, ardından karakter '**:'**, ardından karakter ' **\\'**.</span><span class="sxs-lookup"><span data-stu-id="70337-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="70337-121">**Dışarı konak** cmdlet'i tarafından karakter çıktı ilişkilendirmek ne anlamı belirleyemedi **Get-Location** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="70337-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="70337-122">Ardışık düzeninde komutları izin vermek için metin kullanmak yerine iletişim, Windows PowerShell, nesneleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="70337-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="70337-123">Kullanıcı açısından, nesneleri bir birim olarak bilgiyi işleyebilir kolaylaştırır bir forma ilgili bilgiler paketini ve gerek duyduğunuz belirli öğeleri ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="70337-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="70337-124">**Get-Location** komutu geçerli yolunu içeren metin döndürmez.</span><span class="sxs-lookup"><span data-stu-id="70337-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="70337-125">Adlı bilgi paketi döndüren bir **PATHINFO** bazı diğer bilgilerle birlikte geçerli yolu içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="70337-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="70337-126">**Dışarı konak** cmdlet ardından gönderir bu **PATHINFO** ekran ve Windows PowerShell nesnesine karar ne görüntülemek için bilgi ve görüntülemek nasıl biçimlendirme kendi kurallarına göre.</span><span class="sxs-lookup"><span data-stu-id="70337-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="70337-127">Aslında, başlık bilgileri çıkış olarak **Get-Location** cmdlet'i yalnızca işleminin sonunda ekranda görüntülemek için veri biçimlendirmeyi işleminin bir parçası olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="70337-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="70337-128">Gördüğünüz bilgilerin özetini ve çıkış nesnesi değil eksiksiz bir gösterimini ekranda.</span><span class="sxs-lookup"><span data-stu-id="70337-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="70337-129">Olabilir koşuluyla, bir Windows PowerShell komut biz gördükleri konsol penceresinde görüntülenen daha nasıl kullanabilir daha fazla bilgi çıktısını görünür olmayan öğeleri almak?</span><span class="sxs-lookup"><span data-stu-id="70337-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="70337-130">Ek veriler nasıl görüntüleyebilirim?</span><span class="sxs-lookup"><span data-stu-id="70337-130">How do you view the extra data?</span></span> <span data-ttu-id="70337-131">Ve normal şekilde verileri bir Windows PowerShell farklı bir biçimde görüntülemek isterseniz kullanır?</span><span class="sxs-lookup"><span data-stu-id="70337-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="70337-132">Bu bölümde rest belirli öğeler seçme belirli Windows PowerShell nesnelerin yapısı nasıl bulabilir açıklanır ve onları daha kolay görüntüleme için ve bu bilgiyi alternatif çıkış konumlara gibi göndermek nasıl biçimlendirme dosyaları ve Yazıcılar.</span><span class="sxs-lookup"><span data-stu-id="70337-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>