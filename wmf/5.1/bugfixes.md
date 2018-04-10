---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: WMF 5.1 hata düzeltmeleri
ms.openlocfilehash: dfd9ead447edfe9b7bdae23be14785df4b182bbc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="e31d4-103">WMF 5.1# hata düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="e31d4-103">Bug Fixes in WMF 5.1#</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="e31d4-104">Hata düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="e31d4-104">Bug fixes</span></span> ##

<span data-ttu-id="e31d4-105">WMF 5.1, aşağıdaki önemli hatalar düzeltildi:</span><span class="sxs-lookup"><span data-stu-id="e31d4-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="e31d4-106">Modül otomatik bulma tam olarak geliştirir `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="e31d4-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span> ###

<span data-ttu-id="e31d4-107">Modül otomatik bulma (bir açık Import-bir komutu çağrılırken Module olmadan otomatik olarak yüklenmesini modüller) WMF 3'te tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="e31d4-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="e31d4-108">Sunulan, PowerShell komutları için iade `$PSHome\Modules` kullanmadan önce `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="e31d4-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="e31d4-109">WMF 5.1 vermenizin Bu davranış değişiklikleri `$env:PSModulePath` tamamen.</span><span class="sxs-lookup"><span data-stu-id="e31d4-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="e31d4-110">Bu kullanıcı tarafından yazılan PowerShell tarafından sağlanan komutları tanımlayan bir modül sağlar (örneğin `Get-ChildItem`) otomatik yüklü olmasını ve doğru şekilde yerleşik komut geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="e31d4-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="e31d4-111">Hiçbir uzun sabit kodları dosya yeniden yönlendirmesi `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="e31d4-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span> ###

<span data-ttu-id="e31d4-112">Tüm önceki sürümlerinde PowerShell, örneğin dosya yeniden yönlendirme operatör tarafından kullanılan dosya kodlamasını denetlemek imkansız `Get-ChildItem > out.txt` PowerShell eklenmiş olduğundan `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="e31d4-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="e31d4-113">WMF 5.1 ile başlayarak, artık dosya yeniden yönlendirme kodlama ayarlayarak değiştirebileceğiniz `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="e31d4-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="e31d4-114">Üyeleri erişimde bir gerileme sabit `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="e31d4-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span> ###

