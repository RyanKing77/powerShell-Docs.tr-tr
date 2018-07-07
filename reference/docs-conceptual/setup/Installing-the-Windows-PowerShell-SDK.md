---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell SDK’sını Yükleme
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893547"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="0a2c6-103">Windows PowerShell SDK’sını Yükleme</span><span class="sxs-lookup"><span data-stu-id="0a2c6-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="0a2c6-104">Aşağıdaki konuda farklı Windows sürümleri üzerinde PowerShell SDK'yı yüklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="0a2c6-105">Windows PowerShell 3.0 yükleme Windows 8 ve Windows Server 2012 için SDK'sı</span><span class="sxs-lookup"><span data-stu-id="0a2c6-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="0a2c6-106">Windows PowerShell 3.0, Windows 8 ve Windows Server 2012 ile otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="0a2c6-107">Ayrıca, indirin ve başvuru bütünleştirilmiş kodları için Windows PowerShell 3.0 Windows 8 SDK'ın bir parçası olarak yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="0a2c6-108">Bu derlemeler cmdlet'leri ve sağlayıcıları ana program için Windows PowerShell 3.0 yazmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="0a2c6-109">Windows 8 için Windows SDK'yı yüklediğinizde, Windows PowerShell derlemeler otomatik olarak başvuru derleme klasöründe yüklendiği `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="0a2c6-110">Daha fazla bilgi için [Windows 8 SDK indirme sitesi](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span><span class="sxs-lookup"><span data-stu-id="0a2c6-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="0a2c6-111">Windows PowerShell kod örnekleri geliştirme Merkezi'nden de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="0a2c6-112">Daha fazla bilgi için masaüstü kod örnek sayfasına bakın [Geliştirme Merkezi sitesi](https://code.msdn.microsoft.com:443/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="0a2c6-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="0a2c6-113">Ayrıca, Windows PowerShell 3.0 geriye dönük olarak uyumludur Windows PowerShell 2.0 SDK kod örnekleri sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="0a2c6-114">Windows PowerShell 2.0 SDK'sını indirme hakkında daha fazla bilgi için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="0a2c6-115">(2.0 kod örnekleri Windows 8 ve Windows PowerShell 3.0 ile uyumlu olsa da, Windows 8 platformu üzerinde Windows PowerShell 2.0 uygulamasını yükleyemezsiniz unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="0a2c6-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="0a2c6-116">Windows PowerShell 3.0 yüklenmesi Windows 7 ve Windows Server 2008 R2 için SDK'sı</span><span class="sxs-lookup"><span data-stu-id="0a2c6-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="0a2c6-117">Otomatik olarak Windows 7 ve Windows Server 2008 R2 PowerShell 2.0 yüklü.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="0a2c6-118">Ayrıca, PowerShell 3.0 Bu sistemlerin tümünde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="0a2c6-119">(Daha fazla bilgi için [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).).</span><span class="sxs-lookup"><span data-stu-id="0a2c6-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="0a2c6-120">Yukarıda açıklandığı gibi Windows 7 ve Windows Server 2008 R2'de Windows 8 SDK'sını yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="0a2c6-121">Windows PowerShell 2.0 yükleme için Windows 7, Vista, XP, Server 2003 ve Server 2008 SDK'sı</span><span class="sxs-lookup"><span data-stu-id="0a2c6-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="0a2c6-122">Windows PowerShell 2.0 SDK'sını cmdlet'leri ve sağlayıcıları barındırma uygulamaları yazmak için gereken başvuru derlemelerini sağlar ve kod yazmaya başladığınızda, başlangıç noktası olarak kullanılacak C# örnek kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="0a2c6-123">Bu SDK'yı yüklemek için bkz [Windows PowerShell 2.0 SDK'sını](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span><span class="sxs-lookup"><span data-stu-id="0a2c6-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="0a2c6-124">Başvuru bütünleştirilmiş kodları</span><span class="sxs-lookup"><span data-stu-id="0a2c6-124">Reference assemblies</span></span>

<span data-ttu-id="0a2c6-125">Başvuru bütünleştirilmiş kodları, varsayılan olarak şu konuma yüklenir: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="0a2c6-126">Windows PowerShell 2.0 derlemeleri karşı derlenmiş kod, Windows PowerShell 1.0 yüklemelerde yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="0a2c6-127">Ancak, Windows PowerShell 1.0 derlemelere karşı derlenmiş kod, Windows PowerShell 2.0 yüklemelerde yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="0a2c6-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0a2c6-128">Samples</span></span>

<span data-ttu-id="0a2c6-129">Kod örnekleri, varsayılan olarak şu konuma yüklenir: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="0a2c6-130">Aşağıdaki bölümlerde, her örnek yapar, kısa bir açıklama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="0a2c6-131">Cmdlet örnekleri</span><span class="sxs-lookup"><span data-stu-id="0a2c6-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="0a2c6-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-132">GetProcessSample01</span></span>

<span data-ttu-id="0a2c6-133">Tüm işlemler yerel bilgisayarda alır basit bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="0a2c6-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-134">GetProcessSample02</span></span>

<span data-ttu-id="0a2c6-135">Cmdlet'e parametre ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="0a2c6-136">Cmdlet'i, bir veya daha fazla işlem adlarını alır ve eşleşen işlem döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="0a2c6-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="0a2c6-137">GetProcessSample03</span></span>

<span data-ttu-id="0a2c6-138">Ardışık düzendeki girişi kabul parametreleri ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="0a2c6-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="0a2c6-139">GetProcessSample04</span></span>

<span data-ttu-id="0a2c6-140">Olmak üzere sonlandırmasız hatalar nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="0a2c6-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="0a2c6-141">GetProcessSample05</span></span>

<span data-ttu-id="0a2c6-142">Belirtilen işlemlerin bir listesini görüntüleme işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="0a2c6-143">SelectObject</span><span class="sxs-lookup"><span data-stu-id="0a2c6-143">SelectObject</span></span>

<span data-ttu-id="0a2c6-144">Yalnızca belirli nesneleri seçmek için bir filtre yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="0a2c6-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="0a2c6-145">SelectString</span></span>

<span data-ttu-id="0a2c6-146">Belirtilen desenle dosyalarını aramak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="0a2c6-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-147">StopProcessSample01</span></span>

<span data-ttu-id="0a2c6-148">Nasıl uygulayacağınızı gösteren bir *PassThru* parametresi ve yapılan çağrılar tarafından kullanıcı geri bildirimi nasıl [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) ve [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="0a2c6-149">Kullanıcının belirttiği *PassThru* nesneyi döndürmek için cmdlet zorlamak istediğinizde parametresi</span><span class="sxs-lookup"><span data-stu-id="0a2c6-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="0a2c6-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-150">StopProcessSample02</span></span>

<span data-ttu-id="0a2c6-151">Belirli bir işlem durdurma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="0a2c6-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="0a2c6-152">StopProcessSample03</span></span>

<span data-ttu-id="0a2c6-153">Joker karakterleri destekleme ve parametreler için diğer ad bildirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="0a2c6-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="0a2c6-154">StopProcessSample04</span></span>

<span data-ttu-id="0a2c6-155">Parametre kümesine nasıl gösterir cmdlet'i, girdi ve nasıl belirtileceğini kullanacak şekilde varsayılan parametre olarak alan nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="0a2c6-156">Uzaktan iletişimini örnekleri</span><span class="sxs-lookup"><span data-stu-id="0a2c6-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="0a2c6-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-157">RemoteRunspace01</span></span>

<span data-ttu-id="0a2c6-158">Uzak bağlantı kurmak için kullanılan bir uzak çalışma alanı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="0a2c6-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="0a2c6-160">Bu havuzu kullanarak aynı anda birden çok komut çalıştırma ve bir uzak çalışma alanı havuzu oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="0a2c6-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-161">Serialization01</span></span>

<span data-ttu-id="0a2c6-162">Mevcut bir .NET sınıfı arayın ve bu sınıfın seçilen genel özelliklerin bilgilerinden serileştirme/seri durumdan çıkarma işlemi korunur emin olmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="0a2c6-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-163">Serialization02</span></span>

<span data-ttu-id="0a2c6-164">Mevcut bir .NET sınıfına bakın ve bilgileri sınıfın genel özelliklerini mevcut olmadığında bu sınıfın örneğini bilgilerinden serileştirme/seri durumundan çıkarma arasında korunmasını sağlayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="0a2c6-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="0a2c6-165">Serialization03</span></span>

<span data-ttu-id="0a2c6-166">Mevcut bir .NET sınıfına bakın ve bu sınıfın ve türetilen sınıfların örnekleri (Canlı .NET nesnelerini rehydrated) durumdan emin emin olmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="0a2c6-167">Olay örnekleri</span><span class="sxs-lookup"><span data-stu-id="0a2c6-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="0a2c6-168">Event01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-168">Event01</span></span>

<span data-ttu-id="0a2c6-169">Bir cmdlet için etkinlik kaydı ObjectEventRegistrationBase türetme tarafından oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="0a2c6-170">Event02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-170">Event02</span></span>

<span data-ttu-id="0a2c6-171">Gösterir nasıl uzak bilgisayarlarda oluşturulan Windows PowerShell olay bildirimleri almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="0a2c6-172">Aracılığıyla kullanıma PSEventReceived olay kullanan [çalışma](/dotnet/api/system.management.automation.runspaces.runspace) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="0a2c6-173">Barındırma uygulaması örnekleri</span><span class="sxs-lookup"><span data-stu-id="0a2c6-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="0a2c6-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-174">Runspace01</span></span>

<span data-ttu-id="0a2c6-175">Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) çalıştırılacak sınıfı [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet'i zaman uyumlu olarak.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="0a2c6-176">[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet döndürür [işlem](https://technet.microsoft.com/library/system.diagnostics.process.aspx) nesneler yerel bilgisayarda çalışan her işlem için.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="0a2c6-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-177">Runspace02</span></span>

<span data-ttu-id="0a2c6-178">Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) çalıştırılacak sınıfı [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) ve [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet'leri zaman uyumlu olarak.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="0a2c6-179">[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet döndürür [işlem](https://technet.microsoft.com/library/system.diagnostics.process.aspx) yerel bilgisayarda çalışan her işlem için nesneleri ve `Sort-Object` nesneleri göre sıralar, [kimliği](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) özellik.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="0a2c6-180">Sonuçları aşağıdaki komutlardan birini kullanarak görüntülenen bir [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) denetimi.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="0a2c6-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="0a2c6-181">Runspace03</span></span>

<span data-ttu-id="0a2c6-182">Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) zaman uyumlu olarak bir betik çalıştırmak için sınıf ve sonlandırıcı olmayan hatalara nasıl ele alınacağını.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="0a2c6-183">Betik işlem adları listesini alır ve ardından bu işlemleri alır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="0a2c6-184">Komut dosyası çalıştırılırken oluşturulan sonlandırmayan hatalar dahil olmak üzere betik sonuçlarını konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="0a2c6-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="0a2c6-185">Runspace04</span></span>

<span data-ttu-id="0a2c6-186">Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) komutlarını çalıştırmak için sınıf ve komutlarını çalıştırırken oluşturulan catch Sonlandırıcı hataları.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="0a2c6-187">İki komutu çalıştırın ve son komut, geçerli olmayan bir parametre bağımsız değişkeni olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="0a2c6-188">Sonuç olarak, hiçbir nesne döndürülür ve bir sonlandırma hatası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="0a2c6-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="0a2c6-189">Runspace05</span></span>

