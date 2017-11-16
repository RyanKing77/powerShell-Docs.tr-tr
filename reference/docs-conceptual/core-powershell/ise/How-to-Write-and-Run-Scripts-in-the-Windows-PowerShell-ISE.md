---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Yazma ve komut dosyaları içinde Windows PowerShell ISE çalıştırma"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: dd3055df8c84195f0145b1a058f1d17c9c382f33
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="382dd-103">Yazma ve komut dosyaları içinde Windows PowerShell ISE çalıştırma</span><span class="sxs-lookup"><span data-stu-id="382dd-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>
<span data-ttu-id="382dd-104">Bu konu, oluşturmak, düzenlemek, çalıştırmak ve komut dosyaları betik bölmesinde Kaydet açıklar.</span><span class="sxs-lookup"><span data-stu-id="382dd-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="382dd-105">Oluşturma ve komut dosyalarını çalıştır</span><span class="sxs-lookup"><span data-stu-id="382dd-105">How to create and run scripts</span></span>
<span data-ttu-id="382dd-106">Açın ve Windows PowerShell betik bölmesine dosyalarında düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="382dd-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="382dd-107">Belirli dosya ilgilendiğiniz Windows PowerShell komut dosyaları (.ps1), komut dosyası veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) türleridir.</span><span class="sxs-lookup"><span data-stu-id="382dd-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="382dd-108">Betik bölmesine Düzenleyicisi'nde renkli sözdizimi bu dosya türleridir.</span><span class="sxs-lookup"><span data-stu-id="382dd-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="382dd-109">Betik bölmesinde açılabilir diğer ortak dosya yapılandırma dosyalarını (.ps1xml), XML dosyalarını ve metin dosyaları türleridir.</span><span class="sxs-lookup"><span data-stu-id="382dd-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="382dd-110">Windows PowerShell yürütme ilkesini betik çalıştıran ve Windows PowerShell profilleri ve yapılandırma dosyalarını yükleme olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="382dd-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="382dd-111">Varsayılan yürütme ilkesini kısıtlı, tüm komut dosyalarının çalışmasını engeller ve yükleme profilleri engeller.</span><span class="sxs-lookup"><span data-stu-id="382dd-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="382dd-112">Yürütme İlkesi yüklenmesi ve kullanılması profilleri izin verecek şekilde değiştirmek için bkz: [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) ve [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="382dd-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="382dd-113">Yeni bir komut dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-113">To create a new script file</span></span>
<span data-ttu-id="382dd-114">Araç çubuğunda tıklatın **yeni** , veya **dosya** menüsünde tıklatın **yeni**.</span><span class="sxs-lookup"><span data-stu-id="382dd-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="382dd-115">Yeni bir dosya sekmesinde geçerli PowerShell sekmesi altında oluşturulan dosya görüntülenir. Olduğunda birden fazla PowerShell sekmeleri yalnızca görünür olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="382dd-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="382dd-116">Varsayılan olarak bir dosya türü betiği (.ps1) oluşturuldu, ancak yeni adı ve uzantısı ile kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="382dd-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="382dd-117">Birden çok komut dosyaları aynı PowerShell sekmesindeki oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="382dd-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="382dd-118">Varolan bir komut dosyasını açmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-118">To open an existing script</span></span>
<span data-ttu-id="382dd-119">Araç çubuğunda tıklatın **açık**, veya **dosya** menüsünde tıklatın **açık**.</span><span class="sxs-lookup"><span data-stu-id="382dd-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="382dd-120">İçinde **açmak** iletişim kutusunda, açmak istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="382dd-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="382dd-121">Açılan dosyayı yeni bir sekmede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="382dd-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="382dd-122">Bir komut dosyası sekmesini kapatmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-122">To close a script tab</span></span>
<span data-ttu-id="382dd-123">Kapatmak istediğiniz komut dosyası komut dosyası sekmesini tıklatın, ardından aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="382dd-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="382dd-124">Tıklatın **Kapat** betik sekmesindeki simgesini (X).</span><span class="sxs-lookup"><span data-stu-id="382dd-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="382dd-125">Üzerinde **dosya** menüsünde tıklatın **Kapat**.</span><span class="sxs-lookup"><span data-stu-id="382dd-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="382dd-126">Dosyanın son kaydedilişinden değiştirildiyse kaydedin veya atmak istenir.</span><span class="sxs-lookup"><span data-stu-id="382dd-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="382dd-127">Dosya yolu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="382dd-127">To display the file path</span></span>
<span data-ttu-id="382dd-128">Dosya sekmesinde dosya adının üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="382dd-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="382dd-129">Komut dosyasının tam yoluna bir araç ipucunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="382dd-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="382dd-130">Bir komut dosyasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-130">To run a script</span></span>
<span data-ttu-id="382dd-131">Araç çubuğunda tıklatın **komut dosyasını Çalıştır**, veya **dosya** menüsünde tıklatın **çalıştırmak**.</span><span class="sxs-lookup"><span data-stu-id="382dd-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="382dd-132">Bir bölümü bir komut çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-132">To run a portion of a script</span></span>

