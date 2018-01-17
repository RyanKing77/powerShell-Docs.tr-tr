---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC kaynakları hata ayıklama"
ms.openlocfilehash: 35eb990705bab8190172df899c64c9f34452aa4b
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="4c006-103">DSC kaynakları hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4c006-103">Debugging DSC resources</span></span>

> <span data-ttu-id="4c006-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4c006-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4c006-105">PowerShell 5. 0'da, istenen durum yapılandırma (DSC kaynağı bir yapılandırma uygulanması gibi hata ayıklamak izin veren DSC içinde) yeni bir özellik sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="4c006-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="4c006-106">DSC hata ayıklamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4c006-106">Enabling DSC debugging</span></span>
<span data-ttu-id="4c006-107">Bir kaynak ayıklayabilirsiniz önce çağırarak hata ayıklamayı etkinleştirmek sahip [etkinleştir DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4c006-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) cmdlet.</span></span> <span data-ttu-id="4c006-108">Bu cmdlet zorunlu bir parametre alır **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="4c006-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span> 

<span data-ttu-id="4c006-109">Hata ayıklama için bir çağrı sonucunu bakarak etkinleştirildiğini doğrulayın [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="4c006-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).</span></span>

<span data-ttu-id="4c006-110">Aşağıdaki PowerShell çıkış hata ayıklamasını etkinleştirme sonucunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="4c006-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="4c006-111">Bir yapılandırma ile hata ayıklama etkin başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="4c006-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="4c006-112">DSC kaynağı hata ayıklamak için bu kaynağa çağıran bir yapılandırma başlatın.</span><span class="sxs-lookup"><span data-stu-id="4c006-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span> <span data-ttu-id="4c006-113">Bu örnekte, biz çağıran basit bir yapılandırma sırasında göreceğiz [WindowsFeature](windowsfeatureResource.md) kaynak "WindowsPowerShellWebAccess" özelliği yüklü olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="4c006-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="4c006-114">Yapılandırma derledikten sonra başlatılsın çağırarak [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="4c006-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span></span> <span data-ttu-id="4c006-115">Yerel Configuration Manager (LCM'yi) yapılandırmasında ilk kaynak içine çağırdığında yapılandırma durdurur.</span><span class="sxs-lookup"><span data-stu-id="4c006-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span> <span data-ttu-id="4c006-116">Kullanırsanız `-Verbose` ve `-Wait` parametreleri, çıktı hata ayıklamayı başlatmak için girmeniz gereken satırları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4c006-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will 
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach. 
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="4c006-117">Bu noktada, LCM'yi kaynak adı ve ilk kesme noktası gelir.</span><span class="sxs-lookup"><span data-stu-id="4c006-117">At this point, the LCM has called the resource, and come to the first break point.</span></span> <span data-ttu-id="4c006-118">Çıktıdaki ilk üç satırını işleme ekleyin ve kaynak komut dosyası hata ayıklamayı Başlat gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c006-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="4c006-119">Kaynak komut dosyası hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="4c006-119">Debugging the resource script</span></span>

<span data-ttu-id="4c006-120">PowerShell ISE yeni bir örneğini başlatın.</span><span class="sxs-lookup"><span data-stu-id="4c006-120">Start a new instance of the PowerShell ISE.</span></span> <span data-ttu-id="4c006-121">Konsol bölmesinde çıktısını ilk üç satırını girin `Start-DscConfiguration` değiştirme komutları çıkış `<credentials>` geçerli kullanıcı kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="4c006-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span> <span data-ttu-id="4c006-122">Şimdi için benzer bir istem görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="4c006-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="4c006-123">Kaynak betik betik bölmesinde açılır ve hata ayıklayıcı ilk satırında durdurulur **Test TargetResource** işlevi ( **Test()** sınıf tabanlı bir kaynak yöntemi).</span><span class="sxs-lookup"><span data-stu-id="4c006-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="4c006-124">Kaynak komut dosyası adım için işe hata ayıklama komutlarını kullanabilirsiniz artık değişken değerlere göz, çağrı yığını görüntülemek ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="4c006-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="4c006-125">PowerShell ISE hata ayıklama hakkında daha fazla bilgi için bkz: [hata ayıklama komut dosyalarında Windows PowerShell ISE nasıl](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span><span class="sxs-lookup"><span data-stu-id="4c006-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span> <span data-ttu-id="4c006-126">Kaynak betik (veya sınıfı) her satırda bir kesme noktası olarak ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4c006-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="4c006-127">DSC hata ayıklama devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="4c006-127">Disabling DSC debugging</span></span>

<span data-ttu-id="4c006-128">Çağırdıktan sonra [etkinleştir DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx), tüm çağrıları [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) ayıklayıcıya çiğnemekten yapılandırma neden olur.</span><span class="sxs-lookup"><span data-stu-id="4c006-128">After calling [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="4c006-129">Yapılandırmaları normal olarak çalışmasına izin vermek için çağırarak hata ayıklama devre dışı bırakmalısınız [devre dışı bırakma DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4c006-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="4c006-130">**Not:** Rebooting LCM'yi hata ayıklama durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="4c006-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="4c006-131">Hata ayıklama etkinleştirilirse yapılandırma başlatma hala ayıklayıcıya bir yeniden başlatmadan sonra çalışmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4c006-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="4c006-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4c006-132">See Also</span></span>
- [<span data-ttu-id="4c006-133">Özel bir DSC kaynağı MOF ile yazma</span><span class="sxs-lookup"><span data-stu-id="4c006-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
- [<span data-ttu-id="4c006-134">PowerShell sınıfları içeren özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="4c006-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)

