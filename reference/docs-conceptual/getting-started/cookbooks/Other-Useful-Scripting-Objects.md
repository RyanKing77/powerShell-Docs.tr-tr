---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Diğer Kullanışlı Betik Oluşturma Nesneleri
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 2ae9bc1864daedbcb0070c5f3862a6c98f8db2d4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893289"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="ce376-103">Diğer Kullanışlı Betik Oluşturma Nesneleri</span><span class="sxs-lookup"><span data-stu-id="ce376-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="ce376-104">Aşağıdaki nesneler, Windows PowerShell ıse'de betik ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce376-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="ce376-105">Olmadıkları parçası **$psISE** hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="ce376-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="ce376-106">Kullanışlı betik oluşturma nesneleri</span><span class="sxs-lookup"><span data-stu-id="ce376-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="ce376-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="ce376-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="ce376-108">Windows PowerShell ISE'de konsol uygulamaları ile nasıl etkileştiğini bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="ce376-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="ce376-109">Bir komut veya kullanıcı etkileşimi gerektiren bir Otomasyon betiği Windows PowerShell konsolundan çalışma şeklini çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ce376-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="ce376-110">Bu komutları veya betikleri Windows PowerShell ISE komutunu bölmesinde çalışmasını engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce376-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="ce376-111">**$PsUnsupportedConsoleApplications** nesne bu tür komutların bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="ce376-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="ce376-112">Bu listede komutları çalıştırmayı denerseniz, bunlar desteklenmez bir ileti alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ce376-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="ce376-113">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="ce376-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="ce376-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="ce376-114">$psLocalHelp</span></span>

<span data-ttu-id="ce376-115">Bağlama duyarlı Yardım konularını ve bunların ilişkili bağlantılarını yerel derlenmiş HTML Yardım dosyasında eşlemesini tutan bir sözlük nesnesi budur.</span><span class="sxs-lookup"><span data-stu-id="ce376-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="ce376-116">Belirli bir konu için yerel Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce376-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="ce376-117">Ekleyebilir veya konular bu listeden silin.</span><span class="sxs-lookup"><span data-stu-id="ce376-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="ce376-118">Aşağıdaki kod örneğinde bulunan anahtar-değer çiftleri bazı örnek gösterir `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="ce376-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="pslocalhelp-sample-output"></a><span data-ttu-id="ce376-119">$psLocalHelp örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="ce376-119">$psLocalHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="ce376-120">Anahtar:-Bilgisayar Ekle</span><span class="sxs-lookup"><span data-stu-id="ce376-120">Key : Add-Computer</span></span>|<span data-ttu-id="ce376-121">Değer: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="ce376-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="ce376-122">Anahtar:-İçerik Ekle</span><span class="sxs-lookup"><span data-stu-id="ce376-122">Key : Add-Content</span></span>|<span data-ttu-id="ce376-123">Değer: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="ce376-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="ce376-124">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="ce376-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="ce376-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="ce376-125">$psOnlineHelp</span></span>

<span data-ttu-id="ce376-126">Bağlama duyarlı Yardım konuları, konu başlıkları ve bunların ilişkili dış URL'lerini eşlemesini tutan bir sözlük nesnesi budur.</span><span class="sxs-lookup"><span data-stu-id="ce376-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="ce376-127">Web üzerinde belirli bir konu için Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce376-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="ce376-128">Ekleyebilir veya konular bu listeden silin.</span><span class="sxs-lookup"><span data-stu-id="ce376-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

## <a name="psonilnehelp-sample-output"></a><span data-ttu-id="ce376-129">$psOnilneHelp örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="ce376-129">$psOnilneHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="ce376-130">Anahtar:-Bilgisayar Ekle</span><span class="sxs-lookup"><span data-stu-id="ce376-130">Key : Add-Computer</span></span>|<span data-ttu-id="ce376-131">Değer: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="ce376-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="ce376-132">Anahtar:-İçerik Ekle</span><span class="sxs-lookup"><span data-stu-id="ce376-132">Key : Add-Content</span></span>|<span data-ttu-id="ce376-133">Değer: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="ce376-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

<span data-ttu-id="ce376-134">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="ce376-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="ce376-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ce376-135">See Also</span></span>

[<span data-ttu-id="ce376-136">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="ce376-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)