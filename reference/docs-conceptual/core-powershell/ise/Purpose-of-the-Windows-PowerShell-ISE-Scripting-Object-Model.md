---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Nesne modeli komut dosyası Windows PowerShell ISE amacı"
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="70713-103">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="70713-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="70713-104">Form ve işlevi, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) ile ilişkili nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="70713-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="70713-105">Nesne Modeli Başvurusu, özellikleri ve bu nesnelerin kullanıma yöntemleri üye hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="70713-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="70713-106">Doğrudan bu yöntemlere ve özelliklere erişmek için komut dosyalarını nasıl kullanabileceğiniz göstermek için örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70713-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="70713-107">Komut dosyası nesne modeli görevleri aşağıdaki aralığı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="70713-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="70713-108">Windows PowerShell ISE görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="70713-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="70713-109">Uygulama ayarları ve seçenekleri değiştirmek için nesne modeli kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="70713-110">Örneğin, bunları aşağıdaki gibi değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="70713-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="70713-111">Hata ayıklama çıkarır ve hatalar, uyarılar, ayrıntılı çıktı rengini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

- <span data-ttu-id="70713-112">Alın veya komut bölmesi, çıkış bölmesi ve betik bölmesine ilişkin arka plan renklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70713-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

- <span data-ttu-id="70713-113">Çıkış bölmesinde ön plan rengini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-113">You can set the foreground color for the Output pane.</span></span>

- <span data-ttu-id="70713-114">Windows PowerShell ISE için yazı tipi adı ve yazı tipi boyutunu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="70713-115">Uyarılar yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-115">You can configure warnings.</span></span> <span data-ttu-id="70713-116">Bu ayar, birden çok PowerShell sekmelerdeki veya dosyayı kaydetmeden önce bir komut dosyasındaki çalıştırdığınızda bir dosya açıldığında, verilen uyarıları içerir.</span><span class="sxs-lookup"><span data-stu-id="70713-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

- <span data-ttu-id="70713-117">Betik bölmesine çıkış Bölmesi'üstünde olduğu betik bölmesine ve çıkış bölmesi yan yana nerede bir görünümü ve görünüm arasında geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="70713-118">Komut bölmesi veya çıkış bölmesi En Alta sabitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="70713-119">Windows PowerShell ISE işlevselliğini geliştirme</span><span class="sxs-lookup"><span data-stu-id="70713-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="70713-120">Windows PowerShell ISE işlevselliğini geliştirmek için nesne modeli kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="70713-121">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="70713-121">For example, you can:</span></span>

- <span data-ttu-id="70713-122">Ekleyebilir ve Windows PowerShell ISE kendisini örneği değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="70713-123">Örneğin, menüler değiştirmek için yeni menü öğeleri ekleme ve komut dosyaları için yeni menü öğelerini eşleyin.</span><span class="sxs-lookup"><span data-stu-id="70713-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

- <span data-ttu-id="70713-124">Windows PowerShell ISE düğmeleri ve menü komutlarını kullanarak gerçekleştirebileceğiniz görevlerden bazılarını gerçekleştirmek komut dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70713-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="70713-125">Örneğin, Ekle, Kaldır veya PowerShell sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="70713-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

- <span data-ttu-id="70713-126">Menü komutları ve düğmeleri kullanarak gerçekleştirilen görevleri tamamlama.</span><span class="sxs-lookup"><span data-stu-id="70713-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="70713-127">Örneğin, bir PowerShell sekmesi yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-127">For example, you can rename a PowerShell tab.</span></span>

- <span data-ttu-id="70713-128">Bir dosyayla ilişkili metin arabelleği komut bölmesi, çıkış bölmesi ve betik bölmesine yönetme.</span><span class="sxs-lookup"><span data-stu-id="70713-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="70713-129">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="70713-129">For example, you can:</span></span>

    -   <span data-ttu-id="70713-130">Alın veya tüm metni ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70713-130">Get or set all text.</span></span>

    -   <span data-ttu-id="70713-131">Alın veya bir metin seçimini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70713-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="70713-132">Komut dosyası çalıştırma veya bir komut dosyası seçili bir bölümünü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70713-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="70713-133">Bir satır görünümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="70713-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="70713-134">Metin bir şapka konumuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70713-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="70713-135">Bir metin bloğunu seçin.</span><span class="sxs-lookup"><span data-stu-id="70713-135">Select a block of text.</span></span>

    -   <span data-ttu-id="70713-136">Son satır numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="70713-136">Get the last line number.</span></span>

- <span data-ttu-id="70713-137">Dosya işlemleri</span><span class="sxs-lookup"><span data-stu-id="70713-137">Perform file operations.</span></span> <span data-ttu-id="70713-138">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="70713-138">For example, you can:</span></span>

    -   <span data-ttu-id="70713-139">Bir dosyayı açın, bir dosyayı kaydedin veya bir dosyayı farklı bir ad kullanarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70713-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="70713-140">Son kaydedildikten sonra dosya değiştirilip değiştirilmediğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="70713-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="70713-141">Dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="70713-141">Get the file name.</span></span>

    -   <span data-ttu-id="70713-142">Bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="70713-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="70713-143">Görevleri otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="70713-143">Automating tasks</span></span>
 <span data-ttu-id="70713-144">Komut dosyası nesne modeli, sık kullanılan işlemleri için klavye kısayolları oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70713-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="70713-145">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="70713-145">See Also</span></span>
- [<span data-ttu-id="70713-146">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="70713-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="70713-147">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="70713-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="70713-148">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="70713-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
