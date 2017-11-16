---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Ayrıntılı yardım bilgi alma"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="32b88-103">Ayrıntılı yardım bilgi alma</span><span class="sxs-lookup"><span data-stu-id="32b88-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="32b88-104">Windows PowerShell, Windows PowerShell kavramları ve Windows PowerShell dil açıklayan ayrıntılı Yardım konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="32b88-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="32b88-105">Ayrıca her bir cmdlet'i ve sağlayıcı için Yardım konularını ve vardır birçok işlevleri ve komut dosyaları için Yardım konularını.</span><span class="sxs-lookup"><span data-stu-id="32b88-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="32b88-106">Komut isteminde bu Yardım konularını görüntülemek veya en yakın zamanda güncelleştirilmiş sürümleri bu konularda, Microsoft TechNet Library içinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="32b88-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="32b88-107">Windows PowerShell, Windows PowerShell Tümleşik komut dosyası ortamı gibi konak birçok program derlenmiş Yardım dosyası (.chm) ve bağlama duyarlı Yardım gibi ek Yardım özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="32b88-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="32b88-108">Cmdlet'leri için Yardım alma</span><span class="sxs-lookup"><span data-stu-id="32b88-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="32b88-109">Windows PowerShell cmdlet'leri hakkında Yardım almak için kullanmak [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="32b88-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="32b88-110">Örneğin, Yardım almak için [Get-Childıtem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, türü:</span><span class="sxs-lookup"><span data-stu-id="32b88-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="32b88-111">veya</span><span class="sxs-lookup"><span data-stu-id="32b88-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="32b88-112">Hatta, Get-Help cmdlet'i hakkında Yardım alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32b88-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="32b88-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="32b88-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="32b88-114">Oturumunuzda tüm cmdlet'i Yardım konularını listesini almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="32b88-115">Aynı anda her Yardım konusunun bir sayfasını görüntülemek için **yardımcı** işlevi veya diğer adını **ADAM**.</span><span class="sxs-lookup"><span data-stu-id="32b88-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="32b88-116">Örneğin, Yardım için Get-Childıtem cmdlet'i görüntülemek için şunu yazın</span><span class="sxs-lookup"><span data-stu-id="32b88-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="32b88-117">veya</span><span class="sxs-lookup"><span data-stu-id="32b88-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="32b88-118">Cmdlet, işlev veya komut dosyası, kendi kullanım örnekleri ve parametre açıklamaları da dahil olmak üzere ilgili ayrıntılı bilgileri görüntülemek için kullanın *ayrıntılı* Get-Help cmdlet parametresi.</span><span class="sxs-lookup"><span data-stu-id="32b88-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="32b88-119">Örneğin, Get-Childıtem cmdlet hakkında ayrıntılı bilgi almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="32b88-120">Yardım konusundaki tüm içeriği görüntülemek için kullanın *tam* Get-Help cmdlet parametresi.</span><span class="sxs-lookup"><span data-stu-id="32b88-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="32b88-121">Örneğin, Get-Childıtem cmdlet için Yardım konusundaki tüm içeriği görüntülemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="32b88-122">Almak için Yardım kullanımı bir cmdlet parametreleri hakkında ayrıntılı *parametresi* Get-Help cmdlet parametresi.</span><span class="sxs-lookup"><span data-stu-id="32b88-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="32b88-123">Örneğin, tüm türü Get-Childıtem cmdlet'i parametreleri için Yardım ayrıntılı almak için:</span><span class="sxs-lookup"><span data-stu-id="32b88-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="32b88-124">Yardım konusunun yalnızca örnekler görüntülemek için kullanın *örnek* Get-Help parametresi.</span><span class="sxs-lookup"><span data-stu-id="32b88-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="32b88-125">Örneğin, yalnızca örnek Get-Childıtem cmdlet için Yardım konusu görüntülemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="32b88-126">Yazdığınız cmdlet'leri için Yardım konuları yazma hakkında daha fazla bilgi için bkz: [yazma Cmdlet Yardım nasıl](https://go.microsoft.com/fwlink/?LinkID=123415) MSDN Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="32b88-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="32b88-127">Kavramsal Yardım alma</span><span class="sxs-lookup"><span data-stu-id="32b88-127">Getting Conceptual Help</span></span>
<span data-ttu-id="32b88-128">Get-Help cmdlet'i Windows PowerShell, Windows PowerShell dili ile ilgili konular da dahil olmak üzere kavramsal konuları hakkında bilgi de görüntüler.</span><span class="sxs-lookup"><span data-stu-id="32b88-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="32b88-129">Kavramsal Yardım konuları about_line_editing gibi "about_" öneki ile başlar.</span><span class="sxs-lookup"><span data-stu-id="32b88-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="32b88-130">(Kavramsal konu adını İngilizce bile İngilizce dışındaki sürümlerinde Windows PowerShell girilmesi gerekir.)</span><span class="sxs-lookup"><span data-stu-id="32b88-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="32b88-131">Kavramsal konu listesini görüntülemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="32b88-132">Belirli bir Yardım konusu görüntülemek için konu adı, örneğin yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="32b88-133">Get-Help parametrelerinin gibi *ayrıntılı*, *parametresi*, ve *örnekler*, kavramsal Yardım konularının görüntülenmesini üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="32b88-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="32b88-134">Sağlayıcılar hakkında Yardım alma</span><span class="sxs-lookup"><span data-stu-id="32b88-134">Getting Help About Providers</span></span>
<span data-ttu-id="32b88-135">Get-Help cmdlet'i Windows PowerShell sağlayıcıları hakkında bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="32b88-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="32b88-136">Ardından sağlayıcı adı için bir sağlayıcı Yardım almak için "Get-Help" yazın.</span><span class="sxs-lookup"><span data-stu-id="32b88-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="32b88-137">Örneğin, kayıt defteri sağlayıcısı için Yardım almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="32b88-138">Tüm listesini almak için oturumunuzu sağlayıcısı Yardım konularında yazın</span><span class="sxs-lookup"><span data-stu-id="32b88-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="32b88-139">Get-Help parametrelerinin gibi *ayrıntılı*, *parametresi*, ve *örnekler*, sağlayıcı Yardım konularının görüntülenmesini üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="32b88-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="32b88-140">Komut dosyaları ve işlevleri hakkında Yardım alma</span><span class="sxs-lookup"><span data-stu-id="32b88-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="32b88-141">Çok sayıda betik ve işlevlerde Windows PowerShell'de Yardım konuları vardır.</span><span class="sxs-lookup"><span data-stu-id="32b88-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="32b88-142">Betik ve işlevlerde için Yardım konularını görüntülemek için Get-Help cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="32b88-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="32b88-143">Bir işlev için Yardım görüntülemek için "get-help işlevi adından" yazın.</span><span class="sxs-lookup"><span data-stu-id="32b88-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="32b88-144">Örneğin, devre dışı bırak-PSRemoting işlevi için Yardım almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="32b88-145">Bir komut dosyası için Yardım görüntülemek için komut dosyasının tam yolunu yazın.</span><span class="sxs-lookup"><span data-stu-id="32b88-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="32b88-146">Komut dosyası Path ortam değişkeninde listelenen bir yol ise, komut yolundan atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32b88-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="32b88-147">Örneğin, C: "TestScript.ps1" adlı bir komut dosyası varsa\\PS Test dizin, komut dosyası türü için Yardım konusunu görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="32b88-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="32b88-148">Cmdlet görüntülemek için tasarlanmış olan parametreleri Yardım, gibi *ayrıntılı*, *tam*, *örnekler*, ve *parametresi*, iş için komut dosyası Yardım ve işlevi, çok yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="32b88-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="32b88-149">Ancak, görüntülediğinizde tüm Yardım yazarak "get-help \*", yardımcı olmak için işlevleri ve komut dosyaları görünmez.</span><span class="sxs-lookup"><span data-stu-id="32b88-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="32b88-150">İşlevleri ve komut dosyalarınız için Yardım konuları yazma hakkında daha fazla bilgi için bkz: [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), ve [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="32b88-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="32b88-151">Çevrimiçi Yardım alma</span><span class="sxs-lookup"><span data-stu-id="32b88-151">Getting Help Online</span></span>
<span data-ttu-id="32b88-152">Internet'e bağlıysanız, Yardım almak için en iyi yöntemleri çevrimiçi Yardım konularını görüntülemek için biridir.</span><span class="sxs-lookup"><span data-stu-id="32b88-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="32b88-153">Çevrimiçi konuları güncelleştirmek kolay olduğundan, bunlar en güncel içeriği sağlamak olasıdır.</span><span class="sxs-lookup"><span data-stu-id="32b88-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="32b88-154">Çevrimiçi Yardım almak için deneyin *çevrimiçi* Get-Help cmdlet parametresi.</span><span class="sxs-lookup"><span data-stu-id="32b88-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="32b88-155">*Çevrimiçi* parametresi yalnızca cmdlet Yardım için Get-Help cmdlet'i çalışır, Yardım işlev ve Yardım komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="32b88-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="32b88-156">Kullanamazsınız *çevrimiçi* parametresiyle kavramsal (hakkında) konuları veya sağlayıcı Yardım konuları.</span><span class="sxs-lookup"><span data-stu-id="32b88-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="32b88-157">Bu özellik isteğe bağlı olduğundan, ayrıca, her cmdlet, işlev veya komut dosyası Yardım konusunu çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="32b88-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="32b88-158">Ancak, tüm Yardım konuları gelen sağlayıcısı Yardım dahil olmak üzere Windows PowerShell ile ve (hakkında) Yardım konuları, kavramsal çevrimiçi kullanılabilir [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) Microsoft TechNet Library bölümü.</span><span class="sxs-lookup"><span data-stu-id="32b88-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="32b88-159">Kullanılacak *çevrimiçi* parametresi Get-Help cmdlet'i, aşağıdaki komut biçimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="32b88-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="32b88-160">Örneğin, Get-Childıtem cmdlet'i hakkında Yardım konusunun çevrimiçi sürümünü almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="32b88-161">Yardım konusunun çevrimiçi sürümünü kullanılabilir durumda, varsayılan tarayıcıda açılır.</span><span class="sxs-lookup"><span data-stu-id="32b88-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="32b88-162">Çevrimiçi Yardım için Yardım konusunun destekleniyorsa, Yardım konusunun Internet adresi (URL) de görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32b88-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="32b88-163">Internet adresini Yardım konusunun ilgili bağlantılar bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="32b88-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="32b88-164">Örneğin, Add-Computer cmdlet çevrimiçi sürümünü URL'sini görmek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="32b88-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="32b88-165">Konunun ilgili bağlantılar bölümündeki ilk satırı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32b88-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="32b88-166">Çevrimiçi desteklemek için Yardım konuları hakkında daha fazla bilgi için bkz: [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)ve [yazma Cmdlet Yardım nasıl](https://go.microsoft.com/fwlink/?LinkID=123415) MSDN Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="32b88-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="32b88-167">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="32b88-167">See Also</span></span>
- <span data-ttu-id="32b88-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span><span class="sxs-lookup"><span data-stu-id="32b88-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span></span>
- [<span data-ttu-id="32b88-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="32b88-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="32b88-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="32b88-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- <span data-ttu-id="32b88-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span><span class="sxs-lookup"><span data-stu-id="32b88-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span></span>

