---
ms.date: 08/14/2018
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Betik Yazma ve Çalıştırma
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086859"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="88923-103">Windows PowerShell ISE’de Betik Yazma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="88923-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="88923-104">Bu makalede, oluşturma, düzenleme, çalıştırma ve betikler betik bölmesinde Kaydet açıklar.</span><span class="sxs-lookup"><span data-stu-id="88923-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="88923-105">Oluşturma ve betikleri çalıştırın</span><span class="sxs-lookup"><span data-stu-id="88923-105">How to create and run scripts</span></span>

<span data-ttu-id="88923-106">Açın ve Windows PowerShell dosyaları betik bölmesine düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="88923-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="88923-107">Belirli dosya türleri ilgilendiğiniz Windows PowerShell komut dosyaları (.ps1), komut veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) var.</span><span class="sxs-lookup"><span data-stu-id="88923-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="88923-108">Betik bölmesine Düzenleyicisi'nde renkli söz dizimi bu dosya türleridir.</span><span class="sxs-lookup"><span data-stu-id="88923-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="88923-109">Betik bölmesinde açılabilir ortak diğer dosya türleri, yapılandırma dosyalarını (.ps1xml), XML dosyalarını ve metin dosyaları olan.</span><span class="sxs-lookup"><span data-stu-id="88923-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="88923-110">Windows PowerShell yürütme İlkesi betikleri çalıştırabilir ve Windows PowerShell profilleri ve yapılandırma dosyalarını yükleme olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="88923-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="88923-111">Varsayılan yürütme ilkesini kısıtlı, tüm komut dosyalarının çalışmasını engeller ve yükleme profilleri önler.</span><span class="sxs-lookup"><span data-stu-id="88923-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="88923-112">Yürütme İlkesi yüklenmesi ve kullanılması profilleri izin verecek şekilde değiştirmek için bkz [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) ve [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="88923-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="88923-113">Yeni betik dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88923-113">To create a new script file</span></span>

<span data-ttu-id="88923-114">Araç çubuğunda **yeni**, veya **dosya** menüsünü tıklatın **yeni**.</span><span class="sxs-lookup"><span data-stu-id="88923-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="88923-115">Oluşturulan dosyanın yeni bir dosya sekmesinde geçerli bir PowerShell sekmesi altında görünür. Olduğunda birden fazla PowerShell sekmeleri yalnızca görünür olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="88923-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="88923-116">Bir dosya türü betik (.ps1), varsayılan olarak oluşturulur, ancak yeni bir ad ve uzantı ile kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="88923-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="88923-117">Birden çok komut dosyalarını aynı PowerShell sekmede oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="88923-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="88923-118">Varolan bir komut dosyasını açmak için</span><span class="sxs-lookup"><span data-stu-id="88923-118">To open an existing script</span></span>

<span data-ttu-id="88923-119">Araç çubuğunda **açık**, veya **dosya** menüsünü tıklatın **açık**.</span><span class="sxs-lookup"><span data-stu-id="88923-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="88923-120">İçinde **açın** iletişim kutusunda, açmak istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="88923-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="88923-121">Açılan dosyayı yeni bir sekmede görünür.</span><span class="sxs-lookup"><span data-stu-id="88923-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="88923-122">Bir komut dosyası sekmesini kapatmak için</span><span class="sxs-lookup"><span data-stu-id="88923-122">To close a script tab</span></span>

<span data-ttu-id="88923-123">Tıklayın **kapatmak** simgesini (X) Dosya sekmesini kapatın veya istediğiniz seçin **dosya** menüsüne ve ardından **kapatmak**.</span><span class="sxs-lookup"><span data-stu-id="88923-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="88923-124">Dosyanın son kez kaydedildiğinden beri değiştirilmişse kaydetmek veya atmak istenir.</span><span class="sxs-lookup"><span data-stu-id="88923-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="88923-125">Dosya yolu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="88923-125">To display the file path</span></span>

<span data-ttu-id="88923-126">Dosya sekmesinde dosya adının üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="88923-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="88923-127">Komut dosyasının tam yolu, bir araç ipucu olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="88923-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="88923-128">Bir betiği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="88923-128">To run a script</span></span>

<span data-ttu-id="88923-129">Araç çubuğunda **betiğini Çalıştır**, veya **dosya** menüsünde tıklatın **çalıştırma**.</span><span class="sxs-lookup"><span data-stu-id="88923-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="88923-130">Bir bölümü bir komut çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="88923-130">To run a portion of a script</span></span>

