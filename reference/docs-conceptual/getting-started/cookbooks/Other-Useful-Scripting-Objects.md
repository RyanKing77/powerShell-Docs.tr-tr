---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Diğer Kullanışlı Betik Oluşturma Nesneleri
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 04e94f858b568928b3910dd0ee85a912a6afc264
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268509"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="54549-103">Diğer Kullanışlı Betik Oluşturma Nesneleri</span><span class="sxs-lookup"><span data-stu-id="54549-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="54549-104">Aşağıdaki nesneler, Windows PowerShell ıse'de betik ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="54549-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="54549-105">Olmadıkları parçası **$psISE** hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="54549-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="54549-106">Kullanışlı betik oluşturma nesneleri</span><span class="sxs-lookup"><span data-stu-id="54549-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="54549-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="54549-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="54549-108">Windows PowerShell ISE'de konsol uygulamaları ile nasıl etkileştiğini bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="54549-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="54549-109">Bir komut veya kullanıcı etkileşimi gerektiren bir Otomasyon betiği Windows PowerShell konsolundan çalışma şeklini çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="54549-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="54549-110">Bu komutları veya betikleri Windows PowerShell ISE komutunu bölmesinde çalışmasını engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54549-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="54549-111">**$PsUnsupportedConsoleApplications** nesne bu tür komutların bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="54549-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="54549-112">Bu listede komutları çalıştırmayı denerseniz, bunlar desteklenmez bir ileti alırsınız.</span><span class="sxs-lookup"><span data-stu-id="54549-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="54549-113">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="54549-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="54549-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="54549-114">$psLocalHelp</span></span>

<span data-ttu-id="54549-115">Bağlama duyarlı Yardım konularını ve bunların ilişkili bağlantılarını yerel derlenmiş HTML Yardım dosyasında eşlemesini tutan bir sözlük nesnesi budur.</span><span class="sxs-lookup"><span data-stu-id="54549-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="54549-116">Belirli bir konu için yerel Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54549-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="54549-117">Ekleyebilir veya konular bu listeden silin.</span><span class="sxs-lookup"><span data-stu-id="54549-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="54549-118">Aşağıdaki kod örneğinde bulunan anahtar-değer çiftleri bazı örnek gösterir `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="54549-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

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

<span data-ttu-id="54549-119">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="54549-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="54549-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="54549-120">$psOnlineHelp</span></span>

<span data-ttu-id="54549-121">Bağlama duyarlı Yardım konuları, konu başlıkları ve bunların ilişkili dış URL'lerini eşlemesini tutan bir sözlük nesnesi budur.</span><span class="sxs-lookup"><span data-stu-id="54549-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="54549-122">Web üzerinde belirli bir konu için Yardım bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54549-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="54549-123">Ekleyebilir veya konular bu listeden silin.</span><span class="sxs-lookup"><span data-stu-id="54549-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="54549-124">Aşağıdaki betik, bir giriş listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="54549-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="54549-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="54549-125">See Also</span></span>

[<span data-ttu-id="54549-126">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="54549-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)