1. <span data-ttu-id="382dd-133">Betik bölmesinde bir betiğin bir bölümü seçin.</span><span class="sxs-lookup"><span data-stu-id="382dd-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="382dd-134">Üzerinde **dosya** menüsünde tıklatın **Seçimi Çalıştır**, veya araç çubuğunda tıklatın **Seçimi Çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="382dd-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="382dd-135">Çalışan bir komut dosyası durdurmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-135">To stop a running script</span></span>
<span data-ttu-id="382dd-136">Araç çubuğunda tıklatın **durdurma işlemi**, CTRL + BREAK tuşlarına basın veya **dosya** menüsünde tıklatın **durdurma işlemi**.</span><span class="sxs-lookup"><span data-stu-id="382dd-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="382dd-137">Tuşuna basarak **CTRL + C** bazı metinleri şu anda, bu durumda seçili değilse de çalışır **CTRL + C** kopyalama işlevi için seçili metni eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="382dd-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="382dd-138">Yazma ve düzenleme metin betik bölmesine</span><span class="sxs-lookup"><span data-stu-id="382dd-138">How to write and edit text in the Script Pane</span></span>
<span data-ttu-id="382dd-139">Betik bölmesine metnini düzenlemek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="382dd-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="382dd-140">Kopyalama, kesme, yapıştırma, bulmak ve metni Değiştir.</span><span class="sxs-lookup"><span data-stu-id="382dd-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="382dd-141">Ayrıca, Geri Al ve yalnızca gerçekleştirdiğiniz en son eylemi yinele.</span><span class="sxs-lookup"><span data-stu-id="382dd-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="382dd-142">Bu eylemleri gerçekleştirmek için klavye kısayolları tüm Windows uygulamaları için kullanılanlarla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="382dd-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="382dd-143">Betik bölmesinde metin girmek için</span><span class="sxs-lookup"><span data-stu-id="382dd-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="382dd-144">Betik bölmesinde herhangi bir yere tıklayarak veya tıklatarak imleci betik bölmesine gider **betik bölmesine gider** içinde **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="382dd-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="382dd-145">Bir komut dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="382dd-145">Create a script.</span></span> <span data-ttu-id="382dd-146">Sözdizimi renklendirmesi ve sekme tamamlama bu Windows PowerShell ISE daha zengin bir deneyim yapın.</span><span class="sxs-lookup"><span data-stu-id="382dd-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="382dd-147">Bkz: [kullanım sekme tamamlama betik bölmesine ve konsol bölmesinde nasıl](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) yazarak de yardımcı olmak için sekme tamamlama özelliğini kullanma hakkında ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="382dd-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="382dd-148">Betik bölmesinde metin bulmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="382dd-149">Herhangi bir yere metin bulmak için basın **CTRL + F** veya **Düzenle** menüsünde tıklatın **komut dosyasında bulmak**.</span><span class="sxs-lookup"><span data-stu-id="382dd-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="382dd-150">İmleci sonra metin bulmak için basın **F3** veya **Düzenle** menüsünde tıklatın **komut Sonrakini Bul**.</span><span class="sxs-lookup"><span data-stu-id="382dd-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="382dd-151">İmleç önce metin bulmak için basın **SHIFT + F3** veya **Düzenle** menüsünde tıklatın **komut Öncekini Bul**.</span><span class="sxs-lookup"><span data-stu-id="382dd-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="382dd-152">Betik bölmesine metin bulma ve değiştirme için</span><span class="sxs-lookup"><span data-stu-id="382dd-152">To find and replace text in the Script Pane</span></span>
<span data-ttu-id="382dd-153">Tuşuna **CRTL + H** veya **Düzenle** menüsünde tıklatın **komut dosyasında Değiştir**.</span><span class="sxs-lookup"><span data-stu-id="382dd-153">Press **CRTL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="382dd-154">Bulmak istediğiniz metin ve istediğiniz tuşuna basın ve bunun yerine metin girin **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="382dd-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="382dd-155">Betik bölmesine metnin belirli bir satırın gitmek için</span><span class="sxs-lookup"><span data-stu-id="382dd-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="382dd-156">Betik bölmesinde basın **CTRL + G** veya **Düzenle** menüsünde tıklatın **satıra gitme**.</span><span class="sxs-lookup"><span data-stu-id="382dd-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="382dd-157">Bir satır numarası girin.</span><span class="sxs-lookup"><span data-stu-id="382dd-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="382dd-158">Betik bölmesinde metin kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="382dd-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="382dd-159">Betik bölmesinde kopyalamak istediğiniz metni seçin.</span><span class="sxs-lookup"><span data-stu-id="382dd-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="382dd-160">Basın **CTRL + C** veya araç çubuğunda tıklatın **kopyalama** simgesi, veya **Düzenle** menüsünde tıklatın **kopyalama**.</span><span class="sxs-lookup"><span data-stu-id="382dd-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="382dd-161">Betik bölmesinde metin kesme</span><span class="sxs-lookup"><span data-stu-id="382dd-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="382dd-162">Betik bölmesinde kesmek istediğiniz metni seçin.</span><span class="sxs-lookup"><span data-stu-id="382dd-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="382dd-163">Tuşuna basın **CTRL + X** veya araç çubuğunda tıklatın **Kes** simgesi, veya **Düzenle** menüsünde tıklatın **Kes**.</span><span class="sxs-lookup"><span data-stu-id="382dd-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="382dd-164">Betik bölmesine metni yapıştırmak için</span><span class="sxs-lookup"><span data-stu-id="382dd-164">To paste text into the Script Pane</span></span>
<span data-ttu-id="382dd-165">Tuşuna **CTRL + V** veya araç çubuğunda tıklatın **Yapıştır** simgesi, veya **Düzenle** menüsünde tıklatın **Yapıştır**.</span><span class="sxs-lookup"><span data-stu-id="382dd-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="382dd-166">Betik bölmesine bir eylemi geri almak için</span><span class="sxs-lookup"><span data-stu-id="382dd-166">To undo an action in the Script Pane</span></span>
<span data-ttu-id="382dd-167">Tuşuna **CTRL + Z** veya araç çubuğunda tıklatın **geri** simgesi, veya **Düzenle** menüsünde tıklatın **geri**.</span><span class="sxs-lookup"><span data-stu-id="382dd-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="382dd-168">Betik bölmesine eylemi yinelemek için</span><span class="sxs-lookup"><span data-stu-id="382dd-168">To redo an action in the Script Pane</span></span>
<span data-ttu-id="382dd-169">Tuşuna **CTRL + Y** veya araç çubuğunda tıklatın **Yinele** simgesi, veya **Düzenle** menüsünde tıklatın **Yinele**.</span><span class="sxs-lookup"><span data-stu-id="382dd-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="382dd-170">Bir komut dosyasını kaydetme</span><span class="sxs-lookup"><span data-stu-id="382dd-170">How to save a script</span></span>
<span data-ttu-id="382dd-171">Kaydet ve bir betik adı için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="382dd-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="382dd-172">Bir yıldız işareti, değiştirilmiş olduğundan kaydedilmedi bir dosya olarak işaretlemek için komut dosyası adı yanında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="382dd-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="382dd-173">Dosyası kaydedildiğinde yıldız işareti kaybolur.</span><span class="sxs-lookup"><span data-stu-id="382dd-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="382dd-174">Bir komut dosyası kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="382dd-174">To save a script</span></span>
<span data-ttu-id="382dd-175">Tuşuna basın **CTRL + S** veya araç çubuğunda tıklatın **kaydetmek** simgesi veya **dosya** menüsünde tıklatın **kaydetmek**.</span><span class="sxs-lookup"><span data-stu-id="382dd-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="382dd-176">Kaydet ve bir betik adı</span><span class="sxs-lookup"><span data-stu-id="382dd-176">To save and name a script</span></span>

