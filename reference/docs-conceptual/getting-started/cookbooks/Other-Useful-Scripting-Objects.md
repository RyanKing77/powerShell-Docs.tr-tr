---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Diğer kullanışlı komut dosyası nesneleri"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="5a1b8-103">Diğer kullanışlı komut dosyası nesneleri</span><span class="sxs-lookup"><span data-stu-id="5a1b8-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="5a1b8-104">Aşağıdaki nesneler Windows PowerShell ISE komut dosyası ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="5a1b8-105">Olmadıkları parçası **$psISE** hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="5a1b8-106">Yararlı komut dosyası nesneleri</span><span class="sxs-lookup"><span data-stu-id="5a1b8-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="5a1b8-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="5a1b8-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="5a1b8-108">Windows PowerShell ISE konsol uygulamaları ile nasıl etkileşim kurduğu bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="5a1b8-109">Bir komut veya kullanıcı etkileşimi gerektiren bir otomasyon komut dosyası Windows PowerShell konsolundan çalışma biçimini çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="5a1b8-110">Bu komutlar veya komut dosyaları Windows PowerShell ISE komutu bölmesinde çalışmasını engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="5a1b8-111">**$PsUnsupportedConsoleApplications** nesnesi gibi komutların listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="5a1b8-112">Bu listede komutları çalıştırmayı deneyin, bunlar desteklenmez bir ileti alırsınız.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="5a1b8-113">Aşağıdaki komut dosyasını bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="5a1b8-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="5a1b8-114">$psLocalHelp</span></span>
 <span data-ttu-id="5a1b8-115">Bu Yardım konuları ve yerel koda derlenmiş HTML Yardım dosyasındaki ilişkili bağlantılarını arasında bağlama duyarlı bir eşleme tutan bir sözlük nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="5a1b8-116">Belirli bir konu için yerel Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="5a1b8-117">Ekleyebilir veya bu listeden konuları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="5a1b8-118">Aşağıdaki kod örneğinde bazı örnek bulunan anahtar-değer çiftleri gösterir **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="5a1b8-119">Örnek Çıkış</span><span class="sxs-lookup"><span data-stu-id="5a1b8-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="5a1b8-120">Anahtar:-Bilgisayar Ekle</span><span class="sxs-lookup"><span data-stu-id="5a1b8-120">Key : Add-Computer</span></span>|<span data-ttu-id="5a1b8-121">Değer: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="5a1b8-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="5a1b8-122">Anahtar:-İçerik Ekle</span><span class="sxs-lookup"><span data-stu-id="5a1b8-122">Key : Add-Content</span></span>|<span data-ttu-id="5a1b8-123">Değer: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="5a1b8-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="5a1b8-124">Aşağıdaki komut dosyasını bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="5a1b8-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="5a1b8-125">$psOnlineHelp</span></span>
 <span data-ttu-id="5a1b8-126">Bu Yardım konuları konu başlıklarını ve bunların ilişkili dış URL'lerini arasında bağlama duyarlı bir eşleme tutan bir sözlük nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="5a1b8-127">Web üzerinde belirli bir konu için Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="5a1b8-128">Ekleyebilir veya bu listeden konuları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="5a1b8-129">Örnek Çıkış</span><span class="sxs-lookup"><span data-stu-id="5a1b8-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="5a1b8-130">Anahtar:-Bilgisayar Ekle</span><span class="sxs-lookup"><span data-stu-id="5a1b8-130">Key : Add-Computer</span></span>|<span data-ttu-id="5a1b8-131">Değer: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="5a1b8-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="5a1b8-132">Anahtar:-İçerik Ekle</span><span class="sxs-lookup"><span data-stu-id="5a1b8-132">Key : Add-Content</span></span>|<span data-ttu-id="5a1b8-133">Değer: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="5a1b8-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="5a1b8-134">Aşağıdaki komut dosyasını bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="5a1b8-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="5a1b8-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5a1b8-135">See Also</span></span>
- [<span data-ttu-id="5a1b8-136">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a1b8-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
