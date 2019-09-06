---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Bilgisayar Durumunu Değiştirme
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386281"
---
# <a name="changing-computer-state"></a><span data-ttu-id="7aea9-103">Bilgisayar Durumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7aea9-103">Changing Computer State</span></span>

<span data-ttu-id="7aea9-104">Windows PowerShell 'de bir bilgisayarı sıfırlamak için, standart bir komut satırı aracı, WMI veya CıM sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aea9-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="7aea9-105">Yalnızca aracı çalıştırmak için Windows PowerShell kullanıyor olsanız da, Windows PowerShell 'de bilgisayarın güç durumunu değiştirme hakkında bilgi edinmek için Windows PowerShell 'de dış araçlarla çalışma hakkındaki önemli ayrıntıların bazıları gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7aea9-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="7aea9-106">Bilgisayarı kilitleme</span><span class="sxs-lookup"><span data-stu-id="7aea9-106">Locking a Computer</span></span>

<span data-ttu-id="7aea9-107">Bir bilgisayarı doğrudan standart kullanılabilir araçlarla kilitlemeye yönelik tek yol, **User32. dll**' de **LockWorkstation ()** işlevini çağırmanız durumunda:</span><span class="sxs-lookup"><span data-stu-id="7aea9-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="7aea9-108">Bu komut, iş istasyonunu hemen kilitler.</span><span class="sxs-lookup"><span data-stu-id="7aea9-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="7aea9-109">Windows yönetim işlevlerinin bir kitaplığı olan User32. dll dosyasını çalıştırmak için Windows dll 'Leri çalıştıran *Rundll32. exe*' yi (ve bunları yinelenen kullanım için kaydeder) kullanır.</span><span class="sxs-lookup"><span data-stu-id="7aea9-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="7aea9-110">Windows XP gibi Hızlı Kullanıcı geçişi etkinken bir iş istasyonunu kilitlerseniz, bilgisayar geçerli kullanıcının ekran koruyucuyu başlatmak yerine Kullanıcı oturum açma ekranını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7aea9-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="7aea9-111">Bir terminal sunucusundaki belirli oturumları kapatmak için **Tsshutdn. exe** komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aea9-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="7aea9-112">Geçerli oturumun oturumu kapatılıyor</span><span class="sxs-lookup"><span data-stu-id="7aea9-112">Logging Off the Current Session</span></span>

<span data-ttu-id="7aea9-113">Yerel sistemdeki bir oturum oturumunu kapatmak için birkaç farklı teknik kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aea9-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="7aea9-114">En basit yol, Uzak Masaüstü/Terminal Hizmetleri komut satırı aracı olan **logoff. exe** ' yi kullanmaktır (Ayrıntılar Için Windows PowerShell isteminde, **logoff/?** yazın).</span><span class="sxs-lookup"><span data-stu-id="7aea9-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="7aea9-115">Geçerli etkin oturumu kapatmak için bağımsız değişken olmadan **logoff** yazın.</span><span class="sxs-lookup"><span data-stu-id="7aea9-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="7aea9-116">**Kapatma. exe** aracını, oturum kapatma seçeneğiyle de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7aea9-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="7aea9-117">Başka bir seçenek de WMI kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7aea9-117">Another option is to use WMI.</span></span> <span data-ttu-id="7aea9-118">Win32_OperatingSystem sınıfında bir Win32Shutdown yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="7aea9-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="7aea9-119">Yöntemi 0 bayrağıyla çağırmak oturumu kapatmayı başlatır:</span><span class="sxs-lookup"><span data-stu-id="7aea9-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="7aea9-120">Daha fazla bilgi edinmek ve Win32Shutdown yönteminin diğer özelliklerini bulmak için MSDN 'de "Win32_OperatingSystem sınıfının Win32Shutdown yöntemi" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="7aea9-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="7aea9-121">Son olarak, WMI yönteminde yukarıda açıklanan şekilde aynı Win32_OperatingSystem sınıfıyla CıM kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aea9-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="7aea9-122">Bilgisayarı kapatma veya yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="7aea9-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="7aea9-123">Bilgisayarları kapatmak ve yeniden başlatmak genellikle aynı türde görevdir.</span><span class="sxs-lookup"><span data-stu-id="7aea9-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="7aea9-124">Bir bilgisayarı kapatmakta olan araçlar, genellikle da yeniden başlatılır ve tam tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7aea9-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="7aea9-125">Windows PowerShell 'den bir bilgisayarı yeniden başlatmak için iki basit seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="7aea9-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="7aea9-126">TSShutdn. exe veya kapatılmasını. exe ' yi uygun bağımsız değişkenlerle kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aea9-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="7aea9-127">**Tsshutdn. exe/?** adresinden ayrıntılı kullanım bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aea9-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="7aea9-128">veya **kapatılacak. exe/?** .</span><span class="sxs-lookup"><span data-stu-id="7aea9-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="7aea9-129">Ayrıca, doğrudan Windows PowerShell 'den de kapalı ve yeniden başlatma işlemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aea9-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="7aea9-130">Bilgisayarı kapatmak için, dur-Computer komutunu kullanın</span><span class="sxs-lookup"><span data-stu-id="7aea9-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="7aea9-131">İşletim sistemini yeniden başlatmak için yeniden Başlat-bilgisayar komutunu kullanın</span><span class="sxs-lookup"><span data-stu-id="7aea9-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="7aea9-132">Bilgisayarın hemen yeniden başlatılmasını zorlamak için-zorlama parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aea9-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
