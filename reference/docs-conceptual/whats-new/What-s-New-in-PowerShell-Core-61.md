---
title: PowerShell Core 6.1 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6.1 yayımlanan değişiklikleri
ms.date: 09/13/2018
ms.openlocfilehash: 27e7e846e9ba6ab34d83a084c2589b67a9d5cba9
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557326"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="958d5-103">PowerShell Core 6.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="958d5-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="958d5-104">Seçimi önemli yeni özellikler ve içinde PowerShell Core 6.1 sürümünde değişiklikleri bazıları aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="958d5-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="958d5-105">Ayrıca **ton** boyunca "daha hızlı ve daha kararlı (Ayrıca, birçok ve çok sayıda hata düzeltmesi) PowerShell olun bence olarak"!</span><span class="sxs-lookup"><span data-stu-id="958d5-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="958d5-106">Değişikliklerin tam listesi için kullanıma sunduğumuz [github'da changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="958d5-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="958d5-107">Ve bazı adları diyoruz sırasında kullandığınız için teşekkür ederiz [tüm topluluğa katkıda bulunanlar](https://github.com/PowerShell/PowerShell/graphs/contributors) yapılması bu sürümde mümkün.</span><span class="sxs-lookup"><span data-stu-id="958d5-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="958d5-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="958d5-108">.NET Core 2.1</span></span>

<span data-ttu-id="958d5-109">PowerShell Core 6.1, sonra .NET Core 2.1 için taşınabilir [Mayıs ayında yayımlanan](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), sonuçta elde edilen çok sayıda PowerShell iyileştirmeleri dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="958d5-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="958d5-110">performans geliştirmeleri (bkz [aşağıda](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="958d5-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="958d5-111">Alpine Linux desteği (Önizleme)</span><span class="sxs-lookup"><span data-stu-id="958d5-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="958d5-112">[.NET genel araç desteği](/dotnet/core/tools/global-tools) - PowerShell için Yakında sunulacak</span><span class="sxs-lookup"><span data-stu-id="958d5-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="958d5-113">Windows Uyumluluk Paketi .NET Core için</span><span class="sxs-lookup"><span data-stu-id="958d5-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="958d5-114">Windows üzerinde .NET ekibi sevk [Windows Uyumluluk Paketi .NET Core için](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), bir dizi ekleyen bir derleme kümesi geri Windows üzerinde .NET Core için API kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="958d5-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="958d5-115">Böylece bunlar üzerinde kullanılabilir olan tüm modülleri veya bu API'leri kullanan betikler güvenebilirsiniz PowerShell Core 6.1 sürümüne Windows Uyumluluk Paketi ekledik.</span><span class="sxs-lookup"><span data-stu-id="958d5-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="958d5-116">Windows Uyumluluk Paketi kullanmak PowerShell Core sağlayan **ile Windows 10 Ekim 2018 sevk 1900'den fazla cmdlet Update ve Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="958d5-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="958d5-117">Performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="958d5-117">Performance improvements</span></span>

<span data-ttu-id="958d5-118">PowerShell Core 6.0 bazı önemli performans geliştirmeleri yaptık.</span><span class="sxs-lookup"><span data-stu-id="958d5-118">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="958d5-119">PowerShell Core 6.1 belirli işlemleri hızını geliştirmeye devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="958d5-119">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="958d5-120">Örneğin, `Group-Object` 66 oranında hatalarının çözümünü hızlandırdı:</span><span class="sxs-lookup"><span data-stu-id="958d5-120">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="958d5-121">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="958d5-121">Windows PowerShell 5.1</span></span> | <span data-ttu-id="958d5-122">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="958d5-122">PowerShell Core 6.0</span></span> | <span data-ttu-id="958d5-123">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="958d5-123">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="958d5-124">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="958d5-124">Time (sec)</span></span>   | <span data-ttu-id="958d5-125">25.178</span><span class="sxs-lookup"><span data-stu-id="958d5-125">25.178</span></span>                 | <span data-ttu-id="958d5-126">19.653</span><span class="sxs-lookup"><span data-stu-id="958d5-126">19.653</span></span>              | <span data-ttu-id="958d5-127">6.641</span><span class="sxs-lookup"><span data-stu-id="958d5-127">6.641</span></span>               |
| <span data-ttu-id="958d5-128">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="958d5-128">Speed-up (%)</span></span> | <span data-ttu-id="958d5-129">YOK</span><span class="sxs-lookup"><span data-stu-id="958d5-129">N/A</span></span>                    | <span data-ttu-id="958d5-130">%21,9</span><span class="sxs-lookup"><span data-stu-id="958d5-130">21.9%</span></span>               | <span data-ttu-id="958d5-131">%66.2</span><span class="sxs-lookup"><span data-stu-id="958d5-131">66.2%</span></span>               |

<span data-ttu-id="958d5-132">Benzer şekilde, bunun gibi sıralama senaryoları % 15'den fazla geliştirildi:</span><span class="sxs-lookup"><span data-stu-id="958d5-132">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="958d5-133">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="958d5-133">Windows PowerShell 5.1</span></span> | <span data-ttu-id="958d5-134">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="958d5-134">PowerShell Core 6.0</span></span> | <span data-ttu-id="958d5-135">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="958d5-135">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="958d5-136">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="958d5-136">Time (sec)</span></span>   | <span data-ttu-id="958d5-137">12.170</span><span class="sxs-lookup"><span data-stu-id="958d5-137">12.170</span></span>                 | <span data-ttu-id="958d5-138">8.493</span><span class="sxs-lookup"><span data-stu-id="958d5-138">8.493</span></span>               | <span data-ttu-id="958d5-139">7.08</span><span class="sxs-lookup"><span data-stu-id="958d5-139">7.08</span></span>                |
| <span data-ttu-id="958d5-140">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="958d5-140">Speed-up (%)</span></span> | <span data-ttu-id="958d5-141">YOK</span><span class="sxs-lookup"><span data-stu-id="958d5-141">N/A</span></span>                    | <span data-ttu-id="958d5-142">%30.2</span><span class="sxs-lookup"><span data-stu-id="958d5-142">30.2%</span></span>               | <span data-ttu-id="958d5-143">%16.6</span><span class="sxs-lookup"><span data-stu-id="958d5-143">16.6%</span></span>               |

<span data-ttu-id="958d5-144">`Import-Csv` Ayrıca önemli ölçüde sonra bir gerileme Windows Powershell'den hatalarının çözümünü hızlandırdı.</span><span class="sxs-lookup"><span data-stu-id="958d5-144">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="958d5-145">Aşağıdaki örnek, bir test CSV 26,616 satırlar ve sütunlarla altı kullanır:</span><span class="sxs-lookup"><span data-stu-id="958d5-145">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="958d5-146">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="958d5-146">Windows PowerShell 5.1</span></span> | <span data-ttu-id="958d5-147">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="958d5-147">PowerShell Core 6.0</span></span> | <span data-ttu-id="958d5-148">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="958d5-148">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="958d5-149">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="958d5-149">Time (sec)</span></span>   | <span data-ttu-id="958d5-150">0.441</span><span class="sxs-lookup"><span data-stu-id="958d5-150">0.441</span></span>                  | <span data-ttu-id="958d5-151">1.069</span><span class="sxs-lookup"><span data-stu-id="958d5-151">1.069</span></span>               | <span data-ttu-id="958d5-152">0,268</span><span class="sxs-lookup"><span data-stu-id="958d5-152">0.268</span></span>                  |
| <span data-ttu-id="958d5-153">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="958d5-153">Speed-up (%)</span></span> | <span data-ttu-id="958d5-154">YOK</span><span class="sxs-lookup"><span data-stu-id="958d5-154">N/A</span></span>                    | <span data-ttu-id="958d5-155">-%142.4</span><span class="sxs-lookup"><span data-stu-id="958d5-155">-142.4%</span></span>             | <span data-ttu-id="958d5-156">%74.9 (WPS %39.2)</span><span class="sxs-lookup"><span data-stu-id="958d5-156">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="958d5-157">Son olarak, JSON'a dönüştürme `PSObject` % 50'den itibaren Windows PowerShell hatalarının çözümünü hızlandırdı.</span><span class="sxs-lookup"><span data-stu-id="958d5-157">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="958d5-158">Aşağıdaki örnek, yaklaşık 2 MB test JSON dosyasını kullanır:</span><span class="sxs-lookup"><span data-stu-id="958d5-158">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="958d5-159">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="958d5-159">Windows PowerShell 5.1</span></span> | <span data-ttu-id="958d5-160">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="958d5-160">PowerShell Core 6.0</span></span> | <span data-ttu-id="958d5-161">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="958d5-161">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="958d5-162">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="958d5-162">Time (sec)</span></span>   | <span data-ttu-id="958d5-163">0.259</span><span class="sxs-lookup"><span data-stu-id="958d5-163">0.259</span></span>                  | <span data-ttu-id="958d5-164">0.577</span><span class="sxs-lookup"><span data-stu-id="958d5-164">0.577</span></span>               | <span data-ttu-id="958d5-165">0,125</span><span class="sxs-lookup"><span data-stu-id="958d5-165">0.125</span></span>                  |
| <span data-ttu-id="958d5-166">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="958d5-166">Speed-up (%)</span></span> | <span data-ttu-id="958d5-167">YOK</span><span class="sxs-lookup"><span data-stu-id="958d5-167">N/A</span></span>                    | <span data-ttu-id="958d5-168">-%122.8</span><span class="sxs-lookup"><span data-stu-id="958d5-168">-122.8%</span></span>             | <span data-ttu-id="958d5-169">%78.3 (WPS %51.7)</span><span class="sxs-lookup"><span data-stu-id="958d5-169">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a><span data-ttu-id="958d5-170">Denetleme `system32` Windows üzerinde uyumlu gelen modüller için</span><span class="sxs-lookup"><span data-stu-id="958d5-170">Check `system32` for compatible inbox modules on Windows</span></span>

<span data-ttu-id="958d5-171">Windows 10 1809 güncelleştirmesi ve Windows Server 2019, gelen PowerShell modülleri bunları PowerShell Core ile uyumlu olarak işaretlemek için bir dizi güncelleştirdik.</span><span class="sxs-lookup"><span data-stu-id="958d5-171">In the Windows 10 1809 update and Windows Server 2019, we updated a number of inbox PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="958d5-172">PowerShell Core 6.1 başlatıldığında otomatik olarak içerecektir `$windir\System32` parçası olarak `PSModulePath` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="958d5-172">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="958d5-173">Ancak, yalnızca modüllerle kullanıma sunduğu `Get-Module` ve `Import-Module` varsa kendi `CompatiblePSEdition` ile uyumlu olarak işaretlenmiş `Core`.</span><span class="sxs-lookup"><span data-stu-id="958d5-173">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="958d5-174">Hangi rollerin ve özelliklerin yüklü bağlı olarak farklı kullanılabilir modüllerin görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="958d5-174">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="958d5-175">Kullanarak tüm modülleri göstermek için bu davranışı geçersiz kılabilirsiniz `-SkipEditionCheck` parametresi geçin.</span><span class="sxs-lookup"><span data-stu-id="958d5-175">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="958d5-176">Ayrıca ekledik bir `PSEdition` için tablo çıkışına özelliği.</span><span class="sxs-lookup"><span data-stu-id="958d5-176">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="958d5-177">Bu davranışı hakkında daha fazla bilgi için kullanıma [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/2-Draft-Accepted/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="958d5-177">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/2-Draft-Accepted/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="958d5-178">Markdown cmdlet'leri ve işleme</span><span class="sxs-lookup"><span data-stu-id="958d5-178">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="958d5-179">Markdown temel biçimlendirme ile okunabilir düz metin belgeleri oluşturmak için standart bir HTML'e işlenebilecek ' dir.</span><span class="sxs-lookup"><span data-stu-id="958d5-179">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="958d5-180">Bazı cmdlet'ler konsolunda, Markdown belgeleri işlemek ve dönüştürmek izin 6.1 ekledik dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="958d5-180">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="958d5-181">Örneğin, `Show-Markdown` konsolunda bir Markdown dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="958d5-181">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Örnek Markdown Göster](./images/markdown_example.png)

<span data-ttu-id="958d5-183">Bu cmdlet'ler nasıl çalıştığı hakkında daha fazla bilgi için kullanıma [bu RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="958d5-183">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="958d5-184">Deneysel özellik bayrakları</span><span class="sxs-lookup"><span data-stu-id="958d5-184">Experimental feature flags</span></span>

<span data-ttu-id="958d5-185">Deneysel özellik bayraklarını sonlandırılan henüz özelliklerini etkinleştirme olanağı verir.</span><span class="sxs-lookup"><span data-stu-id="958d5-185">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="958d5-186">Bu Deneysel özelliklerin desteklenmez ve hatalar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="958d5-186">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="958d5-187">' Deki bu özellik hakkında daha fazla bilgi [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="958d5-187">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="958d5-188">Web cmdlet'i geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="958d5-188">Web cmdlet improvements</span></span>

<span data-ttu-id="958d5-189">Performanstan @markekraus, bizim web cmdlet'leri için tam bir slew geliştirmeler yapıldı: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="958d5-189">Thanks to @markekraus, a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="958d5-190">ve [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="958d5-190">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="958d5-191">[Çekme isteği #6109](https://github.com/PowerShell/PowerShell/pull/6109) -UTF-8 için kodlama kümesi varsayılan `application-json` yanıtları</span><span class="sxs-lookup"><span data-stu-id="958d5-191">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="958d5-192">[Çekme isteği # 6018 oluşturun](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` izin vermek için parametre `Content-Type` standartlarıyla uyumlu olmayan üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="958d5-192">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="958d5-193">[Çekme isteği #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` desteklemek için parametre Basitleştirilmiş `multipart/form-data` desteği</span><span class="sxs-lookup"><span data-stu-id="958d5-193">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="958d5-194">[Çekme isteği #6338](https://github.com/PowerShell/PowerShell/pull/6338) - uyumlu, büyük küçük harf duyarsız ilişkisi anahtarlarını işleme</span><span class="sxs-lookup"><span data-stu-id="958d5-194">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="958d5-195">[Çekme isteği #6447](https://github.com/PowerShell/PowerShell/pull/6447) -ekleme `-Resume` web cmdlet'leri için parametre</span><span class="sxs-lookup"><span data-stu-id="958d5-195">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="958d5-196">Uzaktan iletişimini geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="958d5-196">Remoting improvements</span></span>

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a><span data-ttu-id="958d5-197">PowerShell Direct PowerShell Core kullanmayı dener</span><span class="sxs-lookup"><span data-stu-id="958d5-197">PowerShell Direct tries to use PowerShell Core first</span></span>

<span data-ttu-id="958d5-198">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) PowerShell ve bir Hyper-V VM ağ bağlantısı olmayan veya diğer uzaktan yönetim hizmetlere bağlanmasına olanak sağlayan Hyper-V özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="958d5-198">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM without network connectivity or other remote management services.</span></span>

