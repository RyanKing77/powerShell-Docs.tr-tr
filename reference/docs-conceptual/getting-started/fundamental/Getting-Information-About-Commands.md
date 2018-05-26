---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Komutlar Hakkında Bilgi Alma
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: c51579fe2cdf4f2a0d3248d1aaf3f1f9cac83868
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="f748c-103">Komutlar Hakkında Bilgi Alma</span><span class="sxs-lookup"><span data-stu-id="f748c-103">Getting Information About Commands</span></span>
<span data-ttu-id="f748c-104">Windows PowerShell `Get-Command` cmdlet'i Geçerli oturumunuzda kullanılabilir tüm komutları alır.</span><span class="sxs-lookup"><span data-stu-id="f748c-104">The Windows PowerShell `Get-Command` cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="f748c-105">Yazdığınızda `Get-Command` bir PowerShell komut isteminde, aşağıdakine benzer bir çıktı göreceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f748c-105">When you type `Get-Command` at a PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="f748c-106">Bu görünüm Cmd.exe Yardım çıktısı gibi çok çıktı: iç komutları tablo özetini.</span><span class="sxs-lookup"><span data-stu-id="f748c-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="f748c-107">Alıntı içinde **Get-Command** yukarıda gösterilen her komut gösterilen çıktıyı içerir, bir CommandType Cmdlet komutu.</span><span class="sxs-lookup"><span data-stu-id="f748c-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="f748c-108">Windows PowerShell'in iç komut türü - kabaca için karşılık gelen bir cmdlet'tir **dir** ve **cd** komutları Cmd.exe ve UNIX Kabukları BASH gibi öğelerin.</span><span class="sxs-lookup"><span data-stu-id="f748c-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="f748c-109">Çıktısı olarak `Get-Command` komut, tüm tanımları bitiş PowerShell tüm içeriği görüntülenemiyor göstermek için üç nokta ile (...) kullanılabilir alanı.</span><span class="sxs-lookup"><span data-stu-id="f748c-109">In the output of the `Get-Command` command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="f748c-110">Windows PowerShell çıkış görüntülediğinde, çıktı metin olarak biçimlendirir ve düzgün bir şekilde penceresine sığacak veri olmak için düzenler.</span><span class="sxs-lookup"><span data-stu-id="f748c-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="f748c-111">Biz bu konuda daha sonra bölümünde biçimlendiricileri üzerinde konuşur.</span><span class="sxs-lookup"><span data-stu-id="f748c-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="f748c-112">`Get-Command` Cmdlet sahip bir **sözdizimi** her cmdlet sözdizimi alır parametresi.</span><span class="sxs-lookup"><span data-stu-id="f748c-112">The `Get-Command` cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="f748c-113">Get-Help cmdlet sözdizimi almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f748c-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

```
Get-Command Get-Help -Syntax

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="f748c-114">Kullanılabilir komut türlerinden görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f748c-114">Displaying Available Command Types</span></span>
<span data-ttu-id="f748c-115">**Get-Command** komutu, Windows PowerShell içinde kullanılabilir olan her komut listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="f748c-115">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="f748c-116">Bunun yerine, **Get-Command** komutu geçerli oturumdaki yalnızca cmdlet'leri listeler.</span><span class="sxs-lookup"><span data-stu-id="f748c-116">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="f748c-117">Windows PowerShell gerçekte birkaç komut türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f748c-117">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="f748c-118">Windows PowerShell Kullanıcı Kılavuzu'nda ayrıntılı açıklanmamaktadır diğer adları, işlevleri ve komut dosyaları da Windows PowerShell komutları, ancak.</span><span class="sxs-lookup"><span data-stu-id="f748c-118">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="f748c-119">Yürütülebilir dosya veya bir kayıtlı dosya türü işleyicisi olan dış dosyalar da komutları olarak sınıflandırılır.</span><span class="sxs-lookup"><span data-stu-id="f748c-119">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="f748c-120">Tüm komutlar oturumda almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="f748c-120">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="f748c-121">Bu liste, arama yolunuzda dış dosyalar içerdiğinden, binlerce öğeye içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f748c-121">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="f748c-122">Azaltılmış bir grup komutları aramak daha kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f748c-122">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="f748c-123">Diğer türleri yerel komutları almak için **CommandType** parametresinin `Get-Command` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="f748c-123">To get native commands of other types, use the **CommandType** parameter of the `Get-Command` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f748c-124">Yıldız işareti (\*) joker karakter eşleştirme Windows PowerShell komut bağımsız değişkenleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f748c-124">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="f748c-125">\* "Eşleştirilmez ve bir veya daha fazla herhangi bir karakter".</span><span class="sxs-lookup"><span data-stu-id="f748c-125">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="f748c-126">Yazabilirsiniz `Get-Command a*` harfiyle başlayan tüm komutları bulmak için "a".</span><span class="sxs-lookup"><span data-stu-id="f748c-126">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="f748c-127">Joker karakter cmd.exe eşleştirme Windows PowerShell'in joker ayrıca bir süre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="f748c-127">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="f748c-128">Atanan takma adlar komutların olan komut diğer adları almak için aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="f748c-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="f748c-129">Geçerli oturumdaki işlevleri almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="f748c-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="f748c-130">Windows PowerShell'in arama yolunda komut dosyalarını görüntülemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="f748c-130">To display scripts in Windows PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
