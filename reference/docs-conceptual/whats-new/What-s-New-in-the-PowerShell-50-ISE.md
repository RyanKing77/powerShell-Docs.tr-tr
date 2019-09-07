---
ms.date: 09/06/2019
keywords: PowerShell, cmdlet
title: PowerShell 5,0 ıSE 'deki yenilikler
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746214"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="68352-103">Windows PowerShell 5,0 ıSE 'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="68352-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="68352-104">Bu konuda, Windows PowerShell Tümleşik komut dosyası ortamı (ıSE) sürümlerinde sunulan yeni ve güncelleştirilmiş özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68352-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="68352-105">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="68352-105">Feature description</span></span>

<span data-ttu-id="68352-106">Windows PowerShell ISE, bir grafik ve sezgisel bir ortamda betikleri ve modülleri yazmanızı, çalıştırmanızı ve test etmenizi sağlayan bir konak uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="68352-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="68352-107">Sözdizimi renklendirme, sekme tamamlama, görsel hata ayıklama, Unicode uyumluluğu ve bağlama duyarlı yardım gibi önemli özellikler, zengin bir betik deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="68352-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="68352-108">Daha fazla bilgi için bkz. [Windows PowerShell ISE tanıtımı](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="68352-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="68352-109">Aşağıdaki tabloda, Windows PowerShell 'de Windows PowerShell ISE bu sürümü için yeni ve değiştirilmiş özellikler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="68352-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="68352-110">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="68352-110">IntelliSense</span></span>

> <span data-ttu-id="68352-111">ISE 3,0 eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-111">Added in ISE 3.0</span></span>

<span data-ttu-id="68352-112">IntelliSense, Windows PowerShell ISE parçası olan bir otomatik tamamlama yardım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="68352-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="68352-113">IntelliSense, siz yazarken eşleşen cmdlet 'ler, parametreler, parametre değerleri, dosyalar veya klasörler için tıklatılabilir menüler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="68352-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="68352-114">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-114">**What value does this change add?**</span></span>

<span data-ttu-id="68352-115">IntelliSense 'in eklenmesiyle, betikleri oluşturmak için Windows PowerShell ISE kullandığınızda cmdlet 'leri ve sözdizimini bulmayı daha kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="68352-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="68352-116">Yeni betikler oluştururken Windows PowerShell 'i öğrenmek için Windows PowerShell ISE de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="68352-117">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-117">**What works differently?**</span></span>

<span data-ttu-id="68352-118">Windows PowerShell ISE cmdlet 'leri yazdığınızda, kaydırılabilir ve tıklatılabilir bir menü görüntülenir ve ilgili komutlara gözatmanıza ve bunları seçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68352-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="68352-119">Kod parçacıkları</span><span class="sxs-lookup"><span data-stu-id="68352-119">Snippets</span></span>

> <span data-ttu-id="68352-120">ISE 3,0 eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-120">Added in ISE 3.0</span></span>

<span data-ttu-id="68352-121">Kod *parçacıkları* , Windows PowerShell ISE içinde oluşturduğunuz betiklere ekleyebileceğiniz Windows PowerShell kodunun kısa bölümleridir.</span><span class="sxs-lookup"><span data-stu-id="68352-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="68352-122">Windows PowerShell ISE, varsayılan bir parçacık kümesiyle gelir.</span><span class="sxs-lookup"><span data-stu-id="68352-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="68352-123">Windows PowerShell ISE çalışırken `New-Snippet` cmdlet 'ini kullanarak kod parçacığı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="68352-124">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-124">**What value does this change add?**</span></span>

<span data-ttu-id="68352-125">Kod parçacıklarını kullanarak ortamınızı otomatik hale getirmek için hızlı bir şekilde komut dosyaları oluşturabilir ve oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="68352-126">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-126">**What works differently?**</span></span>

<span data-ttu-id="68352-127">Windows PowerShell 3,0 veya sonrasında kod parçacıklarını kullanmak için, **Düzenle** menüsünde, **parçacıkları Başlat**' a tıklayın veya <kbd>CTRL</kbd>+<kbd>J</kbd>' ye basın.</span><span class="sxs-lookup"><span data-stu-id="68352-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="68352-128">Eklenti araçları</span><span class="sxs-lookup"><span data-stu-id="68352-128">Add-on tools</span></span>

> <span data-ttu-id="68352-129">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-130">Windows PowerShell ISE artık nesne modelini kullanan eklenti araçlarını desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="68352-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="68352-131">Bu eklentiler, konsolunda dikey veya yatay bölme olarak görüntülenen Windows Presentation Foundation (WPF) denetimleridir.</span><span class="sxs-lookup"><span data-stu-id="68352-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="68352-132">Bölmedeki çoklu eklenti araçları sekmeli Denetim olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="68352-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="68352-133">Ayrıca, Microsoft dışı taraflar tarafından üretilen eklenti araçları ekleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="68352-134">Daha fazla bilgi için [Windows PowerShell ISE betik nesnesi modelinin amacını](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="68352-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="68352-135">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-135">**What value does this change add?**</span></span>

<span data-ttu-id="68352-136">Eklentiler, işlevselliği ekleyen ve betik deneyiminizi geliştiren araçlarla Windows PowerShell ISE genişletmenize ve özelleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="68352-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="68352-137">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-137">**What works differently?**</span></span>

<span data-ttu-id="68352-138">Windows PowerShell ISE 3,0 ve üzeri, **Komutlar** eklentisi ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="68352-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="68352-139">**Komutlar** eklentisi, cmdlet 'lere gözatmanıza ve cmdlet 'Ler hakkında **komut dosyası** ve **konsol** bölmeleri ile yan yana erişim sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="68352-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="68352-140">Ek **Eklentiler, eklentiler menüsündeki** **eklenti araçları Web sitesini aç** komutu kullanılarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="68352-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="68352-141">Yeniden başlatma Yöneticisi ve otomatik kaydetme</span><span class="sxs-lookup"><span data-stu-id="68352-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="68352-142">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-143">Windows PowerShell ISE artık açık betiklerinizi her iki dakikada bir otomatik olarak ayrı bir konuma kaydeder.</span><span class="sxs-lookup"><span data-stu-id="68352-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="68352-144">Beklenmeyen kilitlenme veya yeniden başlatma işleminden sonra Windows PowerShell ISE yeniden başlatıldığında, betikler kaydedilmese bile son oturumda açık olan betikleri kurtarır.</span><span class="sxs-lookup"><span data-stu-id="68352-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="68352-145">Otomatik kaydetme aralığını değiştirmek için Konsol bölmesinde aşağıdaki komutu çalıştırın: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="68352-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="68352-146">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-146">**What value does this change add?**</span></span>

<span data-ttu-id="68352-147">Artık açık betiklerinizin otomatik olarak kaydedildiğini bilmenin Windows PowerShell ISE içinde çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="68352-148">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-148">**What works differently?**</span></span>

<span data-ttu-id="68352-149">Windows PowerShell ISE 2,0, betikleri otomatik olarak kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="68352-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="68352-150">En son kullanılan liste</span><span class="sxs-lookup"><span data-stu-id="68352-150">Most-recently used list</span></span>

> <span data-ttu-id="68352-151">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-152">Artık Windows PowerShell ISE dosyalar için en son kullanılanlar listesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="68352-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="68352-153">Windows PowerShell ISE **bir dosyayı açtığınızda Dosya menüsündeki en** Son Kullanılanlar listesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="68352-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="68352-154">En son kullanılan listedeki varsayılan dosya sayısını değiştirmek için Konsol bölmesinde aşağıdaki komutu çalıştırın: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="68352-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="68352-155">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-155">**What value does this change add?**</span></span>

<span data-ttu-id="68352-156">Artık sık kullanılan dosyalarınıza kolayca erişmek için en son kullanılan listesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="68352-157">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-157">**What works differently?**</span></span>

<span data-ttu-id="68352-158">Windows PowerShell ISE 2,0 en son kullanılanlar listesine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="68352-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="68352-159">Konsol bölmesi</span><span class="sxs-lookup"><span data-stu-id="68352-159">Console Pane</span></span>

> <span data-ttu-id="68352-160">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-161">İlk Windows PowerShell ISE sürümünde kullanılabilir olan ayrı komut ve çıkış bölmeleri tek bir Konsol bölmesinde birleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="68352-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="68352-162">Konsol bölmesi, tipik bir Windows PowerShell konsoluna işlev ve görünüm ile benzerdir, ancak aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="68352-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="68352-163">XML sözdizimi dahil olmak üzere giriş metni için sözdizimi renklendirme (çıkış metni değil)</span><span class="sxs-lookup"><span data-stu-id="68352-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="68352-164">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="68352-164">IntelliSense</span></span>
- <span data-ttu-id="68352-165">Ayraç eşleştirme</span><span class="sxs-lookup"><span data-stu-id="68352-165">Brace matching</span></span>
- <span data-ttu-id="68352-166">Hata göstergesi</span><span class="sxs-lookup"><span data-stu-id="68352-166">Error indication</span></span>
- <span data-ttu-id="68352-167">Tam Unicode desteği</span><span class="sxs-lookup"><span data-stu-id="68352-167">Full Unicode support</span></span>
- <span data-ttu-id="68352-168"><kbd>F1</kbd> bağlama duyarlı yardım</span><span class="sxs-lookup"><span data-stu-id="68352-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="68352-169"><kbd></kbd>CTRL+<kbd>F1</kbd> bağlama duyarlı göster-komut</span><span class="sxs-lookup"><span data-stu-id="68352-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="68352-170">Karmaşık betik ve sağdan sola destek</span><span class="sxs-lookup"><span data-stu-id="68352-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="68352-171">Yazı tipi desteği</span><span class="sxs-lookup"><span data-stu-id="68352-171">Font support</span></span>
- <span data-ttu-id="68352-172">Yakınlaştır</span><span class="sxs-lookup"><span data-stu-id="68352-172">Zoom</span></span>
- <span data-ttu-id="68352-173">Satır seçme ve blok seçme modları</span><span class="sxs-lookup"><span data-stu-id="68352-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="68352-174">Konsolunda geçmişi görüntülemek için <kbd>yukarı oka</kbd> bastığınızda komut satırında yazılan içeriğin korunması</span><span class="sxs-lookup"><span data-stu-id="68352-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="68352-175">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-175">**What value does this change add?**</span></span>

<span data-ttu-id="68352-176">Bu konsol bölmesi değişikliklerinin eklenmesi konsol arabirimiyle daha tutarlı bir betik deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="68352-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="68352-177">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-177">**What works differently?**</span></span>

<span data-ttu-id="68352-178">Windows PowerShell ISE 2,0 ayrı komut ve çıkış bölmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="68352-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="68352-179">Komut satırı anahtarları</span><span class="sxs-lookup"><span data-stu-id="68352-179">Command-line switches</span></span>

> <span data-ttu-id="68352-180">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-181">Komut satırından Windows PowerShell ISE başlatırsanız ( **powershell_ise. exe**yazarak) aşağıdaki yeni komut satırı anahtarlarını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="68352-182">`-NoProfile`: Çalıştırmadan Windows PowerShell ISE başlatır`$profile`</span><span class="sxs-lookup"><span data-stu-id="68352-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="68352-183">`-Help`: Yardım penceresini görüntüler</span><span class="sxs-lookup"><span data-stu-id="68352-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="68352-184">`-mta`: Windows PowerShell ISE çoklu iş parçacıklı grup modunda başlatır.</span><span class="sxs-lookup"><span data-stu-id="68352-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="68352-185">Windows PowerShell ISE için varsayılan işlem modu tek iş parçacıklı grup modu veya `-sta`' dir.</span><span class="sxs-lookup"><span data-stu-id="68352-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="68352-186">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-186">**What value does this change add?**</span></span>

<span data-ttu-id="68352-187">Bu komut satırı anahtarlarının eklenmesi, Windows PowerShell ISE çalıştığı ortamı denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="68352-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="68352-188">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-188">**What works differently?**</span></span>

<span data-ttu-id="68352-189">Windows PowerShell ISE 2,0, bu komut satırı anahtarlarını tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="68352-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="68352-190">Yeni Düzenleyici özellikleri</span><span class="sxs-lookup"><span data-stu-id="68352-190">New editor features</span></span>

> <span data-ttu-id="68352-191">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-192">Diğer Windows PowerShell ISE düzenlemekte özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="68352-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="68352-193">**XML sözdizimi renklendirme** -Windows PowerShell ISE artık renkler XML söz dizimini BT renkleriyle Windows PowerShell söz dizimi ile aynı şekilde.</span><span class="sxs-lookup"><span data-stu-id="68352-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="68352-194">**Ayraç eşleştirme** -Windows PowerShell ISE parantez ile eşleşen ve vurgulamaya sahiptir ve aşağıdaki yollarla kullanılabilir: (örneğin, **eşleşme komutuna git** komutu veya <kbd>CTRL</kbd>+<kbd>]</kbd> , varsa, kapatma küme ayracını bulur) bir açma ayracı seçili olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="68352-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="68352-195">**Ana hat görünümü** Betik bölmesi ana hattı destekler, böylece sol kenar boşluğunda artı veya eksi işareti tıklatılarak kod bölümlerinin daralmasına veya genişletildiğine izin verir.</span><span class="sxs-lookup"><span data-stu-id="68352-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="68352-196">Daraltılabilir bir bölümün başlangıcını veya sonunu `#region` işaretlemek `#endregion` için küme ayracı veya ve etiketlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="68352-197">Tüm bölgeleri genişletmek veya daraltmak için <kbd>CTRL</kbd>+tuşuna<kbd>basın.</kbd></span><span class="sxs-lookup"><span data-stu-id="68352-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="68352-198">**Sürükle ve bırak metin düzenlemesi** -Windows PowerShell ISE artık sürükle ve bırak metin düzenlemesini destekliyor.</span><span class="sxs-lookup"><span data-stu-id="68352-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="68352-199">Herhangi bir metin bloğunu seçebilir ve metni, düzenleyicide veya konsolda bulunan başka bir konuma sürükleyerek metnin taşınmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="68352-200">Seçili metni sürüklerken <kbd>CTRL</kbd> tuşunu basılı tutarsanız, fare düğmesini serbest bırakırsanız metin yeni konuma kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="68352-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="68352-201">Bu Windows PowerShell ISE sürümünde, dosyaları Windows PowerShell ISE sürükleyip bıraktığınızda Windows PowerShell ISE dosyayı açar.</span><span class="sxs-lookup"><span data-stu-id="68352-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="68352-202">**Ayrıştırma hatası görüntüleme** -Ayrıştırma hataları kırmızı alt çizgilerle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="68352-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="68352-203">Belirtilen bir hatanın üzerine geldiğinizde, araç ipucu metni kodda bulunan sorunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="68352-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="68352-204">**Yakınlaştır** -konsol içeriğinin yakınlaştırma yüzdesi, Yakınlaştırma kaydırıcısı (Windows PowerShell ISE penceresinin sağ alt köşesinde) veya komut `$psise.options.Zoom` konsol bölmesine girilerek ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="68352-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="68352-205">**Zengin metin kopyalama ve yapıştırma** -Windows PowerShell ISE Pano 'ya kopyalama, özgün seçimin yazı tipi, boyut ve renk bilgilerini korur.</span><span class="sxs-lookup"><span data-stu-id="68352-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="68352-206">**Seçimi engelle** - <kbd>alt</kbd> tuşunu basılı tutarak, farenizle betik bölmesinde metin seçerken veya <kbd>alt</kbd>+<kbd>kaydırma</kbd>+<kbd>okuna</kbd>basarak bir metin bloğunu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="68352-207">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-207">**What value does this change add?**</span></span>

<span data-ttu-id="68352-208">Ek Düzenle özellikleri, daha tutarlı ve güçlü bir düzen ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="68352-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="68352-209">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-209">**What works differently?**</span></span>

<span data-ttu-id="68352-210">Bu düzen geliştirmeleri Windows PowerShell ISE 2,0 ' de yoktu.</span><span class="sxs-lookup"><span data-stu-id="68352-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="68352-211">Yeni Yardım Görüntüleyici penceresi</span><span class="sxs-lookup"><span data-stu-id="68352-211">New Help viewer window</span></span>

> <span data-ttu-id="68352-212">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-213">İmlecinizin bir cmdlet 'deyken <kbd>F1</kbd> tuşuna basarsanız veya bir cmdlet 'in bir parçası vurgulandığında, yeni Yardım Görüntüleyicisi vurgulanan cmdlet hakkında bağlama duyarlı yardım açar.</span><span class="sxs-lookup"><span data-stu-id="68352-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="68352-214">Yardım **hakkında** Windows PowerShell 'i göstermek için konsol `operators` bölmesine yazın ve <kbd>F1</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="68352-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="68352-215">Bu özelliği kullanmadan önce, Microsoft Web sitesindeki Windows PowerShell yardım konuları 'nın en güncel sürümünü indirin.</span><span class="sxs-lookup"><span data-stu-id="68352-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="68352-216">Yardım konularını indirmek için en basit yöntem, Windows PowerShell ISE yönetici olarak çalıştırırken `Update-Help` , cmdlet 'ini Konsol bölmesinde çalıştırkullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="68352-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="68352-217"><kbd>F1</kbd> tuşunun yardım için nerede göründüğünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="68352-218">**Araçlar**/Seçenekler menüsünde, **Genel ayarlar** sekmesinde, **diğer ayarlar**' ın altında, **çevrimiçi içerik yerine yerel yardım içeriğini kullan**onay kutusunu ayarlayabilir veya temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="68352-219">İşaretlendiğinde, istemci, modüller klasöründe bulunan indirilen yardım 'da cmdlet yardımına bakar.</span><span class="sxs-lookup"><span data-stu-id="68352-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="68352-220">Onay kutusu silinirse, istemci yardım çevrimiçi olarak arar.</span><span class="sxs-lookup"><span data-stu-id="68352-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="68352-221">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-221">**What value does this change add?**</span></span>

<span data-ttu-id="68352-222">Geçerli cmdlet 'inizden veya betikten çıkmadan bağlama duyarlı yardım tümleşik bir öğrenme deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="68352-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="68352-223">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-223">**What works differently?**</span></span>

<span data-ttu-id="68352-224">Önceki Windows PowerShell ISE <kbd>F1</kbd> tuşlarına basmak, yerel bilgisayardaki yardım dosyasını açtı.</span><span class="sxs-lookup"><span data-stu-id="68352-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="68352-225">Windows PowerShell ISE 3,0 ve üzeri sürümlerde, aranabilir ve yapılandırılabilir cmdlet 'inin yardımını içeren bir pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="68352-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="68352-226">Bu yardım deneyimi Windows PowerShell ISE 3,0 ' de yenidir ve Windows PowerShell 3,0 için güncelleştirilebilir yardım yenidir.</span><span class="sxs-lookup"><span data-stu-id="68352-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="68352-227">Show-Command cmdlet 'i</span><span class="sxs-lookup"><span data-stu-id="68352-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="68352-228">PowerShell 3,0 ' ye eklendi</span><span class="sxs-lookup"><span data-stu-id="68352-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="68352-229">`Show-Command` Cmdlet 'i bir grafik formu doldurarak bir cmdlet veya işlev oluşturabilir veya çalıştırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68352-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="68352-230">Form, kullanıcıların bir grafik ortamında Windows PowerShell ile çalışmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="68352-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="68352-231">`Show-Command`Ayrıca Gelişmiş betikler 'in hızlı Windows PowerShell tabanlı GUI oluşturmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68352-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="68352-232">**Bu değişiklik hangi değeri ekler?**</span><span class="sxs-lookup"><span data-stu-id="68352-232">**What value does this change add?**</span></span>

<span data-ttu-id="68352-233">Windows PowerShell `Show-Command` betiklerinizde kullanarak kullanıcılarınıza tanıdık oldukları grafiksel bir ortam sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68352-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="68352-234">`Show-Command`Ayrıca, giriş kullanıcılarına Windows PowerShell 'i Öğrende yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="68352-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="68352-235">**Ne farklı çalışır?**</span><span class="sxs-lookup"><span data-stu-id="68352-235">**What works differently?**</span></span>

<span data-ttu-id="68352-236">`Show-Command`Yeni Windows PowerShell ISE 3,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="68352-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="68352-237">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68352-237">See also</span></span>

<span data-ttu-id="68352-238">Windows PowerShell ISE kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell Tümleşik komut dosyası ortamını keşfetme](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="68352-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span></span>