<span data-ttu-id="0a2c6-190">Bir ek bileşenine ekleme işlemi açıklanır bir [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) böylece çalışma açıldığında, ek cmdlet kullanılabilir nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="0a2c6-191">Ek bir Get-Proc cmdlet sağlar (tarafından tanımlanan [GetProcessSample01 örnek](https://technet.microsoft.com/library/ff602028.aspx)) çalıştırılan zaman uyumlu olarak kullanarak bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="0a2c6-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="0a2c6-192">Runspace06</span></span>

<span data-ttu-id="0a2c6-193">Bir modüle ekleneceği gösterilmiştir bir [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) modülü bir çalışma açıldığında yüklenmesi nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="0a2c6-194">Get-Proc cmdlet modülü sağlar (tarafından tanımlanan [GetProcessSample02 örnek](https://technet.microsoft.com/library/ff602027.aspx)) çalıştırılan zaman uyumlu olarak kullanarak bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="0a2c6-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="0a2c6-195">Runspace07</span></span>

<span data-ttu-id="0a2c6-196">Bir çalışma alanı oluşturun ve ardından iki cmdlet kullanarak zaman uyumlu olarak çalıştırmak için bu çalışma alanı kullanma gösteren bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="0a2c6-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="0a2c6-197">Runspace08</span></span>

<span data-ttu-id="0a2c6-198">Komut ve bağımsız değişkenler için işlem hattı eklemeyi gösterir bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne ve zaman uyumlu olarak komutları çalıştırmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="0a2c6-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="0a2c6-199">Runspace09</span></span>

<span data-ttu-id="0a2c6-200">İşlem hattı için bir komut dosyası eklemeyi gösterir bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne ve komut zaman uyumsuz olarak çalıştırmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="0a2c6-201">Olaylar, komut çıktısı işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="0a2c6-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="0a2c6-202">Runspace10</span></span>

<span data-ttu-id="0a2c6-203">Bir varsayılan ilk oturum durumu oluşturulacağını gösterir bir cmdlet'e ekleme [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), ilk oturum durumu kullanan bir çalışma alanı oluşturma ve komutu çalıştırmak amacıyla kullanmak üzere nasıl bir [PowerShell](/dotnet/api/system.management.automation.powershell)nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="0a2c6-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="0a2c6-204">Runspace11</span></span>

<span data-ttu-id="0a2c6-205">Nasıl kullanılacağını gösterir [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) var olan bir cmdlet'i çağırır, ancak kullanılabilir parametreleri kümesini sınırlayan bir ara sunucu komutu oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="0a2c6-206">Ara sunucu komutunu kısıtlı bir çalışma alanı oluşturmak için kullanılan bir ilk oturum durumunu daha sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="0a2c6-207">Bu, kullanıcının yalnızca ara sunucu komutu cmdlet işlevselliğini erişebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="0a2c6-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-208">PowerShell01</span></span>

<span data-ttu-id="0a2c6-209">Kullanarak bir kısıtlı çalışma alanı oluşturma işlemi gösterilmektedir bir [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) nesne.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="0a2c6-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-210">PowerShell02</span></span>

<span data-ttu-id="0a2c6-211">Aynı anda birden çok komut çalıştırmak için bir çalışma alanı havuzu kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="0a2c6-212">Konak örnekleri</span><span class="sxs-lookup"><span data-stu-id="0a2c6-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="0a2c6-213">Host01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-213">Host01</span></span>

<span data-ttu-id="0a2c6-214">Özel bir ana bilgisayar kullanan bir konak uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="0a2c6-215">Özel ana bilgisayarı kullanan bu örnekte bir çalışma alanı oluşturulur ve ardından [PowerShell](/dotnet/api/system.management.automation.powershell) API "çıkış" çağıran bir betik çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="0a2c6-216">Konak uygulama betiği çıktısına arar ve sonuçları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="0a2c6-217">Host02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-217">Host02</span></span>

<span data-ttu-id="0a2c6-218">Özel ana bilgisayar uygulaması ile birlikte Windows PowerShell'i çalışma zamanı kullanan bir ana bilgisayar uygulaması yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="0a2c6-219">Ana bilgisayar uygulaması çalışır Almanca için konak kültürü ayarlar [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet ve aynı sonuçları görüntüler bkz bunları pwrsh.exe ve geçerli veri ve saat sonra yazdırır Almanca kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="0a2c6-220">Host03</span><span class="sxs-lookup"><span data-stu-id="0a2c6-220">Host03</span></span>

<span data-ttu-id="0a2c6-221">Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="0a2c6-222">Host04</span><span class="sxs-lookup"><span data-stu-id="0a2c6-222">Host04</span></span>

<span data-ttu-id="0a2c6-223">Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="0a2c6-224">Bu ana bilgisayar uygulaması birden çok seçenek belirtmesini sağlayan görüntüleme yönergeleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="0a2c6-225">Konak05</span><span class="sxs-lookup"><span data-stu-id="0a2c6-225">Host05</span></span>

<span data-ttu-id="0a2c6-226">Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="0a2c6-227">Ayrıca bu ana bilgisayar uygulaması kullanarak uzak bilgisayarlara çağrıları destekleyen [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) ve [çıkış-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="0a2c6-228">Host06</span><span class="sxs-lookup"><span data-stu-id="0a2c6-228">Host06</span></span>

<span data-ttu-id="0a2c6-229">Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="0a2c6-230">Ayrıca, bu örnek, kullanıcı tarafından girilen metin rengi belirtmek için belirteç Oluşturucu API kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="0a2c6-231">Sağlayıcısı örnekleri</span><span class="sxs-lookup"><span data-stu-id="0a2c6-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="0a2c6-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="0a2c6-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="0a2c6-233">Doğrudan öğesinden türetilen bir sağlayıcı sınıfı bildirmek gösterilmektedir [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="0a2c6-234">Burada yalnızca bütünlük açısından dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="0a2c6-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="0a2c6-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="0a2c6-236">Üzerine yazma işlemi gösterilmektedir [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) ve [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) çağrıları desteklemek için yöntemler `New-PSDrive` ve `Remove-PSDrive` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="0a2c6-237">Bu örnekteki sağlayıcı sınıfın türetildiği [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="0a2c6-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="0a2c6-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="0a2c6-239">Üzerine yazma işlemi gösterilmektedir [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) ve [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) çağrıları desteklemek için yöntemler `Get-Item` ve `Set-Item` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="0a2c6-240">Bu örnekteki sağlayıcı sınıfın türetildiği [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="0a2c6-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="0a2c6-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="0a2c6-242">Çağrıları desteklemek için kapsayıcı yöntemleri üzerine gösterilmektedir `Copy-Item`, `Get-ChildItem`, `New-Item`, ve `Remove-Item` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="0a2c6-243">Veri deposu kapsayıcılar olan öğeleri içerdiğinde, bu yöntemleri uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="0a2c6-244">Ortak bir üst öğe altında bir alt öğe grubunu bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="0a2c6-245">Bu örnekteki sağlayıcı sınıfın türetildiği [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="0a2c6-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="0a2c6-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="0a2c6-247">Çağrıları desteklemek için kapsayıcı yöntemleri üzerine gösterilmektedir `Move-Item` ve `Join-Path` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="0a2c6-248">Bu yöntemler, bir kapsayıcı içindeki öğeleri taşımak gerektiğinde ve veri depolama alanı iç içe geçmiş kapsayıcılar varsa uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="0a2c6-249">Bu örnekteki sağlayıcı sınıfın türetildiği [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="0a2c6-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="0a2c6-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="0a2c6-251">Çağrıları desteklemek için içerik yöntemleri üzerine gösterilmektedir `Clear-Content`, `Get-Content`, ve `Set-Content` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="0a2c6-252">Veri deposundaki öğelerinin içeriğini yönetmek gerektiğinde bu yöntemleri uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="0a2c6-253">Bu örnekteki sağlayıcı sınıfın türetildiği [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) sınıf ve uyguladığı [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0a2c6-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>