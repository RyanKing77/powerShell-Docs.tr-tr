---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Komutlar hakkında bilgi alma
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: f4238927f10b4204cd3e23f0b0453011f54cb04a
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134019"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="36a60-103">Komutlar hakkında bilgi alma</span><span class="sxs-lookup"><span data-stu-id="36a60-103">Getting information about commands</span></span>

<span data-ttu-id="36a60-104">PowerShell `Get-Command` Geçerli oturumunuzda kullanılabilir komutları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36a60-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="36a60-105">Çalıştırdığınızda `Get-Command` cmdlet'ini aşağıdaki çıktıya benzer bir şey görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="36a60-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="36a60-106">Bu görünümler Cmd.exe Yardım çıktısını gibi çok çıkış: iç komutları tablosal bir özeti.</span><span class="sxs-lookup"><span data-stu-id="36a60-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="36a60-107">Alıntı içinde `Get-Command` komut gösterilen her komut, yukarıda gösterilen çıkış, bir CommandType cmdlet'i vardır.</span><span class="sxs-lookup"><span data-stu-id="36a60-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="36a60-108">Bir cmdlet, PowerShell'in iç komut türüdür.</span><span class="sxs-lookup"><span data-stu-id="36a60-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="36a60-109">Bu tür komutlar gibi kabaca karşılık `dir` ve `cd` bash Kabuk Cmd.exe veya UNIX yerleşik komutlarını ister.</span><span class="sxs-lookup"><span data-stu-id="36a60-109">This type corresponds roughly to commands like `dir` and `cd` in Cmd.exe or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="36a60-110">`Get-Command` Cmdlet'i sahip bir **söz dizimi** her cmdlet'in söz dizimi döndüren parametresi.</span><span class="sxs-lookup"><span data-stu-id="36a60-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="36a60-111">Aşağıdaki örnek söz dizimini alınacağı gösterilmektedir `Get-Help` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="36a60-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="36a60-112">Kullanılabilir komut türüne göre görüntüleme</span><span class="sxs-lookup"><span data-stu-id="36a60-112">Displaying available command by type</span></span>

<span data-ttu-id="36a60-113">`Get-Command` Komut geçerli oturumda yalnızca cmdlet öğelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="36a60-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="36a60-114">PowerShell komutları diğer birçok türde gerçekten destekler:</span><span class="sxs-lookup"><span data-stu-id="36a60-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="36a60-115">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="36a60-115">Aliases</span></span>
- <span data-ttu-id="36a60-116">İşlevler</span><span class="sxs-lookup"><span data-stu-id="36a60-116">Functions</span></span>
- <span data-ttu-id="36a60-117">Betikler</span><span class="sxs-lookup"><span data-stu-id="36a60-117">Scripts</span></span>

<span data-ttu-id="36a60-118">Ayrıca Dış yürütülebilir dosyalar veya kayıtlı dosya türü işleyicisi dosyalar komut olarak sınıflandırılır.</span><span class="sxs-lookup"><span data-stu-id="36a60-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="36a60-119">Tüm komutlar oturumda almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="36a60-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="36a60-120">Bu liste, binlerce öğenin bulunabilir, arama yolunda dış komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="36a60-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="36a60-121">Sınırlı bir komut kümesini aramak daha yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="36a60-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="36a60-122">Yıldız işareti (\*) joker karakter eşleme PowerShell komut satırı bağımsız değişkenlerini için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36a60-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="36a60-123">\* Eşleşme anlamına gelir"bir veya daha fazla herhangi bir karakter".</span><span class="sxs-lookup"><span data-stu-id="36a60-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="36a60-124">Yazabilirsiniz `Get-Command a*` harfi ile başlayan tüm komutları bulmak için "a".</span><span class="sxs-lookup"><span data-stu-id="36a60-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="36a60-125">Joker karakter eşleme cmd.exe içinde, PowerShell'in joker ayrıca bir süre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="36a60-125">Unlike wildcard matching in Cmd.exe, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="36a60-126">Kullanım **CommandType** parametresinin `Get-Command` diğer tür yerel komutları almak için.</span><span class="sxs-lookup"><span data-stu-id="36a60-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="36a60-127">cmdlet'ini çalıştırdığınızda döndürülen çekirdek kaynakları bilgilerini gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36a60-127">cmdlet.</span></span>

<span data-ttu-id="36a60-128">Komutların atanan takma adları olan komut diğer adları almak için aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="36a60-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="36a60-129">Geçerli oturumda işlevleri almak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="36a60-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="36a60-130">PowerShell'in arama yolunda komut dosyaları görüntülemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="36a60-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```