<span data-ttu-id="958d5-199">Geçmişte, PowerShell Direct VM'ye gelen Windows PowerShell örneğini kullanarak bağlı.</span><span class="sxs-lookup"><span data-stu-id="958d5-199">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the VM.</span></span>
<span data-ttu-id="958d5-200">Şimdi, PowerShell Direct önce herhangi bir kullanılabilir kullanarak bağlanmayı dener `pwsh.exe` üzerinde `PATH` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="958d5-200">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="958d5-201">Varsa `pwsh.exe` değilse kullanılabilir, PowerShell Direct geri kullanmaya döner `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="958d5-201">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="958d5-202">`Enable-PSRemoting` Şimdi Önizleme sürümleri için ayrı bir uzak uç noktası oluşturur</span><span class="sxs-lookup"><span data-stu-id="958d5-202">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="958d5-203">`Enable-PSRemoting` Şimdi iki uzaktan oturum yapılandırmaları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="958d5-203">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="958d5-204">Bir PowerShell ana sürümü.</span><span class="sxs-lookup"><span data-stu-id="958d5-204">One for the major version of PowerShell.</span></span> <span data-ttu-id="958d5-205">Örneğin,`PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="958d5-205">For example,`PowerShell.6`.</span></span> <span data-ttu-id="958d5-206">Bağlı "Sistem genelinde" PowerShell 6 oturum yapılandırması alt sürüm güncelleştirmeleri arasında yararlandı bu endpoint</span><span class="sxs-lookup"><span data-stu-id="958d5-206">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="958d5-207">Örneğin bir sürüme özgü oturum yapılandırması: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="958d5-207">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="958d5-208">Bu davranış, aynı makinede birden çok PowerShell 6 sürümlerinin yüklendiğini ve erişilebilir olmasını istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="958d5-208">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="958d5-209">Ayrıca, Önizleme sürümlerini PowerShell artık kendi uzaktan iletişim oturum yapılandırmaları çalıştırdıktan sonra elde `Enable-PSRemoting` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="958d5-209">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="958d5-210">Çıkış önce WinRM ayarlamadıysanız farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="958d5-210">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="958d5-211">Ardından Önizleme ayrı PowerShell oturum yapılandırmaları görebilir ve PowerShell 6'ın ve her belirli bir sürümü için kararlı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="958d5-211">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="958d5-212">`user@host:port` SSH için desteklenen söz dizimleri</span><span class="sxs-lookup"><span data-stu-id="958d5-212">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="958d5-213">SSH istemcileri genellikle bir bağlantı dizesi şu biçimde desteklemek `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="958d5-213">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="958d5-214">' Nın eklenmesiyle SSH bir protokol olarak PowerShell uzaktan iletişim için bağlantı dizesinin bu biçimi desteği ekledik:</span><span class="sxs-lookup"><span data-stu-id="958d5-214">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="958d5-215">Üzerinde Windows Gezgini Kabuk bağlam menüsü eklemeye MSI seçeneği</span><span class="sxs-lookup"><span data-stu-id="958d5-215">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="958d5-216">Performanstan @bergmeisterartık Windows bağlam menüsünden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="958d5-216">Thanks to @bergmeister, now you can enable a context menu on Windows.</span></span> <span data-ttu-id="958d5-217">Artık sistem genelinde yüklemenizin PowerShell 6.1, Windows Gezgini'nde herhangi bir klasörden açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="958d5-217">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![PowerShell 6 Kabuk bağlam menüsü](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="958d5-219">İlgi çekici Özellikler</span><span class="sxs-lookup"><span data-stu-id="958d5-219">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="958d5-220">"Windows kısayol atlama listesinde yönetici olarak çalıştır"</span><span class="sxs-lookup"><span data-stu-id="958d5-220">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="958d5-221">Performanstan @bergmeister, PowerShell Core kısayolun atlama listesi artık "Yönetici olarak çalıştır" içerir:</span><span class="sxs-lookup"><span data-stu-id="958d5-221">Thanks to @bergmeister, the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![PowerShell 6 atlama listesinde yönetici olarak çalıştırın](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="958d5-223">`cd -` Önceki dizinine döndürür</span><span class="sxs-lookup"><span data-stu-id="958d5-223">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="958d5-224">Ya da Linux üzerinde:</span><span class="sxs-lookup"><span data-stu-id="958d5-224">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="958d5-225">Ayrıca, `cd --` değişikliklerini `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="958d5-225">Also, `cd --` changes to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="958d5-226">Performanstan @iSazonov, [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet'i, PowerShell Core için unity'nin.</span><span class="sxs-lookup"><span data-stu-id="958d5-226">Thanks to @iSazonov, the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="958d5-227">`Update-Help` Yönetici olmayan</span><span class="sxs-lookup"><span data-stu-id="958d5-227">`Update-Help` as non-admin</span></span>