1. <span data-ttu-id="88923-131">Betik bölmesinde bir komut dosyasının bir kısmını seçin.</span><span class="sxs-lookup"><span data-stu-id="88923-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="88923-132">Üzerinde **dosya** menüsünü tıklatın **Seçimi Çalıştır**, veya araç çubuğunda **Seçimi Çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="88923-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="88923-133">Çalışan bir komut dosyası durdurmak için</span><span class="sxs-lookup"><span data-stu-id="88923-133">To stop a running script</span></span>

<span data-ttu-id="88923-134">Çalışan bir komut dosyası durdurmak için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="88923-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="88923-135">Tıklayın **durdurma işlemi** araç</span><span class="sxs-lookup"><span data-stu-id="88923-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="88923-136">CTRL + BREAK tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="88923-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="88923-137">Seçin **dosya** menüsüne ve ardından **durdurma işlemi**.</span><span class="sxs-lookup"><span data-stu-id="88923-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="88923-138">Tuşuna basarak **CTRL + C** metindir, bu durumda seçili olan sürece de çalışır **CTRL + C** kopyalama işlevi için seçili metni eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="88923-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="88923-139">Yazma ve düzenleme metin betik bölmesine</span><span class="sxs-lookup"><span data-stu-id="88923-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="88923-140">Kopyalama, kesme, yapıştırın, bulmak ve metin betik bölmesine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="88923-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="88923-141">Ayrıca Al ve az önce gerçekleştirdiğiniz son eylemi yineleyin.</span><span class="sxs-lookup"><span data-stu-id="88923-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="88923-142">Bu eylemler için klavye kısayolları tüm Windows uygulamaları için kullanılan aynı kısayollarıdır.</span><span class="sxs-lookup"><span data-stu-id="88923-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="88923-143">Betik bölmesinde metin girmek için</span><span class="sxs-lookup"><span data-stu-id="88923-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="88923-144">İmleci betik bölmesine bir betik bölmesinde herhangi bir yere tıklayarak veya tıklayarak taşıma **betik bölmesine gidin** içinde **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="88923-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="88923-145">Bir komut dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88923-145">Create a script.</span></span> <span data-ttu-id="88923-146">Söz dizimi renklendirme ve sekme tamamlama, Windows PowerShell ıse'de daha zengin bir düzenleme deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="88923-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="88923-147">Bkz: [betik bölmesi ve konsol bölmesinde sekme tamamlamayı kullanma nasıl](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) metin yardımcı olmak için sekmesinde Tamamlama özelliğini kullanmayla ilgili ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="88923-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="88923-148">Betik bölmesinde metni bulmak için</span><span class="sxs-lookup"><span data-stu-id="88923-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="88923-149">Herhangi bir metni bulmak için basın **CTRL + F** veya **Düzenle** menüsünde tıklayın **betikte Bul**.</span><span class="sxs-lookup"><span data-stu-id="88923-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="88923-150">İmleci sonra metni bulmak için basın **F3** veya **Düzenle** menüsünde tıklatın **betiğinde Sonrakini Bul**.</span><span class="sxs-lookup"><span data-stu-id="88923-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="88923-151">İmleç önce metni bulmak için basın **SHIFT + F3** veya **Düzenle** menüsünde tıklatın **betiğinde Öncekini Bul**.</span><span class="sxs-lookup"><span data-stu-id="88923-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="88923-152">Betik bölmesine metin bulma ve değiştirme için</span><span class="sxs-lookup"><span data-stu-id="88923-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="88923-153">Tuşuna **CTRL + H** veya **Düzenle** menüsünde tıklatın **betikte değiştirin**.</span><span class="sxs-lookup"><span data-stu-id="88923-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="88923-154">İstediğiniz metin bulma ve değiştirme metnini girin tuşuna **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="88923-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="88923-155">Betik bölmesindeki metnin belirli bir satıra Git</span><span class="sxs-lookup"><span data-stu-id="88923-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="88923-156">Betik bölmesinde basın **CTRL + g'tuşlarını** veya **Düzenle** menüsünde tıklatın **satıra Git**.</span><span class="sxs-lookup"><span data-stu-id="88923-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="88923-157">Bir satır numarası girin.</span><span class="sxs-lookup"><span data-stu-id="88923-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="88923-158">Betik bölmesinde metin kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="88923-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="88923-159">Betik bölmesinde kopyalamak istediğiniz metni seçin.</span><span class="sxs-lookup"><span data-stu-id="88923-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="88923-160">Tuşuna **CTRL + C** veya araç çubuğunda **kopyalama** simgesini veya **Düzenle** menüsünde tıklayın **kopyalama**.</span><span class="sxs-lookup"><span data-stu-id="88923-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="88923-161">Betik bölmesinde metni kesmek için</span><span class="sxs-lookup"><span data-stu-id="88923-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="88923-162">Betik bölmesinde kesmek istediğiniz metni seçin.</span><span class="sxs-lookup"><span data-stu-id="88923-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="88923-163">Tuşuna **CTRL + X** veya araç çubuğunda **Kes** simgesini veya **Düzenle** menüsünde tıklayın **Kes**.</span><span class="sxs-lookup"><span data-stu-id="88923-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="88923-164">Betik bölmesine metni yapıştırmak için</span><span class="sxs-lookup"><span data-stu-id="88923-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="88923-165">Tuşuna **CTRL + V** veya araç çubuğunda **Yapıştır** simgesini veya **Düzenle** menüsünde tıklayın **Yapıştır**.</span><span class="sxs-lookup"><span data-stu-id="88923-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="88923-166">Betik bölmesine bir eylemi geri almak için</span><span class="sxs-lookup"><span data-stu-id="88923-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="88923-167">Tuşuna **CTRL + Z** veya araç çubuğunda **geri** simgesini veya **Düzenle** menüsünde tıklayın **geri**.</span><span class="sxs-lookup"><span data-stu-id="88923-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="88923-168">Betik bölmesine bir eylemi yinelemek için</span><span class="sxs-lookup"><span data-stu-id="88923-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="88923-169">Tuşuna **CTRL + Y** veya araç çubuğunda **Yinele** simgesini veya **Düzenle** menüsünde tıklayın **Yinele**.</span><span class="sxs-lookup"><span data-stu-id="88923-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="88923-170">Bir komut dosyasını kaydetme</span><span class="sxs-lookup"><span data-stu-id="88923-170">How to save a script</span></span>

