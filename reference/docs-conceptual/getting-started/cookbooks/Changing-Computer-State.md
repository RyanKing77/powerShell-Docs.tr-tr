---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bilgisayar Durumunu Değiştirme
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251526"
---
# <a name="changing-computer-state"></a><span data-ttu-id="638a4-103">Bilgisayar Durumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="638a4-103">Changing Computer State</span></span>

<span data-ttu-id="638a4-104">Bir bilgisayarı Windows PowerShell'de sıfırlamak için standart bir komut satırı aracını veya WMI sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="638a4-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="638a4-105">Yalnızca aracı çalıştırmak için Windows PowerShell kullanarak karşın, Windows PowerShell'de bilgisayarın güç durumunu değiştirmek öğrenme bazı Windows PowerShell'de dış araçları ile çalışma hakkında önemli ayrıntıları gösterir.</span><span class="sxs-lookup"><span data-stu-id="638a4-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="638a4-106">Bilgisayarı kilitleme</span><span class="sxs-lookup"><span data-stu-id="638a4-106">Locking a Computer</span></span>

<span data-ttu-id="638a4-107">Standart mevcut araçlar ile doğrudan bilgisayarı kilitlemek için tek yolu çağırmaktır **LockWorkstation() işlevini** işlevi **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="638a4-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="638a4-108">Bu komut, iş istasyonu hemen kilitler.</span><span class="sxs-lookup"><span data-stu-id="638a4-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="638a4-109">Kullandığı *rundll32.exe*, hangi Windows DLL'leri çalışır (ve yinelemeli olarak kullanmak için kendi kitaplıkları kaydeder) user32.dll, bir kitaplık Windows Yönetim işlevlerini çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="638a4-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="638a4-110">Ne zaman hızlı kullanıcı değiştirme etkinken Windows XP'de, geçerli kullanıcının koruyucu başlatmak yerine kullanıcı oturum açma ekranı bilgisayar görüntüler gibi bir iş istasyonu kilitleyin.</span><span class="sxs-lookup"><span data-stu-id="638a4-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="638a4-111">Terminal sunucusu üzerinde belirli oturumları kapatmak üzere kullanmak **tsshutdn.exe** komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="638a4-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="638a4-112">Oturumunu geçerli oturumu kapatma</span><span class="sxs-lookup"><span data-stu-id="638a4-112">Logging Off the Current Session</span></span>

<span data-ttu-id="638a4-113">Yerel sistemde oturum oturumunu için birçok farklı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="638a4-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="638a4-114">En basit yolu Uzak Masaüstü/Terminal Hizmetleri komut satırı aracını kullanmaktır **logoff.exe** (Ayrıntılar için Windows PowerShell komut isteminde yazın **kapatma /?**).</span><span class="sxs-lookup"><span data-stu-id="638a4-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="638a4-115">Geçerli etkin oturumu için şunu yazın **kapatma** bağımsız değişken içermeyen.</span><span class="sxs-lookup"><span data-stu-id="638a4-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="638a4-116">Aynı zamanda **shutdown.exe** , kapatma seçeneğini aracıyla:</span><span class="sxs-lookup"><span data-stu-id="638a4-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="638a4-117">WMI kullanan üçüncü bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="638a4-117">A third option is to use WMI.</span></span> <span data-ttu-id="638a4-118">Win32_OperatingSystem sınıfını Win32Shutdown yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="638a4-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="638a4-119">0 bayrağı yönteminin çağrılması kapatma başlatır:</span><span class="sxs-lookup"><span data-stu-id="638a4-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="638a4-120">Daha fazla bilgi için ve diğer özellikleri Win32Shutdown yönteminin bulmak için "Win32Shutdown yöntemi, Win32_OperatingSystem sınıfında" MSDN bakın.</span><span class="sxs-lookup"><span data-stu-id="638a4-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="638a4-121">Kapatma veya bir bilgisayar yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="638a4-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="638a4-122">Kapatma ve bilgisayarları yeniden genellikle aynı görev türleridir.</span><span class="sxs-lookup"><span data-stu-id="638a4-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="638a4-123">Bir bilgisayarı Araçlar genellikle yeniden onu da — tersi.</span><span class="sxs-lookup"><span data-stu-id="638a4-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="638a4-124">Windows PowerShell bilgisayardan yeniden başlatmak için kolay iki seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="638a4-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="638a4-125">Tsshutdn.exe veya Shutdown.exe uygun bağımsız değişkenlerle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="638a4-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="638a4-126">Ayrıntılı kullanım bilgilerini alabilir **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="638a4-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="638a4-127">veya **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="638a4-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="638a4-128">Ayrıca, kapatma gerçekleştirmek ve Windows PowerShell doğrudan işlemlerinden yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="638a4-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="638a4-129">Bilgisayarı kapatmak için bilgisayarı yeniden Başlat komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="638a4-129">To shut down the computer, use the restart-computer command</span></span>

```powershell
stop-computer
```

<span data-ttu-id="638a4-130">İşletim sistemi yeniden başlatmak için bilgisayarı yeniden Başlat komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="638a4-130">To restart the operating system, use the restart-computer command</span></span>

```powershell
restart-computer
```
