---
ms.date: 09/09/2019
keywords: PowerShell, cmdlet
title: Ek 1 Uyumluluk Takma Adları
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848171"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="af13d-103">Ek 1-uyumluluk diğer adları</span><span class="sxs-lookup"><span data-stu-id="af13d-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="af13d-104">PowerShell, **UNIX** ve **cmd. exe** kullanıcılarının tanıdık komutları kullanmasına izin veren birkaç diğer ad içerir.</span><span class="sxs-lookup"><span data-stu-id="af13d-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="af13d-105">Komutlar ve ilgili PowerShell cmdlet 'i ve PowerShell diğer adı aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="af13d-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="af13d-106">cmd. exe komutu</span><span class="sxs-lookup"><span data-stu-id="af13d-106">cmd.exe command</span></span>|<span data-ttu-id="af13d-107">UNIX komutu</span><span class="sxs-lookup"><span data-stu-id="af13d-107">UNIX command</span></span>|<span data-ttu-id="af13d-108">PowerShell cmdlet 'i</span><span class="sxs-lookup"><span data-stu-id="af13d-108">PowerShell cmdlet</span></span>|<span data-ttu-id="af13d-109">PowerShell diğer adı</span><span class="sxs-lookup"><span data-stu-id="af13d-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="af13d-110">**CLS**</span><span class="sxs-lookup"><span data-stu-id="af13d-110">**cls**</span></span>|<span data-ttu-id="af13d-111">**lediğiniz**</span><span class="sxs-lookup"><span data-stu-id="af13d-111">**clear**</span></span>|<span data-ttu-id="af13d-112">`Clear-Host`çalışmayacaktır</span><span class="sxs-lookup"><span data-stu-id="af13d-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="af13d-113">**kopya**</span><span class="sxs-lookup"><span data-stu-id="af13d-113">**copy**</span></span>|<span data-ttu-id="af13d-114">**'s**</span><span class="sxs-lookup"><span data-stu-id="af13d-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="af13d-115">**öğesini**</span><span class="sxs-lookup"><span data-stu-id="af13d-115">**dir**</span></span>|<span data-ttu-id="af13d-116">**çıkar**</span><span class="sxs-lookup"><span data-stu-id="af13d-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="af13d-117">**type**</span><span class="sxs-lookup"><span data-stu-id="af13d-117">**type**</span></span>|<span data-ttu-id="af13d-118">**kedi**</span><span class="sxs-lookup"><span data-stu-id="af13d-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="af13d-119">**geçiş**</span><span class="sxs-lookup"><span data-stu-id="af13d-119">**move**</span></span>|<span data-ttu-id="af13d-120">**k**</span><span class="sxs-lookup"><span data-stu-id="af13d-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="af13d-121">**MD**</span><span class="sxs-lookup"><span data-stu-id="af13d-121">**md**</span></span>|<span data-ttu-id="af13d-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="af13d-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="af13d-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="af13d-123">**pushd**</span></span>|<span data-ttu-id="af13d-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="af13d-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="af13d-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="af13d-125">**popd**</span></span>|<span data-ttu-id="af13d-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="af13d-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="af13d-127">**del**, **Erase**, **RD**, **RMI**</span><span class="sxs-lookup"><span data-stu-id="af13d-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="af13d-128">**'yi**</span><span class="sxs-lookup"><span data-stu-id="af13d-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="af13d-129">**Ren**</span><span class="sxs-lookup"><span data-stu-id="af13d-129">**ren**</span></span>|<span data-ttu-id="af13d-130">**k**</span><span class="sxs-lookup"><span data-stu-id="af13d-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="af13d-131">**CD**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="af13d-131">**cd**, **chdir**</span></span>|<span data-ttu-id="af13d-132">**CD**</span><span class="sxs-lookup"><span data-stu-id="af13d-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="af13d-133">PowerShell diğer adlarını bulmak için [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet 'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="af13d-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="af13d-134">Bir cmdlet 'in diğer adlarını göstermek için, **tanım** parametresini kullanın ve cmdlet adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="af13d-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="af13d-135">Ya da diğer adın cmdlet adını bulmak için **ad** parametresini kullanın ve diğer adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="af13d-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
