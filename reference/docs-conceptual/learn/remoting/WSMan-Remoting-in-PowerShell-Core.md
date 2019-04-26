---
title: PowerShell Core’da WS-Management (WSMan) Uzaktan İletişimi
description: PowerShell core'da WSMan kullanarak uzaktan iletişim
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058888"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="681e1-103">PowerShell Core’da WS-Management (WSMan) Uzaktan İletişimi</span><span class="sxs-lookup"><span data-stu-id="681e1-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="681e1-104">Bir uzak uç noktası oluşturmaya ilişkin yönergeler</span><span class="sxs-lookup"><span data-stu-id="681e1-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="681e1-105">Bir eklenti WinRM Windows PowerShell Core paketi içerir (`pwrshplugin.dll`) ve bir yükleme komut dosyası (`Install-PowerShellRemoting.ps1`) içinde `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="681e1-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="681e1-106">Bu dosyalar, uç nokta belirtildiğinde gelen PowerShell uzak bağlantıları kabul etmek üzere PowerShell etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="681e1-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="681e1-107">Motivasyon</span><span class="sxs-lookup"><span data-stu-id="681e1-107">Motivation</span></span>

<span data-ttu-id="681e1-108">PowerShell yüklemesi kullanarak uzak bilgisayarlarla PowerShell oturumları kurup `New-PSSession` ve `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="681e1-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="681e1-109">Gelen PowerShell uzak bağlantıları kabul etmek üzere etkinleştirmek için kullanıcı bir WinRM uzaktan iletişim uç noktası oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="681e1-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="681e1-110">Bu kullanıcı WinRM uç nokta oluşturmak için Yükle-PowerShellRemoting.ps1 çalıştığı bir açık katılımı senaryodur.</span><span class="sxs-lookup"><span data-stu-id="681e1-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="681e1-111">Biz ek işlevsellik eklemek kadar yükleme komut dosyasını kısa vadeli bir çözüm olan `Enable-PSRemoting` aynı eylemi gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="681e1-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="681e1-112">Daha fazla ayrıntı için lütfen sorun bakın [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="681e1-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="681e1-113">Betik eylemleri</span><span class="sxs-lookup"><span data-stu-id="681e1-113">Script Actions</span></span>

<span data-ttu-id="681e1-114">Komut dosyası</span><span class="sxs-lookup"><span data-stu-id="681e1-114">The script</span></span>

1. <span data-ttu-id="681e1-115">İçinde eklenti için bir dizin oluşturur. `$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="681e1-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="681e1-116">Pwrshplugin.dll o konuma kopyalar.</span><span class="sxs-lookup"><span data-stu-id="681e1-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="681e1-117">Bir yapılandırma dosyası oluşturur</span><span class="sxs-lookup"><span data-stu-id="681e1-117">Generates a configuration file</span></span>
1. <span data-ttu-id="681e1-118">WinRM ile bu eklenti kayıtları</span><span class="sxs-lookup"><span data-stu-id="681e1-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="681e1-119">Kayıt</span><span class="sxs-lookup"><span data-stu-id="681e1-119">Registration</span></span>

<span data-ttu-id="681e1-120">Betik, bir yönetici düzeyinde PowerShell oturumu ve iki modda çalışan içinde yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="681e1-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="681e1-121">Bunu kaydolacak PowerShell örneği tarafından yürütülen</span><span class="sxs-lookup"><span data-stu-id="681e1-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="681e1-122">Başka bir PowerShell örneği, kaydolacak örneği adına yürüten</span><span class="sxs-lookup"><span data-stu-id="681e1-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="681e1-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="681e1-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="681e1-124">**NOT:** Uzak Kayıt betiği, tüm PSRP oturumlarına hemen komut dosyası çalıştırıldıktan sonra sona erecek şekilde WinRM, yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="681e1-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="681e1-125">Uzak oturum sırasında çalıştırırsanız, bu bağlantı sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="681e1-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="681e1-126">Yeni uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="681e1-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="681e1-127">Yeni PowerShell uç noktası için bir PowerShell oturumu belirterek oluşturun `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="681e1-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="681e1-128">Yukarıdaki örnekte PowerShell örneğine bağlanmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="681e1-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="681e1-129">Unutmayın `New-PSSession` ve `Enter-PSSession` belirtmeyin çağrılarını `-ConfigurationName` varsayılan PowerShell uç noktası hedeflediğini `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="681e1-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>