<span data-ttu-id="e31d4-115">WMF 5.0 ile sunulan bir gerileme erişilirken üyeleri ihlal `System.Reflection.RuntimeType`, örneğin `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="e31d4-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="e31d4-116">Bu hatayı WMF 5.1 düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e31d4-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="e31d4-117">COM nesneleri ile giderilen bazı sorunlar</span><span class="sxs-lookup"><span data-stu-id="e31d4-117">Fixed some issues with COM objects</span></span> ###

<span data-ttu-id="e31d4-118">WMF 5.0 COM nesneleri ve COM nesnelerini erişme özelliklerini çağıran yöntemleri için yeni bir COM bağlayıcı sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="e31d4-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="e31d4-119">Bu yeni bağlayıcı performansı önemli ölçüde iyileştirilmiştir, ancak ayrıca WMF 5.1 düzeltilen bazı hatalar sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="e31d4-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="e31d4-120">Bağımsız değişken dönüşümleri her zaman doğru gerçekleştirilen değil</span><span class="sxs-lookup"><span data-stu-id="e31d4-120">Argument conversions were not always performed correctly</span></span> ####

<span data-ttu-id="e31d4-121">Aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="e31d4-121">In the following example:</span></span>

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="e31d4-122">SendKeys yöntemi bir dize bekliyor, ancak PowerShell char bir dize, bunun yerine '1', '7' ve '3' anahtarları gönderme sonuçlandı dönüştürme yapmak için VariantChangeType kullanır IDispatch::Invoke dönüştürme ertelemeyi dönüştürmemenizi Beklenen Volume.Mute anahtarı.</span><span class="sxs-lookup"><span data-stu-id="e31d4-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="e31d4-123">Her zaman doğru bir şekilde ele numaralandırılabilir COM nesneleri</span><span class="sxs-lookup"><span data-stu-id="e31d4-123">Enumerable COM objects not always handled correctly</span></span> ####

<span data-ttu-id="e31d4-124">PowerShell normal olarak çoğu numaralandırılabilir nesneleri numaralandırır Ancak WMF 5.0 ile sunulan bir gerileme IEnumerable arabirimini uygulayan COM nesneleri listesi engelledi.</span><span class="sxs-lookup"><span data-stu-id="e31d4-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="e31d4-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e31d4-125">For example:</span></span>

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="e31d4-126">Yukarıdaki örnekte WMF 5.0 Scripting.Dictionary anahtar/değer çiftlerini numaralandırma yerine ardışık düzenine yanlış yazıldı.</span><span class="sxs-lookup"><span data-stu-id="e31d4-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="e31d4-127">Bu değişiklik ayrıca adresleri [Kurulunca 1752224 sorun](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="e31d4-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="e31d4-128">`[ordered]` sınıfları içinde izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="e31d4-128">`[ordered]` was not allowed inside classes</span></span> ###

<span data-ttu-id="e31d4-129">WMF 5.0 sınıflarda kullanılan türü değişmez değerleri doğrulaması sınıflarıyla sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="e31d4-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="e31d4-130">`[ordered]` türü değişmez değer gibi görünüyor, ancak gerçek bir .NET türü değil.</span><span class="sxs-lookup"><span data-stu-id="e31d4-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="e31d4-131">WMF 5.0 yanlış bir hata bildirdi üzerinde `[ordered]` bir sınıf içinde:</span><span class="sxs-lookup"><span data-stu-id="e31d4-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="e31d4-132">Birden çok sürümünün olduğu konuları hakkında Yardım üzerinde çalışmıyor</span><span class="sxs-lookup"><span data-stu-id="e31d4-132">Help on About topics with multiple versions does not work</span></span> ###

<span data-ttu-id="e31d4-133">WMF modül yüklü birden fazla sürümünü vardı ve bunların tümü Yardım konusunun, örneğin, paylaşılan 5.1, about_PSReadline, önce `help about_PSReadline` gerçek yardımını görüntülemek için belirgin yolu ile birden çok konu döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="e31d4-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="e31d4-134">WMF 5.1 Bu konunun en son sürümü için Yardım döndürerek giderir.</span><span class="sxs-lookup"><span data-stu-id="e31d4-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="e31d4-135">`Get-Help` hangi sürümü için Yardım istediğinizi belirtmek için bir yol sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="e31d4-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="e31d4-136">Bu sorunu çözmek için modülleri dizine gidin ve tercih ettiğiniz Düzenleyicisi gibi bir araçla doğrudan Yardımı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="e31d4-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="e31d4-137">STDIN okuma powershell.exe durdu</span><span class="sxs-lookup"><span data-stu-id="e31d4-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="e31d4-138">Müşteriler `powershell -command -` PowerShell yürütmek için yerel uygulamalar komut dosyasındaki ne yazık ki bu bozuk diğer tüm değişiklikler son STDIN aracılığıyla bu konsolu konak geçirme.</span><span class="sxs-lookup"><span data-stu-id="e31d4-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="e31d4-139">PowerShell.exe başlangıç CPU kullanımında ani oluşturur</span><span class="sxs-lookup"><span data-stu-id="e31d4-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="e31d4-140">PowerShell oturumu gecikmeye neden önlemek için Grup İlkesi aracılığıyla başlattıysanız denetlemek için WMI sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="e31d4-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="e31d4-141">WMI sorgusu yerel saat dilimi bilgilerini almak WMI Win32_Process sınıfı çalışır olduğundan tzres.mui.dll sistem üzerindeki her işlemine injecting yukarı sona erer.</span><span class="sxs-lookup"><span data-stu-id="e31d4-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="e31d4-142">Bu, büyük bir CPU ani wmiprvse (WMI sağlayıcısı ana bilgisayarı) içinde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e31d4-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="e31d4-143">Düzeltme WMI kullanmak yerine aynı bilgi almak için Win32 API çağrıları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e31d4-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>