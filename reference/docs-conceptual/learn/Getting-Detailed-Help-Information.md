---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Ayrıntılı Yardım Bilgisi Alma
ms.openlocfilehash: 3f52de8c9963618c154b119d5f4859a92d61fbda
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030409"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="497b2-103">Ayrıntılı yardım bilgisi alma</span><span class="sxs-lookup"><span data-stu-id="497b2-103">Getting detailed help information</span></span>

<span data-ttu-id="497b2-104">PowerShell, PowerShell kavramlarını ve PowerShell dil açıklayan ayrıntılı yardım makaleleri içerir.</span><span class="sxs-lookup"><span data-stu-id="497b2-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="497b2-105">Pek çok işlev ve betik ve her cmdlet sağlayıcısı için Yardım makaleleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="497b2-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="497b2-106">Komut isteminde bu Yardım makaleleri görüntüleyebilir veya görünümü en son güncelleştirilmiş aşağıdaki makalelerde sürümlerini [PowerShell](/powershell/scripting/overview) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="497b2-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="497b2-107">Cmdlet'leri için Yardım alma</span><span class="sxs-lookup"><span data-stu-id="497b2-107">Getting help for cmdlets</span></span>

<span data-ttu-id="497b2-108">PowerShell cmdlet'leri hakkında Yardım almak için kullanın [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="497b2-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="497b2-109">Örneğin, Yardım almak için `Get-ChildItem` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="497b2-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="497b2-110">veya</span><span class="sxs-lookup"><span data-stu-id="497b2-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="497b2-111">Hatta, Get-Help cmdlet'i hakkında Yardım alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="497b2-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="497b2-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="497b2-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="497b2-113">Tüm cmdlet listesi Yardım makaleleri oturumunuzda almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="497b2-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="497b2-114">Bir kerede bir sayfa her Yardım makalesinin görüntülemek için kullanın `help` işlevi veya diğer adıyla `man`.</span><span class="sxs-lookup"><span data-stu-id="497b2-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="497b2-115">Örneğin, Yardım için görüntülenecek `Get-ChildItem` cmdlet'i, türü</span><span class="sxs-lookup"><span data-stu-id="497b2-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="497b2-116">veya</span><span class="sxs-lookup"><span data-stu-id="497b2-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="497b2-117">Ayrıntılı bilgi görüntülemek için kullanın **ayrıntılı** parametresinin `Get-Help` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="497b2-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="497b2-118">Örneğin, hakkında ayrıntılı bilgi almak için `Get-ChildItem` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="497b2-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="497b2-119">Yardım makalesi tüm içeriği görüntülemek için kullanın **tam** parametresinin `Get-Help` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="497b2-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="497b2-120">Örneğin, Yardım makalesi için tüm içeriği görüntülemek için `Get-ChildItem` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="497b2-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="497b2-121">Almak için Yardım kullanımı bir cmdlet parametreleri hakkında ayrıntılı **parametre** parametresinin `Get-Help` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="497b2-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="497b2-122">Örneğin, almak için ayrıntılı yardım almak için tüm parametreleri `Get-ChildItem` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="497b2-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="497b2-123">Bir Yardım makalesinde yalnızca örnekleri görüntülemek için kullanın **örnekler** parametresinin `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="497b2-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="497b2-124">Örneğin, Yardım makalesi için yalnızca örnekleri görüntülemek için `Get-ChildItem` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="497b2-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="497b2-125">Yazdığınız cmdlet'leri için Yardım makaleleri yazma hakkında daha fazla bilgi için bkz: [yazma Cmdlet Yardım nasıl](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="497b2-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="497b2-126">Kavramsal Yardım alma</span><span class="sxs-lookup"><span data-stu-id="497b2-126">Getting conceptual help</span></span>

<span data-ttu-id="497b2-127">`Get-Help` Cmdlet ayrıca görüntüler kavramsal makaleleri hakkında bilgi PowerShell, PowerShell dilinin hakkında makaleler de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="497b2-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="497b2-128">Kavramsal Yardım makaleleri başlamak about_line_editing gibi "about_" ön ekine sahip.</span><span class="sxs-lookup"><span data-stu-id="497b2-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="497b2-129">(Makale adı İngilizce PowerShell bile İngilizce olmayan sürümleri üzerinde girilmesi gerekir.)</span><span class="sxs-lookup"><span data-stu-id="497b2-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="497b2-130">Kavramsal makaleleri listesini görüntülemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="497b2-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="497b2-131">Belirli bir Yardım makalesi görüntülemek için örneğin makale adı yazın:</span><span class="sxs-lookup"><span data-stu-id="497b2-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="497b2-132">Parametreleri `Get-Help`, gibi **ayrıntılı**, **parametre**, ve **örnekler**, kavramsal Yardım makaleleri görüntülenmesini üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="497b2-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="497b2-133">Sağlayıcılar hakkında Yardım alma</span><span class="sxs-lookup"><span data-stu-id="497b2-133">Getting help about providers</span></span>