<span data-ttu-id="958d5-228">Popüler isteğe bağlı olarak `Update-Help` artık yönetici olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="958d5-228">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="958d5-229">`Update-Help` artık bir kullanıcı kapsamlı klasöre Yardım kaydetmek için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="958d5-229">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="958d5-230">Yeni yöntemler/özellikler hakkında `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="958d5-230">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="958d5-231">Performanstan @iSazonov, yeni yöntemleri ve özellikleri ekledik `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="958d5-231">Thanks to @iSazonov, we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="958d5-232">`PSCustomObject` artık bir `Count` / `Length` öğe sayısını veren özellik.</span><span class="sxs-lookup"><span data-stu-id="958d5-232">`PSCustomObject` now includes a `Count`/`Length` property that gives the number of items.</span></span>

<span data-ttu-id="958d5-233">Bu örneklerin ikisi de `2` sayısı arttıkça `PSCustomObjects` koleksiyondaki.</span><span class="sxs-lookup"><span data-stu-id="958d5-233">Both of these examples return `2` as the number of `PSCustomObjects` in the collection.</span></span>

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

<span data-ttu-id="958d5-234">Bu iş yöntemlerine `ForEach` ve `Where` çalıştırmak ve filtrelemek olanak sağlayan yöntemleri `PSCustomObject` öğeleri:</span><span class="sxs-lookup"><span data-stu-id="958d5-234">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

