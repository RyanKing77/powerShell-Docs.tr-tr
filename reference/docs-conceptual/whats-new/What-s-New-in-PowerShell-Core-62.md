---
title: PowerShell Core 6.2 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6.2 yayımlanan değişiklikleri
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058106"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="8b6c6-103">PowerShell Core 6.2 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="8b6c6-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="8b6c6-104">PowerShell Core 6.2 yayın performans geliştirmeleri, hata düzeltmeleri ve kalitesini artırmak daha küçük cmdlet'i ve dil geliştirmelerini üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="8b6c6-105">Geliştirmelerinin tam listesi görmek için sunduğumuz ayrıntılı denetle [changelogs](https://github.com/PowerShell/PowerShell/releases) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="8b6c6-106">Deneysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="8b6c6-106">Experimental Features</span></span>

<span data-ttu-id="8b6c6-107">Daha önce için desteği etkinleştirdik [Deneysel Özellikler][].</span><span class="sxs-lookup"><span data-stu-id="8b6c6-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="8b6c6-108">6.2 sürümde denemek için dört Deneysel özellikler sahibiz. Biz geliştirmeler yapmak için lütfen geri bildirim sağlamak ve bu özellik için temel durum yükseltme değer olup olmadığına karar vermek için.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="8b6c6-109">Kullanım `Get-ExperimentalFeature` kullanılabilir Deneysel özellikler listesini almak için.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="8b6c6-110">Etkinleştirin veya bu özellikleri devre dışı `Enable-ExperimentalFeature` ve `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="8b6c6-111">Öneri bulunamadı komutu</span><span class="sxs-lookup"><span data-stu-id="8b6c6-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="8b6c6-112">Bu özellik, komutları veya cmdlet'leri için öneriler, yanlış yazmış olabilirsiniz bulmak için benzer öğe eşleştirmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="8b6c6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b6c6-113">Example</span></span>

<span data-ttu-id="8b6c6-114">Bu örnekte, birkaç önerileri için büyük olasılıkla'den az büyük olasılıkla eşleşen, yanlış yazılmış cmdlet adı belirsiz.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a><span data-ttu-id="8b6c6-115">Örtük uzak iletişim toplu işleme</span><span class="sxs-lookup"><span data-stu-id="8b6c6-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="8b6c6-116">Kullanırken [örtük uzak iletişim](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) bağımsız olarak her komut işlem hattındaki bir işlem hattında, PowerShell değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="8b6c6-117">Nesneleri tekrar tekrar serileştirilmiş ve `de-serialized` istemci ve işlem hattı yürütme üzerinden uzak sistem arasında.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="8b6c6-118">Bu özellik ile PowerShell, komut çalıştırılmasının güvenli olduğundan ve hedef sistemde mevcut belirlemek için işlem hattı analiz eder.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="8b6c6-119">TRUE olduğunda, PowerShell işlem hattının tamamına uzaktan yürütür ve yalnızca serileştirir ve `de-serializes` sonuçları istemciye.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="8b6c6-120">Bir gerçek testi `Get-Process | Sort-Object` localhost üzerinde azaltır 10-15 saniyeden 20-30 **milisaniye**.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="8b6c6-121">Bu özellik yalnızca istemcide etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="8b6c6-122">Değişiklik sunucusunda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="8b6c6-123">Geçici sürücü</span><span class="sxs-lookup"><span data-stu-id="8b6c6-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="8b6c6-124">Farklı işletim sistemlerinde PowerShell Core kullanıyorsanız, geçici dizin bulmak için ortam değişkenini Windows, macOS ve Linux'ta farklı olduğunu keşfedeceksiniz!</span><span class="sxs-lookup"><span data-stu-id="8b6c6-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="8b6c6-125">Bu özellik, size bir [PSDrive][] adlı `Temp:` , otomatik olarak eşleştirilir kullanmakta olduğunuz işletim sistemi için geçici bir klasör.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="8b6c6-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b6c6-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

<span data-ttu-id="8b6c6-127">Unutmayın, yerel dosya komutları (gibi `ls` Linux üzerinde) PSDrives farkında değildir ve bu görmezsiniz `Temp:` sürücü.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="8b6c6-128">Kısaltması genişletme</span><span class="sxs-lookup"><span data-stu-id="8b6c6-128">Abbreviation Expansion</span></span>