<span data-ttu-id="88923-171">Bunu değiştirilmesinden bu yana kaydedilmemiş bir dosyayı işaretlemek için betik adının yanında bir yıldız işareti görünür.</span><span class="sxs-lookup"><span data-stu-id="88923-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="88923-172">Dosya kaydedildiğinde yıldız işareti kaybolur.</span><span class="sxs-lookup"><span data-stu-id="88923-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="88923-173">Bir betiği kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="88923-173">To save a script</span></span>

<span data-ttu-id="88923-174">Basın **CTRL + S** veya araç çubuğunda **Kaydet** simgesi veya **dosya** menüsünde tıklayın **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="88923-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="88923-175">Kaydet ve bir betik adı</span><span class="sxs-lookup"><span data-stu-id="88923-175">To save and name a script</span></span>

1. <span data-ttu-id="88923-176">Üzerinde **dosya** menüsünde tıklatın **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="88923-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="88923-177">**Kaydet** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="88923-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="88923-178">İçinde **dosya adı** kutusuna, dosya için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="88923-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="88923-179">İçinde **farklı kaydetme türü** kutusunda, bir dosya türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="88923-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="88923-180">Örneğin, **farklı kaydetme türü** kutusunda ' PowerShell betikleri (\*.ps1)'.</span><span class="sxs-lookup"><span data-stu-id="88923-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="88923-181">**Kaydet**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88923-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="88923-182">ASCII kodlaması bir komut dosyası kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="88923-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="88923-183">Varsayılan olarak, Windows PowerShell ISE yeni komut dosyaları (.ps1), komut veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) Unicode (BigEndianUnicode) olarak varsayılan olarak kaydeder. Â için başka bir kodlama, bir komut dosyası kaydetme ASCII (ANSI gibi), kullanın **Kaydet** veya **Farklı Kaydet** yöntemlerde [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="88923-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="88923-184">Aşağıdaki komut, yeni bir betik ASCII kodlaması ile MyScript.ps1 kaydeder.</span><span class="sxs-lookup"><span data-stu-id="88923-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="88923-185">Aşağıdaki komutu, geçerli komut dosyasını bir dosyayla aynı ada sahip, ancak ASCII kodlaması ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="88923-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="88923-186">Aşağıdaki komut, geçerli dosyanın kodlamasını alır.</span><span class="sxs-lookup"><span data-stu-id="88923-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="88923-187">Windows PowerShell ISE aşağıdaki kodlama seçeneklerini destekler: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 ve varsayılan.</span><span class="sxs-lookup"><span data-stu-id="88923-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="88923-188">Varsayılan seçenek değerini sistemine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="88923-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="88923-189">Windows PowerShell ISE Kaydet veya Kaydet kullandığınızda komut dosyaları, kodlama değiştirmez komutları.</span><span class="sxs-lookup"><span data-stu-id="88923-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="88923-190">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="88923-190">See Also</span></span>

- [<span data-ttu-id="88923-191">Windows PowerShell ISE’yi Keşfetme</span><span class="sxs-lookup"><span data-stu-id="88923-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
