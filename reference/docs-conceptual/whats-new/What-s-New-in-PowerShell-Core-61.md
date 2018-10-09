---
title: PowerShell Core 6.1 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6.1 yayımlanan değişiklikleri
ms.date: 09/13/2018
ms.openlocfilehash: 4e39780a0ff446993005bba6284741f3b4b02549
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851316"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="e1b55-103">PowerShell Core 6.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="e1b55-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="e1b55-104">Seçimi önemli yeni özellikler ve içinde PowerShell Core 6.1 sürümünde değişiklikleri bazıları aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="e1b55-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="e1b55-105">Ayrıca **ton** boyunca "daha hızlı ve daha kararlı (Ayrıca, birçok ve çok sayıda hata düzeltmesi) PowerShell olun bence olarak"!</span><span class="sxs-lookup"><span data-stu-id="e1b55-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="e1b55-106">Değişikliklerin tam listesi için kullanıma sunduğumuz [github'da changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="e1b55-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="e1b55-107">Ve bazı adları diyoruz sırasında kullandığınız için teşekkür ederiz [tüm topluluğa katkıda bulunanlar](https://github.com/PowerShell/PowerShell/graphs/contributors) yapılması bu sürümde mümkün.</span><span class="sxs-lookup"><span data-stu-id="e1b55-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="e1b55-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-108">.NET Core 2.1</span></span>

<span data-ttu-id="e1b55-109">PowerShell Core 6.1, sonra .NET Core 2.1 için taşınabilir [Mayıs ayında yayımlanan](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), sonuçta elde edilen çok sayıda PowerShell iyileştirmeleri dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="e1b55-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="e1b55-110">performans geliştirmeleri (bkz [aşağıda](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="e1b55-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="e1b55-111">Alpine Linux desteği (Önizleme)</span><span class="sxs-lookup"><span data-stu-id="e1b55-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="e1b55-112">[.NET genel araç desteği](/dotnet/core/tools/global-tools) - PowerShell için Yakında sunulacak</span><span class="sxs-lookup"><span data-stu-id="e1b55-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="e1b55-113">Windows Uyumluluk Paketi .NET Core için</span><span class="sxs-lookup"><span data-stu-id="e1b55-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="e1b55-114">Windows üzerinde .NET ekibi sevk [Windows Uyumluluk Paketi .NET Core için](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), bir dizi ekleyen bir derleme kümesi geri Windows üzerinde .NET Core için API kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="e1b55-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="e1b55-115">Böylece bunlar üzerinde kullanılabilir olan tüm modülleri veya bu API'leri kullanan betikler güvenebilirsiniz PowerShell Core 6.1 sürümüne Windows Uyumluluk Paketi ekledik.</span><span class="sxs-lookup"><span data-stu-id="e1b55-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="e1b55-116">Windows Uyumluluk Paketi kullanmak PowerShell Core sağlayan **ile Windows 10 Ekim 2018 sevk 1900'den fazla cmdlet Update ve Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="e1b55-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="e1b55-117">Uygulama beyaz listeye ekleme desteği</span><span class="sxs-lookup"><span data-stu-id="e1b55-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="e1b55-118">PowerShell Core 6.1, Windows PowerShell 5.1 destekleme ile eşlik sahip [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) ve [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) uygulama beyaz listeye ekleme.</span><span class="sxs-lookup"><span data-stu-id="e1b55-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="e1b55-119">Uygulama beyaz listesini hangi ikili dosyalarını yürütülmek üzere PowerShell ile kullanılan izin ayrıntılı denetim sağlar [kısıtlı dil modu](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span><span class="sxs-lookup"><span data-stu-id="e1b55-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="e1b55-120">Performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="e1b55-120">Performance improvements</span></span>

<span data-ttu-id="e1b55-121">PowerShell Core 6.0 bazı önemli performans geliştirmeleri yaptık.</span><span class="sxs-lookup"><span data-stu-id="e1b55-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="e1b55-122">PowerShell Core 6.1 belirli işlemleri hızını geliştirmeye devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="e1b55-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="e1b55-123">Örneğin, `Group-Object` 66 oranında hatalarının çözümünü hızlandırdı:</span><span class="sxs-lookup"><span data-stu-id="e1b55-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="e1b55-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e1b55-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e1b55-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="e1b55-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="e1b55-127">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="e1b55-127">Time (sec)</span></span>   | <span data-ttu-id="e1b55-128">25.178</span><span class="sxs-lookup"><span data-stu-id="e1b55-128">25.178</span></span>                 | <span data-ttu-id="e1b55-129">19.653</span><span class="sxs-lookup"><span data-stu-id="e1b55-129">19.653</span></span>              | <span data-ttu-id="e1b55-130">6.641</span><span class="sxs-lookup"><span data-stu-id="e1b55-130">6.641</span></span>               |
| <span data-ttu-id="e1b55-131">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="e1b55-131">Speed-up (%)</span></span> | <span data-ttu-id="e1b55-132">YOK</span><span class="sxs-lookup"><span data-stu-id="e1b55-132">N/A</span></span>                    | <span data-ttu-id="e1b55-133">%21,9</span><span class="sxs-lookup"><span data-stu-id="e1b55-133">21.9%</span></span>               | <span data-ttu-id="e1b55-134">%66.2</span><span class="sxs-lookup"><span data-stu-id="e1b55-134">66.2%</span></span>               |

<span data-ttu-id="e1b55-135">Benzer şekilde, bunun gibi sıralama senaryoları % 15'den fazla geliştirildi:</span><span class="sxs-lookup"><span data-stu-id="e1b55-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="e1b55-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e1b55-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e1b55-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="e1b55-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="e1b55-139">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="e1b55-139">Time (sec)</span></span>   | <span data-ttu-id="e1b55-140">12.170</span><span class="sxs-lookup"><span data-stu-id="e1b55-140">12.170</span></span>                 | <span data-ttu-id="e1b55-141">8.493</span><span class="sxs-lookup"><span data-stu-id="e1b55-141">8.493</span></span>               | <span data-ttu-id="e1b55-142">7.08</span><span class="sxs-lookup"><span data-stu-id="e1b55-142">7.08</span></span>                |
| <span data-ttu-id="e1b55-143">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="e1b55-143">Speed-up (%)</span></span> | <span data-ttu-id="e1b55-144">YOK</span><span class="sxs-lookup"><span data-stu-id="e1b55-144">N/A</span></span>                    | <span data-ttu-id="e1b55-145">%30.2</span><span class="sxs-lookup"><span data-stu-id="e1b55-145">30.2%</span></span>               | <span data-ttu-id="e1b55-146">%16.6</span><span class="sxs-lookup"><span data-stu-id="e1b55-146">16.6%</span></span>               |

<span data-ttu-id="e1b55-147">`Import-Csv` Ayrıca önemli ölçüde sonra bir gerileme Windows Powershell'den hatalarının çözümünü hızlandırdı.</span><span class="sxs-lookup"><span data-stu-id="e1b55-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="e1b55-148">Aşağıdaki örnek, bir test CSV 26,616 satırlar ve sütunlarla altı kullanır:</span><span class="sxs-lookup"><span data-stu-id="e1b55-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="e1b55-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e1b55-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e1b55-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="e1b55-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="e1b55-152">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="e1b55-152">Time (sec)</span></span>   | <span data-ttu-id="e1b55-153">0.441</span><span class="sxs-lookup"><span data-stu-id="e1b55-153">0.441</span></span>                  | <span data-ttu-id="e1b55-154">1.069</span><span class="sxs-lookup"><span data-stu-id="e1b55-154">1.069</span></span>               | <span data-ttu-id="e1b55-155">0,268</span><span class="sxs-lookup"><span data-stu-id="e1b55-155">0.268</span></span>                  |
| <span data-ttu-id="e1b55-156">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="e1b55-156">Speed-up (%)</span></span> | <span data-ttu-id="e1b55-157">YOK</span><span class="sxs-lookup"><span data-stu-id="e1b55-157">N/A</span></span>                    | <span data-ttu-id="e1b55-158">-%142.4</span><span class="sxs-lookup"><span data-stu-id="e1b55-158">-142.4%</span></span>             | <span data-ttu-id="e1b55-159">%74.9 (WPS %39.2)</span><span class="sxs-lookup"><span data-stu-id="e1b55-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="e1b55-160">Son olarak, JSON'a dönüştürme `PSObject` % 50'den itibaren Windows PowerShell hatalarının çözümünü hızlandırdı.</span><span class="sxs-lookup"><span data-stu-id="e1b55-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="e1b55-161">Aşağıdaki örnek, yaklaşık 2 MB test JSON dosyasını kullanır:</span><span class="sxs-lookup"><span data-stu-id="e1b55-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="e1b55-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e1b55-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e1b55-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="e1b55-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e1b55-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="e1b55-165">Süre (sn)</span><span class="sxs-lookup"><span data-stu-id="e1b55-165">Time (sec)</span></span>   | <span data-ttu-id="e1b55-166">0.259</span><span class="sxs-lookup"><span data-stu-id="e1b55-166">0.259</span></span>                  | <span data-ttu-id="e1b55-167">0.577</span><span class="sxs-lookup"><span data-stu-id="e1b55-167">0.577</span></span>               | <span data-ttu-id="e1b55-168">0,125</span><span class="sxs-lookup"><span data-stu-id="e1b55-168">0.125</span></span>                  |
| <span data-ttu-id="e1b55-169">Hız yükselmesi (%)</span><span class="sxs-lookup"><span data-stu-id="e1b55-169">Speed-up (%)</span></span> | <span data-ttu-id="e1b55-170">YOK</span><span class="sxs-lookup"><span data-stu-id="e1b55-170">N/A</span></span>                    | <span data-ttu-id="e1b55-171">-%122.8</span><span class="sxs-lookup"><span data-stu-id="e1b55-171">-122.8%</span></span>             | <span data-ttu-id="e1b55-172">%78.3 (WPS %51.7)</span><span class="sxs-lookup"><span data-stu-id="e1b55-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="e1b55-173">Denetleme `system32` uyumlu yerleşik modülleri Windows üzerinde</span><span class="sxs-lookup"><span data-stu-id="e1b55-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="e1b55-174">Windows 10 1809 güncelleştirmesi ve Windows Server 2019, yerleşik PowerShell modülleri bunları PowerShell Core ile uyumlu olarak işaretlemek için bir dizi güncelleştirdik.</span><span class="sxs-lookup"><span data-stu-id="e1b55-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="e1b55-175">PowerShell Core 6.1 başlatıldığında otomatik olarak içerecektir `$windir\System32` parçası olarak `PSModulePath` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="e1b55-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="e1b55-176">Ancak, yalnızca modüllerle kullanıma sunduğu `Get-Module` ve `Import-Module` varsa kendi `CompatiblePSEdition` ile uyumlu olarak işaretlenmiş `Core`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="e1b55-177">Hangi rollerin ve özelliklerin yüklü bağlı olarak farklı kullanılabilir modüllerin görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b55-177">You may see different available modules depending on what roles and features are installed.</span></span>

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

<span data-ttu-id="e1b55-178">Kullanarak tüm modülleri göstermek için bu davranışı geçersiz kılabilirsiniz `-SkipEditionCheck` parametresi geçin.</span><span class="sxs-lookup"><span data-stu-id="e1b55-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="e1b55-179">Ayrıca ekledik bir `PSEdition` için tablo çıkışına özelliği.</span><span class="sxs-lookup"><span data-stu-id="e1b55-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="e1b55-180">Bu davranışı hakkında daha fazla bilgi için kullanıma [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="e1b55-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="e1b55-181">Markdown cmdlet'leri ve işleme</span><span class="sxs-lookup"><span data-stu-id="e1b55-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="e1b55-182">Markdown temel biçimlendirme ile okunabilir düz metin belgeleri oluşturmak için standart bir HTML'e işlenebilecek ' dir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="e1b55-183">Bazı cmdlet'ler konsolunda, Markdown belgeleri işlemek ve dönüştürmek izin 6.1 ekledik dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="e1b55-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="e1b55-184">Örneğin, `Show-Markdown` konsolunda bir Markdown dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e1b55-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Örnek Markdown Göster](./images/markdown_example.png)

<span data-ttu-id="e1b55-186">Bu cmdlet'ler nasıl çalıştığı hakkında daha fazla bilgi için kullanıma [bu RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e1b55-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="e1b55-187">Deneysel özellik bayrakları</span><span class="sxs-lookup"><span data-stu-id="e1b55-187">Experimental feature flags</span></span>

<span data-ttu-id="e1b55-188">Deneysel özellik bayraklarını sonlandırılan henüz özelliklerini etkinleştirme olanağı verir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-188">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="e1b55-189">Bu Deneysel özelliklerin desteklenmez ve hatalar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-189">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="e1b55-190">' Deki bu özellik hakkında daha fazla bilgi [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="e1b55-190">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="e1b55-191">Web cmdlet'i geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="e1b55-191">Web cmdlet improvements</span></span>

<span data-ttu-id="e1b55-192">Performanstan [ @markekraus ](https://github.com/markekraus), bizim web cmdlet'leri için tam bir slew geliştirmeler yapıldı: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="e1b55-192">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="e1b55-193">ve [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="e1b55-193">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="e1b55-194">[Çekme isteği #6109](https://github.com/PowerShell/PowerShell/pull/6109) -UTF-8 için kodlama kümesi varsayılan `application-json` yanıtları</span><span class="sxs-lookup"><span data-stu-id="e1b55-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="e1b55-195">[Çekme isteği # 6018 oluşturun](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` izin vermek için parametre `Content-Type` standartlarıyla uyumlu olmayan üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="e1b55-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="e1b55-196">[Çekme isteği #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` desteklemek için parametre Basitleştirilmiş `multipart/form-data` desteği</span><span class="sxs-lookup"><span data-stu-id="e1b55-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="e1b55-197">[Çekme isteği #6338](https://github.com/PowerShell/PowerShell/pull/6338) - uyumlu, büyük küçük harf duyarsız ilişkisi anahtarlarını işleme</span><span class="sxs-lookup"><span data-stu-id="e1b55-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="e1b55-198">[Çekme isteği #6447](https://github.com/PowerShell/PowerShell/pull/6447) -ekleme `-Resume` web cmdlet'leri için parametre</span><span class="sxs-lookup"><span data-stu-id="e1b55-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="e1b55-199">Uzaktan iletişimini geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="e1b55-199">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="e1b55-200">Kapsayıcılar için PowerShell Direct PowerShell Core kullanmayı dener</span><span class="sxs-lookup"><span data-stu-id="e1b55-200">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="e1b55-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) PowerShell ve ağ bağlantısını veya diğer Uzaktan Yönetim Hizmetleri bir Hyper-V VM veya kapsayıcı bağlanmasına olanak sağlayan Hyper-V özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="e1b55-202">Geçmişte, PowerShell Direct kapsayıcıdaki gelen Windows PowerShell örneğini kullanarak bağlı.</span><span class="sxs-lookup"><span data-stu-id="e1b55-202">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span>
<span data-ttu-id="e1b55-203">Şimdi, PowerShell Direct önce herhangi bir kullanılabilir kullanarak bağlanmayı dener `pwsh.exe` üzerinde `PATH` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="e1b55-203">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="e1b55-204">Varsa `pwsh.exe` değilse kullanılabilir, PowerShell Direct geri kullanmaya döner `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-204">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="e1b55-205">`Enable-PSRemoting` Şimdi Önizleme sürümleri için ayrı bir uzak uç noktası oluşturur</span><span class="sxs-lookup"><span data-stu-id="e1b55-205">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="e1b55-206">`Enable-PSRemoting` Şimdi iki uzaktan oturum yapılandırmaları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e1b55-206">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="e1b55-207">Bir PowerShell ana sürümü.</span><span class="sxs-lookup"><span data-stu-id="e1b55-207">One for the major version of PowerShell.</span></span> <span data-ttu-id="e1b55-208">Örneğin,`PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-208">For example,`PowerShell.6`.</span></span> <span data-ttu-id="e1b55-209">Bağlı "Sistem genelinde" PowerShell 6 oturum yapılandırması alt sürüm güncelleştirmeleri arasında yararlandı bu endpoint</span><span class="sxs-lookup"><span data-stu-id="e1b55-209">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="e1b55-210">Örneğin bir sürüme özgü oturum yapılandırması: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="e1b55-210">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="e1b55-211">Bu davranış, aynı makinede birden çok PowerShell 6 sürümlerinin yüklendiğini ve erişilebilir olmasını istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1b55-211">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="e1b55-212">Ayrıca, Önizleme sürümlerini PowerShell artık kendi uzaktan iletişim oturum yapılandırmaları çalıştırdıktan sonra elde `Enable-PSRemoting` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e1b55-212">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="e1b55-213">Çıkış önce WinRM ayarlamadıysanız farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-213">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="e1b55-214">Ardından Önizleme ayrı PowerShell oturum yapılandırmaları görebilir ve PowerShell 6'ın ve her belirli bir sürümü için kararlı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1b55-214">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

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

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="e1b55-215">`user@host:port` SSH için desteklenen söz dizimleri</span><span class="sxs-lookup"><span data-stu-id="e1b55-215">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="e1b55-216">SSH istemcileri genellikle bir bağlantı dizesi şu biçimde desteklemek `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-216">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="e1b55-217">' Nın eklenmesiyle SSH bir protokol olarak PowerShell uzaktan iletişim için bağlantı dizesinin bu biçimi desteği ekledik:</span><span class="sxs-lookup"><span data-stu-id="e1b55-217">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="e1b55-218">Üzerinde Windows Gezgini Kabuk bağlam menüsü eklemeye MSI seçeneği</span><span class="sxs-lookup"><span data-stu-id="e1b55-218">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="e1b55-219">Performanstan [ @bergmeister ](https://github.com/bergmeister)artık Windows bağlam menüsünden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b55-219">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="e1b55-220">Artık sistem genelinde yüklemenizin PowerShell 6.1, Windows Gezgini'nde herhangi bir klasörden açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1b55-220">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![PowerShell 6 Kabuk bağlam menüsü](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="e1b55-222">İlgi çekici Özellikler</span><span class="sxs-lookup"><span data-stu-id="e1b55-222">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="e1b55-223">"Windows kısayol atlama listesinde yönetici olarak çalıştır"</span><span class="sxs-lookup"><span data-stu-id="e1b55-223">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="e1b55-224">Performanstan [ @bergmeister ](https://github.com/bergmeister), PowerShell Core kısayolun atlama listesi artık "Yönetici olarak çalıştır" içerir:</span><span class="sxs-lookup"><span data-stu-id="e1b55-224">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![PowerShell 6 atlama listesinde yönetici olarak çalıştırın](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="e1b55-226">`cd -` Önceki dizinine döndürür</span><span class="sxs-lookup"><span data-stu-id="e1b55-226">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="e1b55-227">Ya da Linux üzerinde:</span><span class="sxs-lookup"><span data-stu-id="e1b55-227">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="e1b55-228">Ayrıca, `cd` ve `cd --` değiştirmek `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-228">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="e1b55-229">Performanstan [ @iSazonov ](https://github.com/iSazonov), [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet'i, PowerShell Core için unity'nin.</span><span class="sxs-lookup"><span data-stu-id="e1b55-229">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="e1b55-230">`Update-Help` Yönetici olmayan</span><span class="sxs-lookup"><span data-stu-id="e1b55-230">`Update-Help` as non-admin</span></span>

<span data-ttu-id="e1b55-231">Popüler isteğe bağlı olarak `Update-Help` artık yönetici olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-231">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="e1b55-232">`Update-Help` artık bir kullanıcı kapsamlı klasöre Yardım kaydetmek için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="e1b55-232">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="e1b55-233">Yeni yöntemler/özellikler hakkında `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="e1b55-233">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="e1b55-234">Performanstan [ @iSazonov ](https://github.com/iSazonov), yeni yöntemleri ve özellikleri ekledik `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-234">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="e1b55-235">`PSCustomObject` artık bir `Count` / `Length` özelliği gibi diğer nesneler.</span><span class="sxs-lookup"><span data-stu-id="e1b55-235">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="e1b55-236">Bu iş yöntemlerine `ForEach` ve `Where` çalıştırmak ve filtrelemek olanak sağlayan yöntemleri `PSCustomObject` öğeleri:</span><span class="sxs-lookup"><span data-stu-id="e1b55-236">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="e1b55-237">Performanstan @SimonWahlin, ekledik `-Not` parametresi `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-237">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="e1b55-238">Artık bir nesnede bir işlem hattı olmayan-bulunup bulunmadığını bir özelliği ya da null veya boş özellik değeri filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b55-238">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="e1b55-239">Örneğin, bu komut, tanımlanan tüm bağımlı hizmetlerin olmayan tüm hizmetleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="e1b55-239">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="e1b55-240">`New-ModuleManifest` BOM daha az UTF-8 belgesi oluşturur</span><span class="sxs-lookup"><span data-stu-id="e1b55-240">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="e1b55-241">Güncelleştirdik BOM daha az UTF-8'PowerShell 6. 0'de alındığında, `New-ModuleManifest` yerine UTF-16 bir BOM daha az UTF-8 belge oluşturmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e1b55-241">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="e1b55-242">Temsilci PSMethod öğesinden dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e1b55-242">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="e1b55-243">Performanstan [ @powercode ](https://github.com/powercode), artık dönüştürülmesi destekliyoruz bir `PSMethod` içinde bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="e1b55-243">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="e1b55-244">Bu sayede geçirme gibi şeyleri `PSMethod` `[M]::DoubleStrLen` olarak bir temsilci değerde `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="e1b55-244">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

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

<span data-ttu-id="e1b55-245">Bu değişiklikle ilgili daha fazla bilgi için kullanıma [çekme isteği #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="e1b55-245">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="e1b55-246">Standart sapma `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="e1b55-246">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="e1b55-247">Performanstan [ @CloudyDino ](https://github.com/CloudyDino), ekledik bir `StandardDeviation` özelliğini `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="e1b55-247">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

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

<span data-ttu-id="e1b55-248">Performanstan [ @maybe-hello-world ](https://github.com/maybe-hello-world), `Get-PfxCertificate` artık `Password` alan parametresi bir `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-248">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="e1b55-249">Bu, etkileşimli olmayan kullanmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="e1b55-249">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="e1b55-250">Kaldırılmasını `more` işlevi</span><span class="sxs-lookup"><span data-stu-id="e1b55-250">Removal of the `more` function</span></span>

<span data-ttu-id="e1b55-251">Geçmişte, bir işlev üzerinde adlı Windows PowerShell sevk `more` kaydırılan `more.com`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-251">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="e1b55-252">Bu işlev artık kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1b55-252">That function has now been removed.</span></span>

<span data-ttu-id="e1b55-253">Ayrıca `help` işlevi değiştirilen kullanılacak `more.com` Windows ya da sistemin varsayılan çağrı tarafından belirtilen `$env:PAGER` Windows dışı platformlarda.</span><span class="sxs-lookup"><span data-stu-id="e1b55-253">Also the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="e1b55-254">`cd DriveName:` artık bu sürücüye geçerli çalışma dizininde kullanıcıları döndürür</span><span class="sxs-lookup"><span data-stu-id="e1b55-254">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="e1b55-255">Daha önce kullanarak `Set-Location` veya `cd` kullanıcılar söz konusu sürücünün varsayılan konuma gönderilen bir PSDrive penceresine dönün.</span><span class="sxs-lookup"><span data-stu-id="e1b55-255">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="e1b55-256">Performanstan [ @mcbobke ](https://github.com/mcbobke), kullanıcıların son bilinen geçerli çalışma dizini için artık bu oturum için gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-256">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="e1b55-257">Windows PowerShell türü Hızlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="e1b55-257">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="e1b55-258">Windows PowerShell'de, iş ile ilgili kendi türleri daha kolay hale getirmek için aşağıdaki türü Hızlandırıcılar ekledik:</span><span class="sxs-lookup"><span data-stu-id="e1b55-258">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="e1b55-259">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="e1b55-259">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="e1b55-260">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="e1b55-260">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="e1b55-261">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="e1b55-261">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="e1b55-262">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="e1b55-262">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="e1b55-263">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="e1b55-263">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="e1b55-264">Bu tür Hızlandırıcıları PowerShell 6'da bulunmayan, ancak Windows üzerinde çalışan PowerShell 6.1 eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-264">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="e1b55-265">Bu tür AD kolayca oluşturulmasında yararlı olan ve WMI nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e1b55-265">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="e1b55-266">Örneğin, LDAP kullanarak sorgulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1b55-266">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="e1b55-267">Aşağıdaki örnek, bir Win32_OperatingSystem CIM nesnesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e1b55-267">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="e1b55-268">Bu örnek için Win32_OperatingSystem sınıfını bir ManagementClass nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1b55-268">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="e1b55-269">`-lp` diğer tüm `-LiteralPath` parametreleri</span><span class="sxs-lookup"><span data-stu-id="e1b55-269">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="e1b55-270">Performanstan [ @kvprasoon ](https://github.com/kvprasoon), artık bir parametre diğer adını sahibiz `-lp` sahip tüm yerleşik PowerShell cmdlet'lerinin bir `-LiteralPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e1b55-270">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="e1b55-271">Bozucu değişiklikler</span><span class="sxs-lookup"><span data-stu-id="e1b55-271">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="e1b55-272">Windows MSI tabanlı yükleme yollarında</span><span class="sxs-lookup"><span data-stu-id="e1b55-272">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="e1b55-273">Windows üzerinde MSI paketi artık aşağıdaki yola yüklenir:</span><span class="sxs-lookup"><span data-stu-id="e1b55-273">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="e1b55-274">`$env:ProgramFiles\PowerShell\6\` 6.x kararlı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1b55-274">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="e1b55-275">`$env:ProgramFiles\PowerShell\6-preview\` 6.x Önizleme yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1b55-275">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="e1b55-276">Bu değişiklik, PowerShell Core Microsoft Update tarafından güncelleştirilmiş/hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1b55-276">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="e1b55-277">Daha fazla bilgi için kullanıma [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="e1b55-277">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="e1b55-278">Telemetri yalnızca bir ortam değişkeni ile devre dışı bırakılabilir</span><span class="sxs-lookup"><span data-stu-id="e1b55-278">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="e1b55-279">PowerShell Core başlatıldığında temel telemetri verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-279">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="e1b55-280">Veriler, işletim sistemi adı, işletim sistemi sürümü ve PowerShell sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-280">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="e1b55-281">Bu veriler nerede PowerShell kullanılır ve yeni özellikler ve düzeltmeler öncelik sağlıyor ortamları daha iyi anlamak sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="e1b55-281">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="e1b55-282">Çevirme bu telemetri için ortam değişkenini ayarlamak `POWERSHELL_TELEMETRY_OPTOUT` için `true`, `yes`, veya `1`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-282">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="e1b55-283">Dosya silme işlemi artık desteklemiyoruz `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` telemetri devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="e1b55-283">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="e1b55-284">Temel kimlik doğrulaması üzerinden PowerShell uzaktan iletişimini HTTP UNIX platformlarda izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="e1b55-284">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="e1b55-285">Şifrelenmemiş trafik kullanımını önlemek için PowerShell uzaktan iletişimini Unix platformlarında NTLM/anlaşma ya da HTTPS kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1b55-285">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="e1b55-286">Bu değişiklikler hakkında daha fazla bilgi için kullanıma [sorun #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="e1b55-286">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="e1b55-287">Kaldırılan `VisualBasic` desteklenen dilde Add-Type olarak</span><span class="sxs-lookup"><span data-stu-id="e1b55-287">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="e1b55-288">Geçmişte, Visual Basic kod kullanarak derleme `Add-Type` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e1b55-288">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="e1b55-289">Visual Basic ile kullanılan nadiren `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="e1b55-289">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="e1b55-290">PowerShell boyutunu azaltmak için bu özelliği kaldırdık.</span><span class="sxs-lookup"><span data-stu-id="e1b55-290">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="e1b55-291">Kullanımları temizlendi `CommandTypes.Workflow` ve `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="e1b55-291">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="e1b55-292">Bu değişiklikler hakkında daha fazla bilgi için kullanıma [çekme isteği #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="e1b55-292">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>
