---
title: Windows PowerShell modülleri için Yardım yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845461"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="43e08-102">Windows PowerShell Modülleri için Yardım Dosyaları Yazma</span><span class="sxs-lookup"><span data-stu-id="43e08-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="43e08-103">Windows PowerShell modülleri ve cmdlet'leri, sağlayıcıları, İşlevler ve betikler gibi modülü üyeleri modülü hakkında Yardım konuları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="43e08-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="43e08-104">`Get-Help` Cmdlet diğer Windows PowerShell öğeleri için yardımı görüntüler ve kullanıcıların standart bu modülü Yardım konuları aynı biçimde görüntüler `Get-Help` Yardımı almak için komutları.</span><span class="sxs-lookup"><span data-stu-id="43e08-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="43e08-105">Bu belge, biçimi ve modül Yardımı doğru yerleşimi açıklar ve yönergeleri modülü Yardım içeriği önerir.</span><span class="sxs-lookup"><span data-stu-id="43e08-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="43e08-106">Tür modülü Yardımı</span><span class="sxs-lookup"><span data-stu-id="43e08-106">Types of Module Help</span></span>

<span data-ttu-id="43e08-107">Bir modül Yardım aşağıdaki türleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="43e08-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="43e08-108">**Cmdlet yardımına**.</span><span class="sxs-lookup"><span data-stu-id="43e08-108">**Cmdlet Help**.</span></span> <span data-ttu-id="43e08-109">Bir modüldeki cmdlet'ler açıklayan Yardım konularının şema komutunu kullanın, XML dosyalarını yardımcı olan</span><span class="sxs-lookup"><span data-stu-id="43e08-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="43e08-110">**Sağlayıcı Yardım**.</span><span class="sxs-lookup"><span data-stu-id="43e08-110">**Provider Help**.</span></span> <span data-ttu-id="43e08-111">Yardım sağlayıcıları bir modüle açıklayan Yardım şema sağlayıcısı XML dosyaları konulardır.</span><span class="sxs-lookup"><span data-stu-id="43e08-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="43e08-112">**İşlev Yardım**.</span><span class="sxs-lookup"><span data-stu-id="43e08-112">**Function Help**.</span></span> <span data-ttu-id="43e08-113">Modül içindeki işlevleri açıklayan Yardım konularının komutunu kullanın, XML dosyalarını şema veya açıklama tabanlı Yardım konuları işlev veya komut dosyası veya betik modülündeki yardımcı olabilir</span><span class="sxs-lookup"><span data-stu-id="43e08-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="43e08-114">**Komut Yardımı**.</span><span class="sxs-lookup"><span data-stu-id="43e08-114">**Script Help**.</span></span> <span data-ttu-id="43e08-115">Bir modül betiklerde açıklayan Yardım konuları, şema veya açıklama tabanlı Yardım konuları betik veya betik modülündeki ' komutunu kullanın, XML dosyalarını yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="43e08-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="43e08-116">**("Hakkında") Yardım kavramsal**.</span><span class="sxs-lookup"><span data-stu-id="43e08-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="43e08-117">("") Yardım konu hakkında kavramsal modülü ve üyelerini açıklar ve nasıl üyeleri birlikte görevleri gerçekleştirmek için kullanılabilir açıklamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43e08-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="43e08-118">Kavramsal Yardım konuları, kodlama Unicode (UTF-8) ile metin dosyaları olan.</span><span class="sxs-lookup"><span data-stu-id="43e08-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="43e08-119">Dosya adı kullanmalıdır `about_<name>.help.txt` about_MyModule.help.txt gibi biçimi.</span><span class="sxs-lookup"><span data-stu-id="43e08-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="43e08-120">Varsayılan olarak, Windows PowerShell üzerinde 100 Bu kavramsal hakkında Yardım konuları içerir ve bunlar aşağıdaki gibi biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="43e08-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="43e08-121">Yerleşimini modülü Yardımı</span><span class="sxs-lookup"><span data-stu-id="43e08-121">Placement of Module Help</span></span>

<span data-ttu-id="43e08-122">`Get-Help` Cmdlet'i modül dizinini, dile özgü alt modülü Yardım konusu dosyaları arar.</span><span class="sxs-lookup"><span data-stu-id="43e08-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="43e08-123">Örneğin, aşağıdaki dizin yapısını diyagram SampleModule modül için Yardım konularını konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="43e08-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="43e08-124">Örnekte,  *\<ModulePath >* yer tutucusu yollarında birini temsil eder `PSModulePath` $home\Documents\Modules, $pshome\Modules veya kullanıcının belirttiği özel bir yol gibi ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="43e08-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="43e08-125">Modül Yardım alma</span><span class="sxs-lookup"><span data-stu-id="43e08-125">Getting Module Help</span></span>

