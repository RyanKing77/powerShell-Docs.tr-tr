---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Diğer Kullanışlı Betik Oluşturma Nesneleri
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: ff494f375c0d43d83b2a067dbe4f2ab35a90d564
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405681"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="452b2-103">Diğer Kullanışlı Betik Oluşturma Nesneleri</span><span class="sxs-lookup"><span data-stu-id="452b2-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="452b2-104">Aşağıdaki nesneler, Windows PowerShell ıse'de betik ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="452b2-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="452b2-105">Olmadıkları parçası **$psISE** hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="452b2-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="452b2-106">Kullanışlı betik oluşturma nesneleri</span><span class="sxs-lookup"><span data-stu-id="452b2-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="452b2-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="452b2-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="452b2-108">Windows PowerShell ISE'de konsol uygulamaları ile nasıl etkileştiğini bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="452b2-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="452b2-109">Bir komut veya kullanıcı etkileşimi gerektiren bir Otomasyon betiği Windows PowerShell konsolundan çalışma şeklini çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="452b2-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="452b2-110">Bu komutları veya betikleri Windows PowerShell ISE komutunu bölmesinde çalışmasını engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="452b2-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="452b2-111">**$PsUnsupportedConsoleApplications** nesne bu tür komutların bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="452b2-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="452b2-112">Bu listede komutları çalıştırmayı denerseniz, bunlar desteklenmez bir ileti alırsınız.</span><span class="sxs-lookup"><span data-stu-id="452b2-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="452b2-113">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="452b2-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="452b2-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="452b2-114">$psLocalHelp</span></span>

<span data-ttu-id="452b2-115">Bağlama duyarlı Yardım konularını ve bunların ilişkili bağlantılarını yerel derlenmiş HTML Yardım dosyasında eşlemesini tutan bir sözlük nesnesi budur.</span><span class="sxs-lookup"><span data-stu-id="452b2-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="452b2-116">Belirli bir konu için yerel Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="452b2-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="452b2-117">Ekleyebilir veya konular bu listeden silin.</span><span class="sxs-lookup"><span data-stu-id="452b2-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="452b2-118">Aşağıdaki kod örneğinde bulunan anahtar-değer çiftleri bazı örnek gösterir `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="452b2-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="452b2-119">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="452b2-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="452b2-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="452b2-120">$psOnlineHelp</span></span>

<span data-ttu-id="452b2-121">Bağlama duyarlı Yardım konuları, konu başlıkları ve bunların ilişkili dış URL'lerini eşlemesini tutan bir sözlük nesnesi budur.</span><span class="sxs-lookup"><span data-stu-id="452b2-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="452b2-122">Web üzerinde belirli bir konu için Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="452b2-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="452b2-123">Ekleyebilir veya konular bu listeden silin.</span><span class="sxs-lookup"><span data-stu-id="452b2-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="452b2-124">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="452b2-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="452b2-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="452b2-125">See Also</span></span>

[<span data-ttu-id="452b2-126">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="452b2-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)