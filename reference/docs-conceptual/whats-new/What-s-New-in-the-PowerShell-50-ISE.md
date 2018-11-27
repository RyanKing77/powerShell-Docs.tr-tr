---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: "' Teki yenilikler 50 PowerShell ISE"
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: f05e3f3f95c8ceec6e843b8a1c79e6f092e1b87b
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320593"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="246c1-103">Hangi&#39;yeni Windows PowerShell ıse'de s</span><span class="sxs-lookup"><span data-stu-id="246c1-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="246c1-104">Bu konuda, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) sürümlerinde sunulan yeni ve güncelleştirilmiş özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="246c1-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="246c1-105">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="246c1-105">Feature description</span></span>
<span data-ttu-id="246c1-106">Windows PowerShell ISE yazma, çalıştırma ve betikler ve modüllerle grafik ve sezgisel bir ortamda test olanak tanıyan bir ana bilgisayar uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="246c1-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="246c1-107">Söz dizimi renklendirme gibi önemli özelliklerle sekme tamamlama, görsel hata ayıklama, Unicode uyumluluk ve bağlama duyarlı Yardım zengin bir kodlama deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="246c1-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="246c1-108">Windows PowerShell ISE genel bakış için bkz. [Windows PowerShell Tümleşik komut dosyası ortamı genel bakış](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="246c1-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="246c1-109">Windows PowerShell ıse'de yeni ve değiştirilen işlevsellik</span><span class="sxs-lookup"><span data-stu-id="246c1-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="246c1-110">Aşağıdaki tabloda, bu sürümü Windows PowerShell ISE'de Windows PowerShell için yeni ve değiştirilmiş özellikler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="246c1-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="246c1-111">Özellik/işlevsellik</span><span class="sxs-lookup"><span data-stu-id="246c1-111">Feature/functionality</span></span>|<span data-ttu-id="246c1-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="246c1-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="246c1-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="246c1-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="246c1-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="246c1-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="246c1-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="246c1-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="246c1-116">X</span><span class="sxs-lookup"><span data-stu-id="246c1-116">X</span></span>|<span data-ttu-id="246c1-117">X</span><span class="sxs-lookup"><span data-stu-id="246c1-117">X</span></span>||
|<span data-ttu-id="246c1-118">**[Kod parçacıkları](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="246c1-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="246c1-119">X</span><span class="sxs-lookup"><span data-stu-id="246c1-119">X</span></span>|<span data-ttu-id="246c1-120">X</span><span class="sxs-lookup"><span data-stu-id="246c1-120">X</span></span>||
|<span data-ttu-id="246c1-121">**[Eklenti araçları](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="246c1-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="246c1-122">X</span><span class="sxs-lookup"><span data-stu-id="246c1-122">X</span></span>|<span data-ttu-id="246c1-123">X</span><span class="sxs-lookup"><span data-stu-id="246c1-123">X</span></span>||
|<span data-ttu-id="246c1-124">**[Yeniden başlatma Yöneticisi ve Otomatik Kaydet](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="246c1-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="246c1-125">X</span><span class="sxs-lookup"><span data-stu-id="246c1-125">X</span></span>|<span data-ttu-id="246c1-126">X</span><span class="sxs-lookup"><span data-stu-id="246c1-126">X</span></span>||
|<span data-ttu-id="246c1-127">**[En son kullanılan listesi](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="246c1-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="246c1-128">X</span><span class="sxs-lookup"><span data-stu-id="246c1-128">X</span></span>|<span data-ttu-id="246c1-129">X</span><span class="sxs-lookup"><span data-stu-id="246c1-129">X</span></span>||
|<span data-ttu-id="246c1-130">**[Konsol bölmesinde](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="246c1-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="246c1-131">X</span><span class="sxs-lookup"><span data-stu-id="246c1-131">X</span></span>|<span data-ttu-id="246c1-132">X</span><span class="sxs-lookup"><span data-stu-id="246c1-132">X</span></span>||
|<span data-ttu-id="246c1-133">**[Komut satırı anahtarları](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="246c1-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="246c1-134">X</span><span class="sxs-lookup"><span data-stu-id="246c1-134">X</span></span>|<span data-ttu-id="246c1-135">X</span><span class="sxs-lookup"><span data-stu-id="246c1-135">X</span></span>||
|<span data-ttu-id="246c1-136">**[Yeni Düzenleyici Özellikleri](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="246c1-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="246c1-137">X</span><span class="sxs-lookup"><span data-stu-id="246c1-137">X</span></span>|<span data-ttu-id="246c1-138">X</span><span class="sxs-lookup"><span data-stu-id="246c1-138">X</span></span>||
|<span data-ttu-id="246c1-139">**[Yeni Yardım Görüntüleyici penceresi](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="246c1-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="246c1-140">X</span><span class="sxs-lookup"><span data-stu-id="246c1-140">X</span></span>|<span data-ttu-id="246c1-141">X</span><span class="sxs-lookup"><span data-stu-id="246c1-141">X</span></span>||
|<span data-ttu-id="246c1-142">**[Show-Command cmdlet'i](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="246c1-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="246c1-143">X</span><span class="sxs-lookup"><span data-stu-id="246c1-143">X</span></span>|<span data-ttu-id="246c1-144">X</span><span class="sxs-lookup"><span data-stu-id="246c1-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="246c1-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="246c1-145">IntelliSense</span></span>
<span data-ttu-id="246c1-146">**3.0 ISE'de eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="246c1-147">IntelliSense Windows PowerShell ISE parçası olan bir otomatik tamamlama Yardım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="246c1-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="246c1-148">IntelliSense, siz yazarken, potansiyel olarak cmdlet'leri, parametreleri, parametre değerleri, dosyaları veya klasörleri eşleşen tıklanabilir menü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="246c1-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="246c1-149">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-149">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-150">IntelliSense'nın eklenmesiyle, komut dosyaları oluşturmak için Windows PowerShell ISE kullandığınızda, cmdlet'ler ve söz dizimi bulmak daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="246c1-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="246c1-151">Ayrıca, yeni komut dosyası oluştururken, Windows PowerShell öğrenmek için Windows PowerShell ISE kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="246c1-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="246c1-152">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-152">**What works differently?**</span></span>

<span data-ttu-id="246c1-153">Cmdlet'lerini Windows PowerShell ISE 3.0 veya üzeri yazdığınızda, böylece ve uygun komutları seçmek kaydırılabilir ve tıklatılabilir bir menü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="246c1-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="246c1-154">Kod parçacıkları</span><span class="sxs-lookup"><span data-stu-id="246c1-154">Snippets</span></span>
<span data-ttu-id="246c1-155">**3.0 ISE'de eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="246c1-156">*Kod parçacıkları* Windows PowerShell ISE'de oluşturduğunuz betikler eklemek Windows PowerShell kodu kısa bölümler.</span><span class="sxs-lookup"><span data-stu-id="246c1-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="246c1-157">Windows PowerShell ISE kod parçacıkları varsayılan kümesi ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="246c1-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="246c1-158">Kod parçacıkları kullanarak ekleyebilirsiniz **yeni kod parçacığı** Windows PowerShell ISE'de çalışırken cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="246c1-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="246c1-159">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-159">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-160">Kod parçacıkları kullanarak hızlı bir şekilde birleştirin ve ortamınızı otomatik hale getirmek için betikleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="246c1-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="246c1-161">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-161">**What works differently?**</span></span>

<span data-ttu-id="246c1-162">Windows PowerShell 3.0 veya sonraki kod parçacıkları kullanması için **Düzenle** menüsünde tıklayın **parçacıkları Başlat**, veya basın **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="246c1-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="246c1-163">Eklenti araçları</span><span class="sxs-lookup"><span data-stu-id="246c1-163">Add-on tools</span></span>
<span data-ttu-id="246c1-164">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-165">Windows PowerShell ISE nesne modeli kullanılarak eklenen denetimler Windows Presentation Foundation (WPF) eklenti araçları, artık desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="246c1-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="246c1-166">Eklenti araçları, konsolda bir dikey veya yatay bölme olarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="246c1-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="246c1-167">Sekmeli denetim olarak birden fazla eklenti araçları bölmesinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="246c1-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="246c1-168">Ayrıca, ekleyebilir veya Microsoft dışı taraflarca oluşturulan eklenti araçları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="246c1-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="246c1-169">İçeri aktarma veya eklenti araçları kaldırma hakkında daha fazla bilgi için bkz. [Windows PowerShell ISE işlemleri](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="246c1-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](https://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="246c1-170">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-170">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-171">Eklentiler, genişletme ve Windows PowerShell ISE betik oluşturma deneyiminizi geliştirin veya Windows PowerShell ISE'ye işlevsellik ekleyen araçlarla özelleştirme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="246c1-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="246c1-172">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-172">**What works differently?**</span></span>

<span data-ttu-id="246c1-173">Windows PowerShell ISE 3.0 ve sonraki sürümleri ile birlikte geldiğinden **komutları** eklenti.</span><span class="sxs-lookup"><span data-stu-id="246c1-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="246c1-174">**Komutları** eklenti cmdlet'leri göz atın ve cmdlet'leri yan yana ile ilgili Yardım erişim olanak tanır **betik** ve **konsol** bölmeleri.</span><span class="sxs-lookup"><span data-stu-id="246c1-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="246c1-175">Ek Eklentiler kullanarak bulunabilir **eklenti araçları Web sitesi Aç** komutunu **eklentileri** menüsü.</span><span class="sxs-lookup"><span data-stu-id="246c1-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="246c1-176">Yöneticisi yeniden Otomatik Kaydet</span><span class="sxs-lookup"><span data-stu-id="246c1-176">Restart manager and auto-save</span></span>
<span data-ttu-id="246c1-177">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-178">Windows PowerShell ISE artık otomatik olarak açık betiklerinizi iki dakikada bir, ayrı bir konuma kaydeder.</span><span class="sxs-lookup"><span data-stu-id="246c1-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="246c1-179">Betikleri kaydedilmedi bile Windows PowerShell ISE çalışmayı durduruyor ya da Windows PowerShell ISE yeniden başlatıldıktan sonra işletim sistemini yeniden başlatılırsa bu kurtarır olan betikler son oturumunuzda açın.</span><span class="sxs-lookup"><span data-stu-id="246c1-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="246c1-180">Otomatik kaydetme aralığını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="246c1-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="246c1-181">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-181">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-182">Artık Windows PowerShell ISE açık betiklerinizi beklenmeyen bir yeniden başlatma durumunda otomatik olarak kaydedilir bilerek içinde çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="246c1-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="246c1-183">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-183">**What works differently?**</span></span>

<span data-ttu-id="246c1-184">Windows PowerShell ISE 2.0 komut dosyalarını otomatik olarak yeniden başlatma durumunda kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="246c1-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="246c1-185">En son kullanılan listesi</span><span class="sxs-lookup"><span data-stu-id="246c1-185">Most-recently used list</span></span>
<span data-ttu-id="246c1-186">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-187">Windows PowerShell ISE artık dosyalar için en son kullanılan bir listesi vardır.</span><span class="sxs-lookup"><span data-stu-id="246c1-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="246c1-188">Windows PowerShell ISE'de bir dosyayı açtığınızda, dosyanın en son kullanılan listeye eklendiğini **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="246c1-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="246c1-189">En son kullanılan listede yer alan dosyalar varsayılan sayısını değiştirmek için konsol bölmesinde aşağıdaki komutu çalıştırın: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="246c1-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="246c1-190">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-190">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-191">En Son Kullanılanlar listesi artık kolayca sık kullanılan dosyalarınıza erişmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="246c1-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="246c1-192">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-192">**What works differently?**</span></span>

<span data-ttu-id="246c1-193">Windows PowerShell ISE 2.0 en son kullanılan liste yok.</span><span class="sxs-lookup"><span data-stu-id="246c1-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="246c1-194">Konsol bölmesinde</span><span class="sxs-lookup"><span data-stu-id="246c1-194">Console Pane</span></span>
<span data-ttu-id="246c1-195">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-196">Tek bir konsol bölmesine ayrı komut ve Windows PowerShell ISE ilk sürümde kullanılabilir çıkış bölmeleri birleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="246c1-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="246c1-197">Konsol bölmesinde işlevi ve tipik bir Windows PowerShell Konsolu görünümünü benzer, ancak (çoğu bu konuda açıklandığı gibi) aşağıdaki geliştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="246c1-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="246c1-198">Giriş metin (çıkış metin değil), XML sözdizimi de dahil olmak üzere söz dizimi renklendirmesi</span><span class="sxs-lookup"><span data-stu-id="246c1-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="246c1-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="246c1-199">IntelliSense</span></span>

- <span data-ttu-id="246c1-200">Ayraç eşleştirme</span><span class="sxs-lookup"><span data-stu-id="246c1-200">Brace matching</span></span>

- <span data-ttu-id="246c1-201">Hata göstergesi</span><span class="sxs-lookup"><span data-stu-id="246c1-201">Error indication</span></span>

- <span data-ttu-id="246c1-202">Tam Unicode desteği</span><span class="sxs-lookup"><span data-stu-id="246c1-202">Full Unicode support</span></span>

- <span data-ttu-id="246c1-203">**F1** bağlama duyarlı Yardım</span><span class="sxs-lookup"><span data-stu-id="246c1-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="246c1-204">**CTRL + F1** bağlama duyarlı Göster komutu</span><span class="sxs-lookup"><span data-stu-id="246c1-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="246c1-205">Karmaşık bir betik ve sağdan sola destek</span><span class="sxs-lookup"><span data-stu-id="246c1-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="246c1-206">Yazı tipi desteği</span><span class="sxs-lookup"><span data-stu-id="246c1-206">Font support</span></span>

- <span data-ttu-id="246c1-207">Yakınlaştırma</span><span class="sxs-lookup"><span data-stu-id="246c1-207">Zoom</span></span>

- <span data-ttu-id="246c1-208">Satırı seçin ve blok seçim modları</span><span class="sxs-lookup"><span data-stu-id="246c1-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="246c1-209">Yazılan içerik tuşuna bastığınızda komut satırında korunmasını **yukarı** konsolda geçmişini görüntülemek için oku</span><span class="sxs-lookup"><span data-stu-id="246c1-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="246c1-210">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-210">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-211">Konsol bölmesinde değişikliklerin eklenmesini konsoluna arabirimle daha tutarlı bir kodlama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="246c1-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="246c1-212">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-212">**What works differently?**</span></span>

<span data-ttu-id="246c1-213">Windows PowerShell ISE 2.0 ayrı komut ve çıkış bölmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="246c1-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="246c1-214">Komut satırı anahtarları</span><span class="sxs-lookup"><span data-stu-id="246c1-214">Command-line switches</span></span>
<span data-ttu-id="246c1-215">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-216">Komut satırından Windows PowerShell ISE başlatırsanız (yazarak **powershell_ise.exe**), aşağıdaki yeni komut satırı anahtarları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="246c1-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="246c1-217">*-NoProfile*: Windows PowerShell ISE çalıştırılmadan başlar **$profile**</span><span class="sxs-lookup"><span data-stu-id="246c1-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="246c1-218">*-Help*: Yardım penceresini görüntüler</span><span class="sxs-lookup"><span data-stu-id="246c1-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="246c1-219">*-mta*: Windows PowerShell ISE birden çok iş parçacıklı bölme modunda başlatır.</span><span class="sxs-lookup"><span data-stu-id="246c1-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="246c1-220">Windows PowerShell ISE için varsayılan işlem modu tek iş parçacıklı bölme modunda olduğundan veya *- sta*.</span><span class="sxs-lookup"><span data-stu-id="246c1-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="246c1-221">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-221">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-222">Bu komut satırı anahtarları eklenmesi, Windows PowerShell ISE çalıştığı ortam denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="246c1-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="246c1-223">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-223">**What works differently?**</span></span>

<span data-ttu-id="246c1-224">Windows PowerShell ISE 2.0, bu komut satırı anahtarları kabul etmiyor.</span><span class="sxs-lookup"><span data-stu-id="246c1-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="246c1-225">Yeni Düzenleyici Özellikleri</span><span class="sxs-lookup"><span data-stu-id="246c1-225">New editor features</span></span>
<span data-ttu-id="246c1-226">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-227">Diğer Windows PowerShell ISE düzenleme özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="246c1-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="246c1-228">**XML sözdizimi renklendirme**Windows PowerShell ISE'de artık renkleri XML sözdizimini aynı şekilde Windows PowerShell söz dizimi renkleri gibi.</span><span class="sxs-lookup"><span data-stu-id="246c1-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="246c1-229">**Ayraç eşleştirme** Windows PowerShell ISE vurgulama ve Ayraç eşleştirme içerir ve aşağıdaki şekillerde kullanılabilir: (örneğin, kullanarak **eşleşmeye Git** komutu veya **Ctrl +]** bulur Seçili bir açılış ayracı varsa, kapanış ayracı).</span><span class="sxs-lookup"><span data-stu-id="246c1-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="246c1-230">**Anahat görünümü** betik bölmesine destekler anahat oluşturma, artı veya eksi tıklayarak kod bölümlerini genişletme veya daraltma imzalar sol kenar boşluğunda izin verir.</span><span class="sxs-lookup"><span data-stu-id="246c1-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="246c1-231">Küme ayraçları kullanabilirsiniz veya **#region** ve **#endregion** başlangıcında veya daraltılabilir bir bölüm sonu işaretlemek için etiketleri.</span><span class="sxs-lookup"><span data-stu-id="246c1-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="246c1-232">Genişlet veya daralt tüm bölgeler için basın **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="246c1-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="246c1-233">**Sürükle ve bırak metin düzenlemesini**sürükle ve bırak metin düzenlemesini artık Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="246c1-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="246c1-234">Herhangi bir metin bloğu seçin ve bu metin düzenleyicisi veya konsol metni taşımak için başka bir konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="246c1-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="246c1-235">Fare düğmesini bıraktığınızda, seçili metni sürüklerken Ctrl tuşunu basılı tutun, metin yeni konuma kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="246c1-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="246c1-236">Windows PowerShell ISE'yi .iso dosyalarını sürükleyip Windows PowerShell ISE bu sürümü, aynı zamanda Windows PowerShell ISE önceki sürümünü, Windows PowerShell ISE dosyayı açar.</span><span class="sxs-lookup"><span data-stu-id="246c1-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="246c1-237">**Hata ekranı ayrıştırma** ayrıştırma hataları kırmızı alt çizgi ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="246c1-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="246c1-238">Belirtilen bir hata geldiğinizde, araç ipucu metni, kod içinde bulunan sorun görüntüler.</span><span class="sxs-lookup"><span data-stu-id="246c1-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="246c1-239">**Yakınlaştırma** konsol yakınlaştırma yüzdesi '™ s içerik yakınlaştırma kaydırıcısı (alt sağ köşesinde Windows PowerShell ISE penceresi) kullanarak veya komutu girerek ayarlanabilir **$psise.options.Zoom** Konsol bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="246c1-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="246c1-240">**Zengin Metin Kopyala ve Yapıştır** yazı tipi, boyut ve renk bilgilerini özgün seçimin içinde Windows PowerShell ISE korur Panoya kopyalama.</span><span class="sxs-lookup"><span data-stu-id="246c1-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="246c1-241">**Blok seçimi** betik bölmesine farenizi metin seçim sırasında ALT tuşunu basılı tutarak veya tuşuna basarak metin bloğu seçin **Alt + SHIFT + ok**.</span><span class="sxs-lookup"><span data-stu-id="246c1-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="246c1-242">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-242">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-243">Ek düzenleme özellikleri, daha tutarlı ve güçlü bir düzenleme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="246c1-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="246c1-244">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-244">**What works differently?**</span></span>

<span data-ttu-id="246c1-245">Bu düzenleme geliştirmeleri, Windows PowerShell ISE 2.0 sürümünde bulunmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="246c1-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="246c1-246">Yeni Yardım Görüntüleyici penceresi</span><span class="sxs-lookup"><span data-stu-id="246c1-246">New Help viewer window</span></span>
<span data-ttu-id="246c1-247">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-248">Basarsanız **F1** imlecinizi bir cmdlet'tir veya vurgulanmış bir cmdlet bir parçası olan, bağlama duyarlı Yardım vurgulanan cmdlet'i hakkında yeni Yardım Görüntüleyicisi'ni açar.</span><span class="sxs-lookup"><span data-stu-id="246c1-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="246c1-249">Windows PowerShell hakkında Yardım görüntülemek üzere şunu yazın **işleçleri** ENTER tuşuna basın ve konsol bölmesinde **F1**.</span><span class="sxs-lookup"><span data-stu-id="246c1-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="246c1-250">Bu özelliği kullanmadan önce Windows PowerShell Yardım konularını en güncel sürümü Microsoft Web sitesinden indirin.</span><span class="sxs-lookup"><span data-stu-id="246c1-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="246c1-251">Yardım konuları karşıdan yüklemek için en basit yöntem çalıştırmaktır **Update-Help** cmdlet'ini yönetici olarak Windows PowerShell ISE çalışırken Konsol bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="246c1-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="246c1-252">Where değiştirebilirsiniz **F1** anahtar Yardım için arar.</span><span class="sxs-lookup"><span data-stu-id="246c1-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="246c1-253">İçinde **Araçları**/**seçenekleri** menü, **genel ayarlar** sekmesindeki **diğer ayarlar**, ayarlama veya Temizle onay kutusu **yerel Yardım içeriğini kullanmak yerine çevrimiçi içerik**.</span><span class="sxs-lookup"><span data-stu-id="246c1-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="246c1-254">Eğer işaretliyse, cmdlet modülleri klasöründe bulunan indirilen Yardımı'nda Yardım istemci arar.</span><span class="sxs-lookup"><span data-stu-id="246c1-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="246c1-255">Onay kutusu işaretli değilse, istemci için cmdlet yardımına TechNet kitaplığında arar.</span><span class="sxs-lookup"><span data-stu-id="246c1-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="246c1-256">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-256">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-257">Geçerli bir cmdlet veya betik çıkmadan bağlama duyarlı Yardım sorunsuz öğrenme deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="246c1-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="246c1-258">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-258">**What works differently?**</span></span>

<span data-ttu-id="246c1-259">Windows PowerShell ISE önceki sürümlerinde F1 tuşuna bastığınızda, Yardım dosyasını yerel bilgisayarda açıldı.</span><span class="sxs-lookup"><span data-stu-id="246c1-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="246c1-260">Windows PowerShell ISE 3.0 ve sonraki sürümlerinde, aranabilir ve yapılandırılabilir bir cmdlet için Yardım içeren bir pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="246c1-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="246c1-261">Bu Yardım deneyimi için Windows PowerShell ISE 3.0 yenidir ve Windows PowerShell 3.0 için güncelleştirilebilir Yardımı yenidir.</span><span class="sxs-lookup"><span data-stu-id="246c1-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="246c1-262">Show-Command cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="246c1-262">Show-Command cmdlet</span></span>
<span data-ttu-id="246c1-263">**PowerShell 3.0 eklendi**</span><span class="sxs-lookup"><span data-stu-id="246c1-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="246c1-264">**Show komutunu** cmdlet'i oluşturun veya bir grafik biçiminde doldurarak bir cmdlet veya işlev çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="246c1-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="246c1-265">Formu Windows PowerShell ile bir grafiksel ortamda çalışma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="246c1-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="246c1-266">**Show komutunu** ayrıca çalıştırıcılara hızlı bir Windows PowerShell tabanlı GUI oluşturmak için Gelişmiş etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="246c1-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="246c1-267">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="246c1-267">**What value does this change add?**</span></span>

<span data-ttu-id="246c1-268">Kullanarak **Show komutunu** , Windows PowerShell betiklerini, kullanıcılarınızın olduğu tanıdık grafik ortamıyla sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="246c1-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="246c1-269">**Show komutunu** Windows PowerShell tanıtım kullanıcıların da yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="246c1-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="246c1-270">**Farklı işleyen nedir?**</span><span class="sxs-lookup"><span data-stu-id="246c1-270">**What works differently?**</span></span>

<span data-ttu-id="246c1-271">Show-yeni Windows PowerShell ISE 3.0 komutudur.</span><span class="sxs-lookup"><span data-stu-id="246c1-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="246c1-272">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="246c1-272">See also</span></span>
<span data-ttu-id="246c1-273">Windows PowerShell'de Windows PowerShell ISE'yi kullanma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="246c1-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="246c1-274">Windows PowerShell Tümleşik komut dosyası ortamı keşfetme</span><span class="sxs-lookup"><span data-stu-id="246c1-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="246c1-275">ISE TechNet Wiki</span><span class="sxs-lookup"><span data-stu-id="246c1-275">ISE on the TechNet Wiki</span></span>](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="246c1-276">Betik Merkezi</span><span class="sxs-lookup"><span data-stu-id="246c1-276">Script Center</span></span>](https://technet.microsoft.com/scriptcenter/default)