---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Hangi s yeni 50 PowerShell ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 35b825cfa6ea720d0af3537c5d1b16c5ececb701
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953591"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="733fa-103">Ne&#39;s Windows PowerShell ISE'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="733fa-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="733fa-104">Bu konu, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) sürümlerde sunulan yeni ve güncelleştirilmiş özelliklerin açıklar.</span><span class="sxs-lookup"><span data-stu-id="733fa-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="733fa-105">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="733fa-105">Feature description</span></span>
<span data-ttu-id="733fa-106">Windows PowerShell ISE yazma, çalıştırma ve komut dosyaları ve modüller bir grafik ve sezgisel ortamında test etme olanak tanıyan bir ana bilgisayar uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="733fa-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="733fa-107">Sözdizimi renklendirmesi gibi anahtar özellikleri sekme tamamlama, visual hata ayıklama, Unicode uyumluluk ve bağlama duyarlı Yardım zengin bir komut dosyası deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="733fa-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="733fa-108">Windows PowerShell ISE genel bakış için bkz: [Windows PowerShell Tümleşik komut dosyası ortamı genel bakış](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="733fa-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="733fa-109">Windows PowerShell ISE yeni ve değiştirilmiş işlevleri</span><span class="sxs-lookup"><span data-stu-id="733fa-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="733fa-110">Aşağıdaki tabloda, Windows PowerShell'de Windows PowerShell ISE bu sürümü için yeni ve değiştirilmiş özellikler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="733fa-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="733fa-111">Özellik/işlevsellik</span><span class="sxs-lookup"><span data-stu-id="733fa-111">Feature/functionality</span></span>|<span data-ttu-id="733fa-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="733fa-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="733fa-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="733fa-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="733fa-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="733fa-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="733fa-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="733fa-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="733fa-116">X</span><span class="sxs-lookup"><span data-stu-id="733fa-116">X</span></span>|<span data-ttu-id="733fa-117">X</span><span class="sxs-lookup"><span data-stu-id="733fa-117">X</span></span>||
|<span data-ttu-id="733fa-118">**[Snippets](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="733fa-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="733fa-119">X</span><span class="sxs-lookup"><span data-stu-id="733fa-119">X</span></span>|<span data-ttu-id="733fa-120">X</span><span class="sxs-lookup"><span data-stu-id="733fa-120">X</span></span>||
|<span data-ttu-id="733fa-121">**[Eklenti araçları](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="733fa-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="733fa-122">X</span><span class="sxs-lookup"><span data-stu-id="733fa-122">X</span></span>|<span data-ttu-id="733fa-123">X</span><span class="sxs-lookup"><span data-stu-id="733fa-123">X</span></span>||
|<span data-ttu-id="733fa-124">**[Yeniden başlatma Yöneticisi ve otomatik kayıt](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="733fa-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="733fa-125">X</span><span class="sxs-lookup"><span data-stu-id="733fa-125">X</span></span>|<span data-ttu-id="733fa-126">X</span><span class="sxs-lookup"><span data-stu-id="733fa-126">X</span></span>||
|<span data-ttu-id="733fa-127">**[En son kullanılan listesi](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="733fa-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="733fa-128">X</span><span class="sxs-lookup"><span data-stu-id="733fa-128">X</span></span>|<span data-ttu-id="733fa-129">X</span><span class="sxs-lookup"><span data-stu-id="733fa-129">X</span></span>||
|<span data-ttu-id="733fa-130">**[Konsol bölmesinde](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="733fa-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="733fa-131">X</span><span class="sxs-lookup"><span data-stu-id="733fa-131">X</span></span>|<span data-ttu-id="733fa-132">X</span><span class="sxs-lookup"><span data-stu-id="733fa-132">X</span></span>||
|<span data-ttu-id="733fa-133">**[Komut satırı anahtarları](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="733fa-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="733fa-134">X</span><span class="sxs-lookup"><span data-stu-id="733fa-134">X</span></span>|<span data-ttu-id="733fa-135">X</span><span class="sxs-lookup"><span data-stu-id="733fa-135">X</span></span>||
|<span data-ttu-id="733fa-136">**[Yeni Düzenleyicisi özellikleri](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="733fa-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="733fa-137">X</span><span class="sxs-lookup"><span data-stu-id="733fa-137">X</span></span>|<span data-ttu-id="733fa-138">X</span><span class="sxs-lookup"><span data-stu-id="733fa-138">X</span></span>||
|<span data-ttu-id="733fa-139">**[Yeni Yardım Görüntüleyici](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="733fa-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="733fa-140">X</span><span class="sxs-lookup"><span data-stu-id="733fa-140">X</span></span>|<span data-ttu-id="733fa-141">X</span><span class="sxs-lookup"><span data-stu-id="733fa-141">X</span></span>||
|<span data-ttu-id="733fa-142">**[Göster-Command cmdlet'i](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="733fa-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="733fa-143">X</span><span class="sxs-lookup"><span data-stu-id="733fa-143">X</span></span>|<span data-ttu-id="733fa-144">X</span><span class="sxs-lookup"><span data-stu-id="733fa-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="733fa-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="733fa-145">IntelliSense</span></span>
<span data-ttu-id="733fa-146">**ISE 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="733fa-147">IntelliSense Windows PowerShell ISE parçası olan bir otomatik tamamlama Yardım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="733fa-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="733fa-148">IntelliSense, siz yazarken, büyük olasılıkla cmdlet'leri, parametreleri, parametre değerlerini, dosyalar veya klasörler eşleşen tıklanabilir menüleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="733fa-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="733fa-149">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-149">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-150">IntelliSense eklenmesiyle, komut dosyaları oluşturmak için Windows PowerShell ISE kullandığınızda cmdlet'ler ve söz dizimine bulmak daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="733fa-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="733fa-151">Yeni komut dosyası oluştururken, Windows PowerShell öğrenmek için Windows PowerShell ISE de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="733fa-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="733fa-152">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-152">**What works differently?**</span></span>

<span data-ttu-id="733fa-153">Cmdlet'lerini Windows PowerShell ISE 3.0 veya daha yenisi yazdığınızda, göz atın ve uygun komutları seçim olanak tanıyan bir kaydırılabilir ve tıklatılabilir menüsünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="733fa-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="733fa-154">Kod parçacıkları</span><span class="sxs-lookup"><span data-stu-id="733fa-154">Snippets</span></span>
<span data-ttu-id="733fa-155">**ISE 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="733fa-156">*Kod parçacıkları* kısa bölümler Windows PowerShell kodunun, Windows PowerShell ISE oluşturduğunuz betikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="733fa-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="733fa-157">Windows PowerShell ISE parçacıkları varsayılan kümesi ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="733fa-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="733fa-158">Kullanarak parçacıkları ekleyebilirsiniz **yeni kod parçacığında** Windows PowerShell ISE çalışırken cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="733fa-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="733fa-159">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-159">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-160">Parçacıkları kullanarak hızlı bir şekilde derleyecek ve ortamınızı yönetmek için betikler oluşturma.</span><span class="sxs-lookup"><span data-stu-id="733fa-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="733fa-161">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-161">**What works differently?**</span></span>

<span data-ttu-id="733fa-162">Parçacıkları Windows PowerShell 3.0 veya üstü, üzerinde kullanmak için **Düzenle** menüsünde tıklatın **Başlat parçacıkları**, veya basın **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="733fa-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="733fa-163">Eklenti araçları</span><span class="sxs-lookup"><span data-stu-id="733fa-163">Add-on tools</span></span>
<span data-ttu-id="733fa-164">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-165">Windows PowerShell ISE artık nesne modelini kullanarak eklenen Windows Presentation Foundation (WPF) denetimler eklenti araçları destekler.</span><span class="sxs-lookup"><span data-stu-id="733fa-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="733fa-166">Eklenti araçları konsol dikey veya yatay bölmesinde olarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="733fa-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="733fa-167">Birden fazla eklenti araçları bölmesinde sekmeli bir denetim olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="733fa-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="733fa-168">Ayrıca, ekleyin veya Microsoft dışı taraflarca üretilen eklenti araçları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="733fa-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="733fa-169">Alma veya eklenti araçları kaldırma hakkında daha fazla bilgi için bkz: [Windows PowerShell ISE işlemleri](http://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="733fa-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="733fa-170">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-170">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-171">Eklentiler genişletmenizi ve komut dosyası deneyiminizi iyileştirmek veya Windows PowerShell ISE işlevsellik ekleyen araçları ile Windows PowerShell ISE özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="733fa-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="733fa-172">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-172">**What works differently?**</span></span>

<span data-ttu-id="733fa-173">Windows PowerShell ISE 3.0 ve sonraki sürümleri ile birlikte gelir **komutları** eklentisi.</span><span class="sxs-lookup"><span data-stu-id="733fa-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="733fa-174">**Komutları** eklenti cmdlet'leri göz atarak cmdlet'leri yan yana ile ilgili yardıma erişmek verir **betik** ve **konsol** bölmeleri.</span><span class="sxs-lookup"><span data-stu-id="733fa-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="733fa-175">Ek eklentilerin kullanarak bulunabilir **açık eklenti araçları Web sitesi** komutunu **eklentileri** menüsü.</span><span class="sxs-lookup"><span data-stu-id="733fa-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="733fa-176">Yöneticisi ve otomatik kayıt yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="733fa-176">Restart manager and auto-save</span></span>
<span data-ttu-id="733fa-177">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-178">Windows PowerShell ISE artık otomatik olarak açık komut dosyalarınızı her iki dakikada ayrı bir konuma kaydeder.</span><span class="sxs-lookup"><span data-stu-id="733fa-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="733fa-179">Komut dosyalarını kaydedilmedi olsa bile Windows PowerShell ISE çalışmayı durduruyor ya da Windows PowerShell ISE yeniden başlatıldıktan sonra işletim sistemini yeniden başlatılırsa, kurtarır olan komut dosyaları son oturumu açın.</span><span class="sxs-lookup"><span data-stu-id="733fa-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="733fa-180">Otomatik kaydetme aralığını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="733fa-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="733fa-181">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-181">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-182">Artık Windows PowerShell ISE açık komut dosyalarınızı beklenmeyen bir yeniden başlatma durumunda otomatik olarak kaydedilir bilerek içinde çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="733fa-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="733fa-183">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-183">**What works differently?**</span></span>

<span data-ttu-id="733fa-184">Windows PowerShell ISE 2.0 komut dosyaları otomatik olarak yeniden başlatma durumunda kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="733fa-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="733fa-185">En son kullanılan listesi</span><span class="sxs-lookup"><span data-stu-id="733fa-185">Most-recently used list</span></span>
<span data-ttu-id="733fa-186">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-187">Windows PowerShell ISE artık dosyalar için en son kullanılan bir listesi vardır.</span><span class="sxs-lookup"><span data-stu-id="733fa-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="733fa-188">Windows PowerShell ISE'de bir dosyayı açtığınızda, dosyanın en son kullanılan listeye üzerinde eklenen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="733fa-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="733fa-189">En son kullanılan listede yer alan dosyalar varsayılan sayısını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="733fa-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="733fa-190">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-190">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-191">Artık, en son kullanılan listesinde kolayca sık kullanılan dosyalarınıza erişmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="733fa-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="733fa-192">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-192">**What works differently?**</span></span>

<span data-ttu-id="733fa-193">Windows PowerShell ISE 2.0 en son kullanılan listesini yok.</span><span class="sxs-lookup"><span data-stu-id="733fa-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="733fa-194">Konsol bölmesinde</span><span class="sxs-lookup"><span data-stu-id="733fa-194">Console Pane</span></span>
<span data-ttu-id="733fa-195">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-196">Tek bir konsol bölmesine birleştirilmiştir, ayrı komut ve çıktı bölmeleri, Windows PowerShell ISE ilk sürümünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="733fa-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="733fa-197">Konsol bölmesinde işlevi ve tipik bir Windows PowerShell Konsolu görünümünü benzer, ancak (Bu konuda açıklanan çoğu) aşağıdaki geliştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="733fa-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="733fa-198">Giriş metni (çıktı metin değil), XML sözdizimi dahil olmak üzere sözdizimi renklendirmesi</span><span class="sxs-lookup"><span data-stu-id="733fa-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="733fa-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="733fa-199">IntelliSense</span></span>

- <span data-ttu-id="733fa-200">Ayraç eşleştirme</span><span class="sxs-lookup"><span data-stu-id="733fa-200">Brace matching</span></span>

- <span data-ttu-id="733fa-201">Hata göstergesi</span><span class="sxs-lookup"><span data-stu-id="733fa-201">Error indication</span></span>

- <span data-ttu-id="733fa-202">Tam Unicode desteği</span><span class="sxs-lookup"><span data-stu-id="733fa-202">Full Unicode support</span></span>

- <span data-ttu-id="733fa-203">**F1** bağlama duyarlı Yardım</span><span class="sxs-lookup"><span data-stu-id="733fa-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="733fa-204">**CTRL + F1** bağlama duyarlı Göster komutu</span><span class="sxs-lookup"><span data-stu-id="733fa-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="733fa-205">Karmaşık komut dosyası ve sağdan sola desteği</span><span class="sxs-lookup"><span data-stu-id="733fa-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="733fa-206">Yazı tipi desteği</span><span class="sxs-lookup"><span data-stu-id="733fa-206">Font support</span></span>

- <span data-ttu-id="733fa-207">Yakınlaştır</span><span class="sxs-lookup"><span data-stu-id="733fa-207">Zoom</span></span>

- <span data-ttu-id="733fa-208">Satırı seçin ve blok seçim modları</span><span class="sxs-lookup"><span data-stu-id="733fa-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="733fa-209">Yazılan içerik tuşuna bastığınızda komut satırında korunmasını **yukarı** konsolda geçmişini görüntülemek için oku</span><span class="sxs-lookup"><span data-stu-id="733fa-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="733fa-210">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-210">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-211">Konsol bölmesinde değişikliklerin eklenmesi, konsol arabirimiyle daha tutarlı bir komut dosyası deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="733fa-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="733fa-212">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-212">**What works differently?**</span></span>

<span data-ttu-id="733fa-213">Windows PowerShell ISE 2.0 ayrı komut ve çıktı bölmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="733fa-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="733fa-214">Komut satırı anahtarları</span><span class="sxs-lookup"><span data-stu-id="733fa-214">Command-line switches</span></span>
<span data-ttu-id="733fa-215">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-216">Komut satırından Windows PowerShell ISE başlatırsanız (yazarak **powershell_ise.exe**), aşağıdaki yeni komut satırı anahtarları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="733fa-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="733fa-217">*-NoProfile*: Windows PowerShell ISE çalıştırılmadan başlatır **$profile**</span><span class="sxs-lookup"><span data-stu-id="733fa-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="733fa-218">*-Yardım*: Yardım penceresini görüntüler</span><span class="sxs-lookup"><span data-stu-id="733fa-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="733fa-219">*-mta*: Windows PowerShell ISE birden çok iş parçacıklı grup modunda başlatır.</span><span class="sxs-lookup"><span data-stu-id="733fa-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="733fa-220">Tek iş parçacıklı bölme modunda, Windows PowerShell ISE için varsayılan çalışma modu olan veya *- sta*.</span><span class="sxs-lookup"><span data-stu-id="733fa-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="733fa-221">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-221">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-222">Bu komut satırı anahtarları eklenmesi, Windows PowerShell ISE çalıştığı ortam denetlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="733fa-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="733fa-223">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-223">**What works differently?**</span></span>

<span data-ttu-id="733fa-224">Windows PowerShell ISE 2.0 Bu komut satırı anahtarları tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="733fa-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="733fa-225">Yeni Düzenleyicisi özellikleri</span><span class="sxs-lookup"><span data-stu-id="733fa-225">New editor features</span></span>
<span data-ttu-id="733fa-226">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-227">Diğer Windows PowerShell ISE düzenleme özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="733fa-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="733fa-228">**XML sözdizimi renklendirmesi**Windows PowerShell ISE şimdi renkleri XML sözdizimi aynı şekilde Windows PowerShell sözdizimi renkleri gibi.</span><span class="sxs-lookup"><span data-stu-id="733fa-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="733fa-229">**Ayraç eşleştirme** Windows PowerShell ISE eşleşen ayraç ve vurgulama içerir ve aşağıdaki şekillerde kullanılabilir: (örneğin, kullanarak **eşleşen Git** komut veya **Ctrl +]** bulur Seçili açılan parantez varsa, kapanış ayracı).</span><span class="sxs-lookup"><span data-stu-id="733fa-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="733fa-230">**Anahat görünümü** betik bölmesine destekler daraltma veya kodun bölümlerini artı veya eksi tıklayarak genişletme imzalar sol kenar boşluğunda sağlayan anahat oluşturma,.</span><span class="sxs-lookup"><span data-stu-id="733fa-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="733fa-231">Küme ayraçları kullanabilirsiniz veya **#region** ve **#endregion** başında ve sonunda daraltılabilir bölümünün işaretlemek için etiketler.</span><span class="sxs-lookup"><span data-stu-id="733fa-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="733fa-232">Genişlet veya daralt tüm bölgeler için basın **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="733fa-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="733fa-233">**Sürükle ve bırak metin düzenleme**destekler sürükleyip metin düzenleme artık Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="733fa-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="733fa-234">Herhangi bir metin bloğunu seçin ve bu metin düzenleyicisi veya Konsolu metni taşımak için başka bir konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="733fa-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="733fa-235">Ctrl tuşunu basılı tutarak fare düğmesini bıraktığınızda seçili metni sürükleyin, metin yeni bir konuma kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="733fa-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="733fa-236">Windows PowerShell ISE dosyalarını sürükleyip Windows PowerShell ISE bu sürümü, aynı zamanda Windows PowerShell ISE önceki sürümü, Windows PowerShell ISE dosyayı açar.</span><span class="sxs-lookup"><span data-stu-id="733fa-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="733fa-237">**Hata ekranı ayrıştırma** ayrıştırma hatalarını kırmızı alt çizgi ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="733fa-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="733fa-238">Belirtilen hata geldiğinizde, araç ipucu metni kodda bulundu sorun görüntüler.</span><span class="sxs-lookup"><span data-stu-id="733fa-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="733fa-239">**Yakınlaştırma** konsol yakınlaştırma yüzdesini '™ s içeriğin (alt sağ köşesinde Windows PowerShell ISE penceresi) yakınlaştırma kaydırıcıyı kullanarak ya da komutu girerek ayarlanabilir **$psise.options.Zoom** Konsol bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="733fa-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="733fa-240">**Zengin Metin Kopyala ve Yapıştır** yazı tipi, boyut ve renk bilgilerini özgün seçimin içinde Windows PowerShell ISE korur Panoya kopyalama.</span><span class="sxs-lookup"><span data-stu-id="733fa-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="733fa-241">**Blok Seçi** basarak veya betik bölmesine fareyi metin seçerken ALT tuşunu basılı tutarak bir metin bloğunu seçebileceğiniz **Alt + üst karakter + ok**.</span><span class="sxs-lookup"><span data-stu-id="733fa-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="733fa-242">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-242">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-243">Ek düzenleme özellikleri daha tutarlı ve güçlü bir düzenleme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="733fa-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="733fa-244">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-244">**What works differently?**</span></span>

<span data-ttu-id="733fa-245">Bu düzenleme iyileştirmeler Windows PowerShell ISE 2. 0 ' mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="733fa-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="733fa-246">Yeni Yardım Görüntüleyici</span><span class="sxs-lookup"><span data-stu-id="733fa-246">New Help viewer window</span></span>
<span data-ttu-id="733fa-247">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-248">Basarsanız **F1** imlecinizi bir cmdlet veya vurgulanmış bir cmdlet parçası sahip olduğunda, bağlama duyarlı Yardım vurgulanan cmdlet'i hakkında yeni Yardım Görüntüleyicisi'ni açar.</span><span class="sxs-lookup"><span data-stu-id="733fa-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="733fa-249">Windows PowerShell hakkında Yardım görüntülemek için şunu yazın **işleçleri** Konsol bölmesinde ve ENTER tuşuna basın **F1**.</span><span class="sxs-lookup"><span data-stu-id="733fa-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="733fa-250">Bu özelliği kullanmadan önce Windows PowerShell Yardım konularını en güncel sürümünü Microsoft Web sitesinden indirin.</span><span class="sxs-lookup"><span data-stu-id="733fa-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="733fa-251">Yardım konuları indirme en basit yöntemi çalıştırmaktır **Update-Help** konsol Windows PowerShell ISE yönetici olarak çalıştırırken bölmesinde cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="733fa-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="733fa-252">Where alter **F1** anahtar yardımını arar.</span><span class="sxs-lookup"><span data-stu-id="733fa-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="733fa-253">İçinde **Araçları**/**seçenekleri** menüsü, **genel ayarları** sekmesinde, altında **diğer ayarlar**, ayarlama veya temizleyin onay kutusu **yerel Yardım içeriği yerine çevrimiçi içerik kullanmak**.</span><span class="sxs-lookup"><span data-stu-id="733fa-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="733fa-254">İşaretlendiğinde, cmdlet modülleri klasöründe bulunan indirilen Yardımı'nda Yardım istemci arar.</span><span class="sxs-lookup"><span data-stu-id="733fa-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="733fa-255">Onay kutusu işaretli değilse, istemci cmdlet Yardım için TechNet kitaplığında arar.</span><span class="sxs-lookup"><span data-stu-id="733fa-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="733fa-256">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-256">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-257">Geçerli cmdlet veya betik ayrılmadan bağlama duyarlı Yardım sorunsuz öğrenme deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="733fa-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="733fa-258">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-258">**What works differently?**</span></span>

<span data-ttu-id="733fa-259">Windows PowerShell ISE önceki sürümlerinde F1'e basarak Yardım dosyasını yerel bilgisayarda açıldı.</span><span class="sxs-lookup"><span data-stu-id="733fa-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="733fa-260">Windows PowerShell ISE 3.0 ve sonraki sürümlerinde, aranabilir ve yapılandırılabilir cmdlet için Yardım içeren bir pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="733fa-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="733fa-261">Bu Yardım deneyimi için Windows PowerShell ISE 3.0 yenidir ve Windows PowerShell 3.0 için güncelleştirilebilir Yardımı yenidir.</span><span class="sxs-lookup"><span data-stu-id="733fa-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="733fa-262">Göster-Command cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="733fa-262">Show-Command cmdlet</span></span>
<span data-ttu-id="733fa-263">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="733fa-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="733fa-264">**Göster komutu** cmdlet oluşturun veya bir cmdlet veya işlevi bir grafik formda doldurarak çalıştırmak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="733fa-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="733fa-265">Form, kullanıcılar Windows PowerShell ile bir grafiksel ortamda iş olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="733fa-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="733fa-266">**Göster komutu** da hızlı bir Windows PowerShell tabanlı GUI oluşturmak için çalıştırıcılara Gelişmiş etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="733fa-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="733fa-267">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="733fa-267">**What value does this change add?**</span></span>

<span data-ttu-id="733fa-268">Kullanarak **Göster komutu** Windows PowerShell komut dosyalarınızı oldukları tanıdık grafik ortamıyla kullanıcılarınızın sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="733fa-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="733fa-269">**Göster komutu** Windows PowerShell öğrenin giriş kullanıcılar da yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="733fa-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="733fa-270">**Neler farklı şekilde çalışır?**</span><span class="sxs-lookup"><span data-stu-id="733fa-270">**What works differently?**</span></span>

<span data-ttu-id="733fa-271">Göster-yeni Windows PowerShell ISE 3.0 komuttur.</span><span class="sxs-lookup"><span data-stu-id="733fa-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="733fa-272">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="733fa-272">See also</span></span>
<span data-ttu-id="733fa-273">Windows PowerShell'de Windows PowerShell ISE kullanma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="733fa-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="733fa-274">Windows PowerShell Tümleşik komut dosyası ortamı keşfetme</span><span class="sxs-lookup"><span data-stu-id="733fa-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="733fa-275">TechNet Wiki'de işe</span><span class="sxs-lookup"><span data-stu-id="733fa-275">ISE on the TechNet Wiki</span></span>](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="733fa-276">Komut Merkezi</span><span class="sxs-lookup"><span data-stu-id="733fa-276">Script Center</span></span>](http://technet.microsoft.com/scriptcenter/default)