1. <span data-ttu-id="382dd-177">Üzerinde **dosya** menüsünde tıklatın **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="382dd-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="382dd-178">**Kaydet** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="382dd-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="382dd-179">İçinde **dosya adı** kutusuna, dosya için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="382dd-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="382dd-180">İçinde **farklı türde Kaydet** kutusunda, bir dosya türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="382dd-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="382dd-181">Örneğin, **farklı türde Kaydet** kutusunda ' œPowerShell komut dosyaları (\* .ps1)'.</span><span class="sxs-lookup"><span data-stu-id="382dd-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="382dd-182">**Kaydet**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="382dd-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="382dd-183">Bir komut dosyası ASCII kodlamasında kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="382dd-183">To save a script in ASCII encoding</span></span>
<span data-ttu-id="382dd-184">Varsayılan olarak, Windows PowerShell ISE yeni komut dosyaları (.ps1), komut dosyası veri dosyaları (.psd1) ve betik Modülü dosyaları (.psm1) Unicode (BigEndianUnicode) olarak varsayılan olarak kaydeder. Â için başka bir kodlamada bir komut dosyası kaydetme ASCII (ANSI gibi), kullanın **kaydetmek** veya **Farklı Kaydet** yöntemlere [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="382dd-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="382dd-185">Aşağıdaki komutu ASCII kodlama ile yeni bir komut dosyası MyScript.ps1 kaydeder.</span><span class="sxs-lookup"><span data-stu-id="382dd-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="382dd-186">Aşağıdaki komutu geçerli komut dosyasını aynı ada sahip, ancak ASCII kodlama ile bir dosya ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="382dd-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="382dd-187">Aşağıdaki komutu, geçerli dosyanın kodlamasını alır.</span><span class="sxs-lookup"><span data-stu-id="382dd-187">The following command gets the encoding of the current file.</span></span>

```
$psise.CurrentFile.encoding
```

<span data-ttu-id="382dd-188">Windows PowerShell ISE aşağıdaki kodlama seçeneklerini destekler: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 ve varsayılan.</span><span class="sxs-lookup"><span data-stu-id="382dd-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="382dd-189">Varsayılan seçenek değerini sistemine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="382dd-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="382dd-190">Windows PowerShell ISE diğer düzenleyicilerde tarafından oluşturulan komut dosyalarını kodlama değiştirmez bile Kaydet veya Kaydet kullandığınızda, Windows PowerShell ISE komutları.</span><span class="sxs-lookup"><span data-stu-id="382dd-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="382dd-191">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="382dd-191">See Also</span></span>
- [<span data-ttu-id="382dd-192">Windows PowerShell ISE kullanma</span><span class="sxs-lookup"><span data-stu-id="382dd-192">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

