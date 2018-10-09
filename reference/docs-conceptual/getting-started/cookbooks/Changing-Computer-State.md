---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bilgisayar Durumunu Değiştirme
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: f2fadcedaeddfa6f8b9dd4d70738ee062b907d61
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851092"
---
# <a name="changing-computer-state"></a><span data-ttu-id="be8f5-103">Bilgisayar Durumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="be8f5-103">Changing Computer State</span></span>

<span data-ttu-id="be8f5-104">Bir bilgisayar Windows PowerShell'de sıfırlamak için standart bir komut satırı aracını veya WMI sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="be8f5-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="be8f5-105">Yalnızca aracı çalıştırmak için Windows PowerShell kullanarak karşın, Windows PowerShell'de bir bilgisayarın güç durumu değiştirmek öğrenme Windows PowerShell'de dış araçları ile çalışma hakkında önemli ayrıntıları bazıları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="be8f5-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="be8f5-106">Bilgisayarı kilitleme</span><span class="sxs-lookup"><span data-stu-id="be8f5-106">Locking a Computer</span></span>

<span data-ttu-id="be8f5-107">Standart kullanılabilir araçları ile doğrudan bir bilgisayarı kilitlemek için tek yolu çağırmaktır **LockWorkstation() işlevini** işlevi **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="be8f5-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="be8f5-108">Bu komut, hemen iş istasyonu kilitler.</span><span class="sxs-lookup"><span data-stu-id="be8f5-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="be8f5-109">Kullandığı *rundll32.exe*, hangi Windows DLL'leri çalışır (ve yinelemeli olarak kullanmak için kendi kitaplıkları kaydeder) user32.dll, Windows Yönetim işlevlerini içeren bir kitaplık çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="be8f5-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="be8f5-110">Ne zaman hızlı kullanıcı değiştirme etkinken Windows XP'de geçerli kullanıcının ekran koruyucu başlangıç yerine kullanıcı oturum açma ekranında bilgisayarı görüntüler gibi bir iş istasyonu kilitleyin.</span><span class="sxs-lookup"><span data-stu-id="be8f5-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="be8f5-111">Belirli bir Terminal sunucusu oturumları kapatmak için kullanın **tsshutdn.exe** komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="be8f5-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="be8f5-112">Geçerli oturumu oturumunu kapatma</span><span class="sxs-lookup"><span data-stu-id="be8f5-112">Logging Off the Current Session</span></span>

<span data-ttu-id="be8f5-113">Yerel sistem hakkındaki oturumu oturumunu için birkaç farklı teknikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be8f5-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="be8f5-114">En basit yolu Uzak Masaüstü/Terminal Hizmetleri komut satırı aracını kullanmaktır **logoff.exe** (Ayrıntılar için Windows PowerShell komut isteminde yazın **kapatma /?**).</span><span class="sxs-lookup"><span data-stu-id="be8f5-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="be8f5-115">Geçerli etkin oturumu için şunu yazın **kapatma** bağımsız değişken olmadan.</span><span class="sxs-lookup"><span data-stu-id="be8f5-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="be8f5-116">Ayrıca **shutdown.exe** aracı ile oturum kapatma seçeneği:</span><span class="sxs-lookup"><span data-stu-id="be8f5-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="be8f5-117">Üçüncü bir seçenek WMI kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="be8f5-117">A third option is to use WMI.</span></span> <span data-ttu-id="be8f5-118">Win32_OperatingSystem sınıfını Win32Shutdown yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="be8f5-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="be8f5-119">0 bayrağıyla metodu çağrılırken, oturum kapatma başlatır:</span><span class="sxs-lookup"><span data-stu-id="be8f5-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="be8f5-120">Daha fazla bilgi almak ve diğer özellikleri Win32Shutdown yöntemin bulmak için "Win32Shutdown yöntemi, Win32_OperatingSystem sınıfını" MSDN'de bakın.</span><span class="sxs-lookup"><span data-stu-id="be8f5-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="be8f5-121">Kapatma veya bir bilgisayar yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="be8f5-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="be8f5-122">Bilgisayarları yeniden başlatma ve kapatma genellikle aynı görevi türleridir.</span><span class="sxs-lookup"><span data-stu-id="be8f5-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="be8f5-123">Bir bilgisayarı Araçlar genellikle yeniden başlatılacak, de- ve bunun tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="be8f5-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="be8f5-124">Windows powershell'den bilgisayarı yeniden başlatmak için iki basit seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="be8f5-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="be8f5-125">Tsshutdn.exe ya da Shutdown.exe uygun bağımsız değişkenlerle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="be8f5-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="be8f5-126">Ayrıntılı kullanım bilgilerini alabileceğiniz **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="be8f5-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="be8f5-127">veya **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="be8f5-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="be8f5-128">Kapatma gerçekleştirme ve işlemleri de Windows PowerShell üzerinden doğrudan yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="be8f5-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="be8f5-129">Bilgisayarı kapatmak için Stop-Computer komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="be8f5-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="be8f5-130">İşletim sistemi yeniden başlatmak için Restart-Computer komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="be8f5-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="be8f5-131">Bir bilgisayarı hemen yeniden zorlamak için kullanın - Force parametresini.</span><span class="sxs-lookup"><span data-stu-id="be8f5-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