<span data-ttu-id="8b6c6-129">PowerShell cmdlet'leri, açıklayıcı adlar olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="8b6c6-130">Bu, yazmak daha zor olan uzun adları sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="8b6c6-131">Bu özellik yalnızca büyük harf karakterler cmdlet'inin yazın ve bir eşleşme bulmak için sekme tamamlamayı kullanma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="8b6c6-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b6c6-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="8b6c6-133">Sekme isabet ve Azure PowerShell'in [Az](https://www.powershellgallery.com/packages/Az) Modülü yüklü için otomatik tamamlama yapar:</span><span class="sxs-lookup"><span data-stu-id="8b6c6-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="8b6c6-134">Bu özellik, etkileşimli olarak kullanılması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="8b6c6-135">Cmdlet'lerin kısaltılmış forms yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="8b6c6-136">Bu özellik, diğer adları yerine kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="8b6c6-137">Hataya Neden Olan Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="8b6c6-137">Breaking Changes</span></span>

- <span data-ttu-id="8b6c6-138">Düzeltme `-NoEnumerate` davranışı `Write-Output` Windows PowerShell ile tutarlı olacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="8b6c6-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-139">(#9069)</span></span>
- <span data-ttu-id="8b6c6-140">Olun `Join-String -InputObject 1,2,3` eşit neden `1,2,3 | Join-String` neden (#8611) (teşekkürler @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="8b6c6-141">Ekleme `-Stable` için `Sort-Object` ve ilgili testler (#7862) (teşekkürler @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="8b6c6-142">Geliştirmek `Start-Sleep` Kesirli saniye kabul etmek için cmdlet'i (#8537) (teşekkürler @Prototyyppi!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="8b6c6-143">Değiştirme olmasını Ordinalıgnorecase kullanılacak hashtable `case-insensitive` bütün kültürler (#8566)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="8b6c6-144">Düzeltme **LiteralPath** içinde `Import-Csv` bağlamak için `Get-ChildItem` çıktı (#8277) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-145">Adı olmayan bir sütunu çift tırnak işareti ayırıcı kullanılırsa artık atlar `Import-Csv` (#7899) (teşekkürler @Topping!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="8b6c6-146">`Get-ExperimentalFeature` artık `-ListAvailable` (#8318) geçiş</span><span class="sxs-lookup"><span data-stu-id="8b6c6-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="8b6c6-147">Parametre şimdi kümeleri hata ayıklama `$DebugPreference` için **devam** yerine **Inquire** (#8195) (teşekkürler @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="8b6c6-148">Uy `-OutputFormat` pwsh ile kullanılan etkileşimli olmayan, yeniden yönlendirilen, kodlanmış komutta belirtilmişse (#8115)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="8b6c6-149">GAC yüklemeye çalışmadan önce modülü taban yoldan bütünleştirilmiş kod yükle (#8073)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="8b6c6-150">Tilde Linux Önizleme paketten Kaldır (#8244)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="8b6c6-151">İşlenmesini taşıma `-WorkingDirectory` profillerinin işlemeden önce (#8079)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="8b6c6-152">Eklemeyin `PATHEXT` UNIX ortam değişkenine (#7697) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="8b6c6-153">Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="8b6c6-153">Known Issues</span></span>

- <span data-ttu-id="8b6c6-154">Uzak Windows IOT ARM platformlarında modülleri yüklenirken bir sorun var.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="8b6c6-155">See (#8053)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="8b6c6-156">Genel güncelleştirme ve düzeltme</span><span class="sxs-lookup"><span data-stu-id="8b6c6-156">General Updates and Fixes</span></span>

- <span data-ttu-id="8b6c6-157">Büyük küçük harfe duyarlı dosya sistemi üzerindeki dosya ve klasörleri için büyük küçük harf duyarsız sekme tamamlamayı etkinleştirme (#8128)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="8b6c6-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="8b6c6-159">Tür çıkarımı için ekleme `$_`  /  `$PSItem` içinde `catch{ }` engeller (#8020) (teşekkürler @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8b6c6-160">Statik yöntem çağırma tür çıkarımı düzeltme (#8018) (teşekkürler @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="8b6c6-161">İçin çıkarsanan tür oluşturma `Select-Object`, `Group-Object`, **PSObject** ve **Hashtable** (#7231) (teşekkürler @powercode!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="8b6c6-162">Destek yöntemi çağrılırken `ByRef-like` tür parametrelerindeki (#7721)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="8b6c6-163">Windows PowerShell modülü yol olduğu zaten ortamın PSModulePath içinde durumu işlemek (#7727)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="8b6c6-164">Etkinleştirme `SecureString` cmdlet'leri için Windows olmayan düz metin depolayarak (#9199)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="8b6c6-165">Windows olmayan hata iletisini clixml securestring ile içeri aktarılırken geliştirmek (#7997)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="8b6c6-166">Parametre ReplyTo eklemek için `Send-MailMessage` (#8727) (teşekkürler @replicaJunction!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="8b6c6-167">Geçersiz ileti Ekle `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="8b6c6-168">Düzeltme `Restart-Computer` üzerinde çalışmak için `localhost` WinRM olmadığında (#9160) sunar.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="8b6c6-169">Olun `Start-Job` throw (#9128) barındırılan PowerShell yüklenirken hata sonlandırılıyor</span><span class="sxs-lookup"><span data-stu-id="8b6c6-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="8b6c6-170">Ekleme C# stili türü hızlandırıcıları ve soneki ushort, uint, ulong ve kısa değişmez değerleri (#7813) (teşekkürler @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8b6c6-171">Sayısal sabit değerleri - eklenen yeni sonekleri bkz [about_Numeric_Literals][] (#7901) (teşekkürler @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8b6c6-172">'(#8209) true olarak ' SupportsShouldProcess ayarlanmadığında etki düzeyi doğru şekilde rapor (teşekkürler @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8b6c6-173">Web cmdlet'leri isteği Charset sorunları düzeltme (#8742) (teşekkürler @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="8b6c6-174">Expect düzeltme `100-continue` Web cmdlet'leri ile ilgili sorun (#8679) (teşekkürler @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="8b6c6-175">Web cmdlet'leri ile dosya engelleme sorunu düzeltme (#7676) (teşekkürler @Claustn!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="8b6c6-176">Kod sayfası ayrıştırma sorunu düzeltme `Invoke-RestMethod` (#8694) (teşekkürler @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="8b6c6-177">Yeniden düzenleme `ConvertTo-Json` JsonObject.ConvertToJson Genel API olarak kullanıma sunmak için (#8682)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="8b6c6-178">Yapılandırılabilir maksimum derinlik ekleme `ConvertFrom-Json` ile - derinliği (#8199) (teşekkürler @louistio!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="8b6c6-179">EscapeHandling parametreyi ekleyin `ConvertTo-Json` cmdlet'i (#7775) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-180">Ekleme `-CustomPipeName` pwsh için ve `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="8b6c6-181">İle Windows üzerinde göreli sembolik bağlantıları oluşturmayı etkinleştirmek `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="8b6c6-182">Yükseltme olmadan çözümlemeyin oluşturmak için geliştirici modunda Windows kullanıcıların (#8534)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="8b6c6-183">Etkinleştirme `Write-Information` kabul edecek şekilde `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="8b6c6-184">Düzeltme `Get-Help` MAML ile gelişmiş işlevleri için Yardım içeriği (#8353)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="8b6c6-185">Düzeltme `Get-Help` PSTypeName sorun - yalnızca bir parametresi (#8754) olarak bildirildiğinde parametre (teşekkürler @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="8b6c6-186">Belirteç hesaplama düzeltme `Get-Help` açıklama Yardım için ScriptBlock üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="8b6c6-187">(#8238) (Thanks @hubuk!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="8b6c6-188">Değişiklik `Get-Help` cmdlet-Parameter parametresi dize kabul eder (#8454) diziler (teşekkürler @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="8b6c6-189">Diskteki yolu içeriyorsa, çağrı CİHAZI alanları (#8571) gidermek (teşekkürler @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="8b6c6-190">Komut isteminde kullanımı eklemek `less` kullanıcı (#7998) çıkma istemek için ' Yardım' işlevindeki</span><span class="sxs-lookup"><span data-stu-id="8b6c6-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="8b6c6-191">Destek enum ve karakter türleri ekleme `Format-Hex` cmdlet'i (#8191) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-192">ShouldProcess öğesinden kaldırmak `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="8b6c6-193">Yeni uzaklık ve sayı parametre eklemek `Format-Hex` ve cmdlet'ini yeniden düzenleme (#7877) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-194">'Bir diğer ad anahtarı olarak 'etiketi' name' izin `ConvertTo-Html`, bir tamsayı olacak şekilde 'width' giriş izin ver (#8426) (teşekkürler @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="8b6c6-195">Yapma scriptblock göre hesaplanan özellikleri yeniden iş `ConvertTo-Html` (#8427) (teşekkürler @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="8b6c6-196">Cmdlet'i eklendi `Join-String` metin (#7660) giriş işlem hattını oluşturmak için (teşekkürler @powercode!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="8b6c6-197">Düzeltme `Join-String` FormatString parametresi mantıksal cmdlet'i (#8449) (teşekkürler @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="8b6c6-198">Değişiklik `Clear-Host` kullanımına geri `$RAWUI` ve Temizle remoting çalışmak için (#8609)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="8b6c6-199">Değişiklik `Clear-Host` yalnızca izin `[console]::clear` ve net bir diğer ad UNIX kaldırma (#8603)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="8b6c6-200">İçinde LiteralPath düzeltme `Import-Csv` bağlamak için `Get-ChildItem` çıktı (#8277) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-201">Yardım işlevi için AliasHelpInfo çağrı kullanmak olmamalıdır (#8552)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="8b6c6-202">Ekleme `-UseMinimalHeader` için `Start-Transcript` döküm üstbilgi en aza indirmek için (#8402) (teşekkürler @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="8b6c6-203">Ekleme `Enable-ExperimentalFeature` ve `Disable-ExperimentalFeature` cmdlet'leri (#8318)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="8b6c6-204">Tüm cmdlet'leri kullanıma **PSDiagnostics** logman.exe kullanılabilir (#8366) ise</span><span class="sxs-lookup"><span data-stu-id="8b6c6-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="8b6c6-205">Kaldırma **kalan** parametresinden `New-PSDrive` üzerinde `non-Windows` Platformu (#8291) (teşekkürler @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="8b6c6-206">İçin destek ekleme `cd +` (#7206) (teşekkürler @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="8b6c6-207">Etkinleştirme `Set-Location -LiteralPath` adlı - klasörlerle ve + (#8089)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="8b6c6-208">`Test-Path` döndürür `$false` boş verildiğinde veya `$null` yolu (#8080) değeri (teşekkürler @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8b6c6-209">Yol herhangi bir sağlayıcı eşleşmiyor olsa bile döndürülecek dinamik parametre izin ver (#7957)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="8b6c6-210">Destek `Get-PSHostProcessInfo` ve `Enter-PSHostProcess` Unix platformlarında (#8232)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="8b6c6-211">Ayırmalar halinde azaltma `Get-Content` cmdlet'i (#8103) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-212">Etkinleştirme `Add-Content` okuma erişimi diğer araçlarla yazılırken içerik paylaşmak için (#8091)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="8b6c6-213">`Get/Add-Content` bir kapsayıcı hedeflenirken Gelişmiş bir hata oluşturur (#7823) (teşekkürler @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="8b6c6-214">Ekleme `-Name`, `-NoUserOverrides` ve `-ListAvailable` parametreleri `Get-Culture` cmdlet'i (#7702) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-215">Tamamlama için birleştirilmiş öznitelik Ekle **kodlama** parametresi.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="8b6c6-216">(#7732) (Thanks @ThreeFive-O!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="8b6c6-217">Sayısal kimlikleri ve kayıtlı kod sayfalarında adını izin **kodlama** parametreleri (#7636) (teşekkürler @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8b6c6-218">Düzeltme `Rename-Item -Path` ile joker karakter (#7398) (teşekkürler @kwkam!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="8b6c6-219">Kullanırken `Start-Transcript` ve dosya var, dosya yerine boş (#8131) silme değerinden (teşekkürler @paalbra!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="8b6c6-220">Olun `Add-Type` açık kaynak dosyalarını içeren **FileAccess.Read** ve **FileShare.Read** açıkça (#7915) (teşekkürler @IISResetMe!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="8b6c6-221">Düzeltme `Enter-PSSession -ContainerId` en son Windows için (#7883)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="8b6c6-222">Olun **NestedModules** özelliği tarafından doldurulan `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="8b6c6-223">Ekleme `%F` için büyük/küçük harf `Get-Date` - UFormat (#7630) (teşekkürler @britishben!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="8b6c6-224">Düzeltme `Set-Service -Status Stopped` bağımlılıkları olan hizmeti durduramadı (#5525) (teşekkürler @zhenggu!)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Deneysel Özellikler]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