<span data-ttu-id="497b2-134">`Get-Help` Cmdlet'i, PowerShell sağlayıcıları hakkında daha fazla bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="497b2-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="497b2-135">Sağlayıcı için Yardım almak için şunu yazın `Get-Help` ardından sağlayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="497b2-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="497b2-136">Örneğin, kayıt defteri sağlayıcısı için Yardım almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="497b2-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="497b2-137">Sağlayıcı listesi Yardım makaleleri oturumunuzda almak için yazın</span><span class="sxs-lookup"><span data-stu-id="497b2-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="497b2-138">Parametreleri `Get-Help`, gibi **ayrıntılı**, **parametre**, ve **örnekler**, sağlayıcı Yardım makaleleri görüntülenmesini üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="497b2-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="497b2-139">Betik ve işlevlerde hakkında Yardım alma</span><span class="sxs-lookup"><span data-stu-id="497b2-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="497b2-140">Birçok betik ve işlevlerde PowerShell'de Yardım makaleleri sahip.</span><span class="sxs-lookup"><span data-stu-id="497b2-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="497b2-141">Kullanım `Get-Help` betik ve işlevlerde kullanılan Yardım makaleleri görüntülemek için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="497b2-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="497b2-142">Bir işlev için Yardım görüntülemek üzere şunu yazın `Get-Help` ardından işlevi adı.</span><span class="sxs-lookup"><span data-stu-id="497b2-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="497b2-143">Örneğin, Yardım almak için `Disable-PSRemoting` işlev, yazın:</span><span class="sxs-lookup"><span data-stu-id="497b2-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="497b2-144">Bir komut için Yardım görüntülemek için betik dosyasının yolunu yazın.</span><span class="sxs-lookup"><span data-stu-id="497b2-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="497b2-145">Betiği, Path ortam değişkeninde listelenen bir yol değil, tam yolu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="497b2-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="497b2-146">Örneğin, C: "TestScript.ps1" adlı bir komut dosyası varsa\\Yardım makalesi betik, tür için görüntülenecek PS Test dizini:</span><span class="sxs-lookup"><span data-stu-id="497b2-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="497b2-147">Betik ve işlevi için cmdlet Yardım iş görüntülemek için tasarlanmış parametreleri, çok yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="497b2-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="497b2-148">Programını çalıştırdığınızda işlev ve betik Yardımı ancak gösterilmez `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="497b2-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="497b2-149">Yardım makaleleri işlev ve betik yazma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="497b2-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="497b2-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="497b2-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="497b2-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="497b2-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="497b2-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="497b2-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="497b2-153">Çevrimiçi Yardım alma</span><span class="sxs-lookup"><span data-stu-id="497b2-153">Getting help online</span></span>

<span data-ttu-id="497b2-154">Çevrimiçi Yardım makaleleri görüntüleme konusunda yardım almak için en iyi yollarından biridir.</span><span class="sxs-lookup"><span data-stu-id="497b2-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="497b2-155">Çevrimiçi makaleler, güncelleştirmek ve en güncel içeriği sağlamak daha kolay.</span><span class="sxs-lookup"><span data-stu-id="497b2-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="497b2-156">Çevrimiçi Yardım almak için kullanın **çevrimiçi** parametresinin `Get-Help` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="497b2-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="497b2-157">Sağlayıcı Yardım dahil olmak üzere PowerShell ile gelen tüm Yardım makaleleri ve kavramsal (hakkında) Yardım makaleleri çevrimiçi kullanılabilir [PowerShell](/powershell/scripting/powershell-scripting) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="497b2-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="497b2-158">Kullanamazsınız **çevrimiçi** kavramsal parametresiyle (about_\*) ya da sağlayıcı Yardım makaleleri.</span><span class="sxs-lookup"><span data-stu-id="497b2-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="497b2-159">Çevrimiçi Yardım, isteğe bağlı olduğundan her cmdlet, işlev veya betiği için çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="497b2-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="497b2-160">Örneğin, hakkında Yardım makalesi'nın çevrimiçi sürümünü almak için `Get-ChildItem` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="497b2-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="497b2-161">Makalede, PowerShell varsayılan tarayıcınızda açılır.</span><span class="sxs-lookup"><span data-stu-id="497b2-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="497b2-162">Çevrimiçi Yardım için Yardım makalesine destekleniyorsa, Yardım makalesi URL'sini de görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="497b2-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="497b2-163">URL, bir Yardım makalesinin ilgili bağlantılar bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="497b2-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="497b2-164">Örneğin, Add-Computer cmdlet'ın çevrimiçi sürümünü URL'sini görmek için aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="497b2-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="497b2-165">Makalenin ilgili bağlantılar bölümüne ilk satırı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="497b2-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="497b2-166">Çevrimiçi destek için Yardım makaleleriniz sağlama hakkında daha fazla bilgi için bkz: [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="497b2-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="497b2-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="497b2-167">See also</span></span>

- [<span data-ttu-id="497b2-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="497b2-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="497b2-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="497b2-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="497b2-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="497b2-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="497b2-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="497b2-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