<span data-ttu-id="43e08-126">Bir kullanıcı bir modülün oturuma aktardığında, bu modül için Yardım konularını oturumuna modülü ile birlikte içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="43e08-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="43e08-127">Modül bildirimindeki FileList anahtarının değerini Yardım konusu dosyaları listeleyebilirsiniz ancak Yardım konuları etkilenmez `Export-ModuleMember` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="43e08-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="43e08-128">Farklı dillerde modülü Yardım konuları sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43e08-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="43e08-129">`Get-Help` Cmdlet'i otomatik olarak görüntüler modülü Yardım konuları için Denetim Masası'nda Bölge ve Dil Seçenekleri öğesi geçerli kullanıcının belirtilen dilde.</span><span class="sxs-lookup"><span data-stu-id="43e08-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="43e08-130">Windows Vista ve sonraki sürümlerinde, Windows `Get-Help` Yardım konular, dile özgü alt modülü dizin için Windows dil geri dönüş standartlarla uygun olarak arar.</span><span class="sxs-lookup"><span data-stu-id="43e08-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="43e08-131">Çalışan Windows PowerShell 3.0 başlayan bir `Get-Help` komutu bir cmdlet veya işlevi için otomatik modül içeri tetikler.</span><span class="sxs-lookup"><span data-stu-id="43e08-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="43e08-132">`Get-Help` Cmdlet modülünde hemen Yardım konularının içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e08-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="43e08-133">Modül, Yardım konuları içermiyor ve hiçbir kullanıcının bilgisayarında modüldeki komutlar için Yardım konularını varsa `Get-Help` otomatik olarak oluşturulan Yardımı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e08-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="43e08-134">Otomatik olarak oluşturulmuş Yardım komut söz dizimi, parametreleri ve girdi ve çıktı türleri içerir, ancak herhangi bir açıklamasını içermez.</span><span class="sxs-lookup"><span data-stu-id="43e08-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="43e08-135">Otomatik olarak oluşturulmuş Yardım kullanmaya çalıştığınızda kullanıcının yönlendiren metin içeren `Update-Help` cmdlet'ini Internet veya Dosya Paylaşımı'ndan komut için Yardım'ı yükle.</span><span class="sxs-lookup"><span data-stu-id="43e08-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="43e08-136">Ayrıca kullanmanızı önerir **çevrimiçi** parametresinin `Get-Help` Yardım konusunun çevrimiçi sürümünü almak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43e08-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="43e08-137">Güncelleştirilebilir Yardımı Destekleme</span><span class="sxs-lookup"><span data-stu-id="43e08-137">Supporting Updatable Help</span></span>

<span data-ttu-id="43e08-138">Kullanıcılar, Windows PowerShell 3.0 ve sonraki sürümlerinde Windows PowerShell, indirin ve Internet'ten veya bir yerel dosya paylaşımından bir modül için güncelleştirilmiş Yardım dosyalarını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="43e08-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="43e08-139">`Update-Help` Ve `Save-Help` cmdlet'leri kullanıcı yönetimi ayrıntıları gizle.</span><span class="sxs-lookup"><span data-stu-id="43e08-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="43e08-140">Kullanıcıların çalıştırmasını `Update-Help` cmdlet'ini ve ardından `Get-Help` cmdlet Windows PowerShell komut isteminde modülü için en yeni Yardım dosyaları okumak için.</span><span class="sxs-lookup"><span data-stu-id="43e08-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="43e08-141">Kullanıcılar, Windows veya Windows PowerShell yeniden başlatmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="43e08-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="43e08-142">Güvenlik duvarları ve Internet erişimi olmayan kullanıcıların güncelleştirilebilir Yardımı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43e08-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="43e08-143">Yöneticileri Internet erişimi kullanım `Save-Help` indirmek ve bir dosya paylaşımı için en yeni Yardım dosyaları yüklemek için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="43e08-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="43e08-144">Ardından, kullanıcıların kullanması **yolu** parametresinin `Update-Help` dosya paylaşımından en yeni Yardım dosyaları almak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43e08-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="43e08-145">Modül yazarları, modüldeki Yardım dosyaları içerir ve Yardım dosyaları güncelleştirmek veya modülünden Yardım dosyaları çıkarın ve yüklemek ve bunları güncelleştirmek için güncelleştirilebilir Yardımı kullanın için güncelleştirilebilir Yardımı'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="43e08-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="43e08-146">Güncelleştirilebilir Yardımı hakkında daha fazla bilgi için bkz: [güncelleştirilebilir Yardımı destekleme](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="43e08-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="43e08-147">Çevrimiçi Yardımı Destekleme</span><span class="sxs-lookup"><span data-stu-id="43e08-147">Supporting Online Help</span></span>

<span data-ttu-id="43e08-148">Olamaz veya yükleme kullanıcıları Yardım dosyalarını bilgisayarlarında genellikle modülü Yardım konuları online sürümüne dayanan güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="43e08-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="43e08-149">**Çevrimiçi** parametresinin `Get-Help` cmdlet'i, bir cmdlet veya Gelişmiş işlevi kullanıcının Yardım konusunun çevrimiçi sürümünü kendi varsayılan Internet tarayıcısında açar.</span><span class="sxs-lookup"><span data-stu-id="43e08-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="43e08-150">`Get-Help` Cmdlet'ini kullanır değerini **HelpUri** cmdlet'ini veya işlevin Yardım konusunun çevrimiçi sürümünü bulmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="43e08-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="43e08-151">Windows PowerShell 3. 0'den itibaren cmdlet ve işlev Yardım konuları'nın çevrimiçi sürümünü cmdlet'i sınıf üzerinde HelpUri özniteliğini tanımlayarak bulmalarına yardımcı olabilir veya **HelpUri** özelliği **CmdletBinding** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="43e08-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="43e08-152">Özniteliğin değerini değeridir **HelpUri** cmdlet'ini veya işlevin özelliği.</span><span class="sxs-lookup"><span data-stu-id="43e08-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="43e08-153">Daha fazla bilgi için [çevrimiçi Yardımı destekleme](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="43e08-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43e08-154">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="43e08-154">See Also</span></span>

[<span data-ttu-id="43e08-155">Bir Windows PowerShell modülü yazma</span><span class="sxs-lookup"><span data-stu-id="43e08-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="43e08-156">Güncelleştirilebilir Yardımı destekleme</span><span class="sxs-lookup"><span data-stu-id="43e08-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="43e08-157">Çevrimiçi Yardımı destekleme</span><span class="sxs-lookup"><span data-stu-id="43e08-157">Supporting Online Help</span></span>](./supporting-online-help.md)