<span data-ttu-id="958d5-235">Performanstan @SimonWahlin, ekledik `-Not` parametresi `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="958d5-235">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="958d5-236">Artık bir nesnede bir işlem hattı olmayan-bulunup bulunmadığını bir özelliği ya da null veya boş özellik değeri filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="958d5-236">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="958d5-237">Örneğin, bu komut, tanımlanan tüm bağımlı hizmetlerin olmayan tüm hizmetleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="958d5-237">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="958d5-238">`New-ModuleManifest` BOM daha az UTF-8 belgesi oluşturur</span><span class="sxs-lookup"><span data-stu-id="958d5-238">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="958d5-239">Güncelleştirdik BOM daha az UTF-8'PowerShell 6. 0'de alındığında, `New-ModuleManifest` yerine UTF-16 bir BOM daha az UTF-8 belge oluşturmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="958d5-239">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="958d5-240">Temsilci PSMethod öğesinden dönüştürme</span><span class="sxs-lookup"><span data-stu-id="958d5-240">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="958d5-241">Performanstan @powercode, artık dönüştürülmesi destekliyoruz bir `PSMethod` içinde bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="958d5-241">Thanks to @powercode, we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="958d5-242">Bu sayede geçirme gibi şeyleri `PSMethod` `[M]::DoubleStrLen` olarak bir temsilci değerde `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="958d5-242">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="958d5-243">Bu değişiklikle ilgili daha fazla bilgi için kullanıma [çekme isteği #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="958d5-243">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="958d5-244">Standart sapma `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="958d5-244">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="958d5-245">Performanstan @CloudyDino, ekledik bir `StandardDeviation` özelliğini `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="958d5-245">Thanks to @CloudyDino, we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="958d5-246">Performanstan @maybe-hello-world, `Get-PfxCertificate` artık `Password` alan parametresi bir `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="958d5-246">Thanks to @maybe-hello-world, `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="958d5-247">Bu, etkileşimli olmayan kullanmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="958d5-247">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="958d5-248">Kaldırılmasını `more` işlevi</span><span class="sxs-lookup"><span data-stu-id="958d5-248">Removal of the `more` function</span></span>

<span data-ttu-id="958d5-249">Geçmişte, bir işlev üzerinde adlı Windows PowerShell sevk `more` kaydırılan `more.com`.</span><span class="sxs-lookup"><span data-stu-id="958d5-249">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="958d5-250">Bu işlev artık kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="958d5-250">That function has now been removed.</span></span>

<span data-ttu-id="958d5-251">Ayrıca `help` işlevi değiştirilen kullanılacak `more.com` Windows ya da sistemin varsayılan çağrı tarafından belirtilen `$env:PAGER` Windows dışı platformlarda.</span><span class="sxs-lookup"><span data-stu-id="958d5-251">Also the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="958d5-252">`cd DriveName:` artık bu sürücüye geçerli çalışma dizininde kullanıcıları döndürür</span><span class="sxs-lookup"><span data-stu-id="958d5-252">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="958d5-253">Daha önce kullanarak `Set-Location` veya `cd` kullanıcılar söz konusu sürücünün varsayılan konuma gönderilen bir PSDrive penceresine dönün.</span><span class="sxs-lookup"><span data-stu-id="958d5-253">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="958d5-254">Performanstan @mcbobke, kullanıcıların son bilinen geçerli çalışma dizini için artık bu oturum için gönderilir.</span><span class="sxs-lookup"><span data-stu-id="958d5-254">Thanks to @mcbobke, users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="958d5-255">Windows PowerShell türü Hızlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="958d5-255">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="958d5-256">Windows PowerShell'de, iş ile ilgili kendi türleri daha kolay hale getirmek için aşağıdaki türü Hızlandırıcılar ekledik:</span><span class="sxs-lookup"><span data-stu-id="958d5-256">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="958d5-257">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="958d5-257">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="958d5-258">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="958d5-258">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="958d5-259">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="958d5-259">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="958d5-260">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="958d5-260">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="958d5-261">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="958d5-261">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="958d5-262">Bu tür Hızlandırıcıları PowerShell 6'da bulunmayan, ancak Windows üzerinde çalışan PowerShell 6.1 eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="958d5-262">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="958d5-263">Bu tür AD kolayca oluşturulmasında yararlı olan ve WMI nesneleri.</span><span class="sxs-lookup"><span data-stu-id="958d5-263">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="958d5-264">Örneğin, LDAP kullanarak sorgulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="958d5-264">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="958d5-265">Bu örneklerin her ikisi Win32_OperatingSystem CIM nesnesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="958d5-265">Both of these examples create a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="958d5-266">`-lp` diğer tüm `-LiteralPath` parametreleri</span><span class="sxs-lookup"><span data-stu-id="958d5-266">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="958d5-267">Performanstan @kvprasoon, artık bir parametre diğer adını sahibiz `-lp` sahip tüm yerleşik PowerShell cmdlet'lerinin bir `-LiteralPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="958d5-267">Thanks to @kvprasoon, we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="958d5-268">Bozucu değişiklikler</span><span class="sxs-lookup"><span data-stu-id="958d5-268">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="958d5-269">Windows MSI tabanlı yükleme yollarında</span><span class="sxs-lookup"><span data-stu-id="958d5-269">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="958d5-270">Windows üzerinde MSI paketi artık aşağıdaki yola yüklenir:</span><span class="sxs-lookup"><span data-stu-id="958d5-270">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="958d5-271">`$env:ProgramFiles\PowerShell\6\` 6.x kararlı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="958d5-271">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="958d5-272">`$env:ProgramFiles\PowerShell\6-preview\` 6.x Önizleme yüklemek için</span><span class="sxs-lookup"><span data-stu-id="958d5-272">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="958d5-273">Bu değişiklik, PowerShell Core Microsoft Update tarafından güncelleştirilmiş/hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="958d5-273">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="958d5-274">Daha fazla bilgi için kullanıma [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="958d5-274">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="958d5-275">Telemetri yalnızca bir ortam değişkeni ile devre dışı bırakılabilir</span><span class="sxs-lookup"><span data-stu-id="958d5-275">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="958d5-276">PowerShell Core başlatıldığında temel telemetri verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="958d5-276">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="958d5-277">Veriler, işletim sistemi adı, işletim sistemi sürümü ve PowerShell sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="958d5-277">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="958d5-278">Bu veriler nerede PowerShell kullanılır ve yeni özellikler ve düzeltmeler öncelik sağlıyor ortamları daha iyi anlamak sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="958d5-278">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="958d5-279">Çevirme bu telemetri için ortam değişkenini ayarlamak `POWERSHELL_TELEMETRY_OPTOUT` için `true`, `yes`, veya `1`.</span><span class="sxs-lookup"><span data-stu-id="958d5-279">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="958d5-280">Dosya silme işlemi artık desteklemiyoruz `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` telemetri devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="958d5-280">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="958d5-281">Temel kimlik doğrulaması üzerinden PowerShell uzaktan iletişimini HTTP UNIX platformlarda izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="958d5-281">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="958d5-282">Şifrelenmemiş trafik kullanımını önlemek için PowerShell uzaktan iletişimini Unix platformlarında NTLM/anlaşma ya da HTTPS kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="958d5-282">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="958d5-283">Bu değişiklikler hakkında daha fazla bilgi için kullanıma [çekme isteği #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span><span class="sxs-lookup"><span data-stu-id="958d5-283">For more information on these changes, check out [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="958d5-284">Kaldırılan `VisualBasic` desteklenen dilde Add-Type olarak</span><span class="sxs-lookup"><span data-stu-id="958d5-284">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="958d5-285">Geçmişte, Visual Basic kod kullanarak derleme `Add-Type` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="958d5-285">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="958d5-286">Visual Basic ile kullanılan nadiren `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="958d5-286">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="958d5-287">PowerShell boyutunu azaltmak için bu özelliği kaldırdık.</span><span class="sxs-lookup"><span data-stu-id="958d5-287">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="958d5-288">Kullanımları temizlendi `CommandTypes.Workflow` ve `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="958d5-288">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="958d5-289">Bu değişiklikler hakkında daha fazla bilgi için kullanıma [çekme isteği #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="958d5-289">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>