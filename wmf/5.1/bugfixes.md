---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1, hata düzeltmeleri
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795377"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="8806d-103">WMF 5.1, hata düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="8806d-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="8806d-104">Hata düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="8806d-104">Bug fixes</span></span>

<span data-ttu-id="8806d-105">WMF 5.1 aşağıdaki önemli hatalar düzeltildi:</span><span class="sxs-lookup"><span data-stu-id="8806d-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="8806d-106">Otomatik bulma modülü tam olarak geliştirir `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="8806d-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span>

<span data-ttu-id="8806d-107">Modül otomatik bulma (bir açık içeri aktarma-komutu çağrılırken modülü olmadan otomatik olarak yüklenmesini modülleri) WMF 3'te tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="8806d-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="8806d-108">Sunulan, PowerShell komutlarında kontrol `$PSHome\Modules` kullanmadan önce `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="8806d-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="8806d-109">WMF 5.1 uymanız Bu davranış değişiklikleri `$env:PSModulePath` tamamen.</span><span class="sxs-lookup"><span data-stu-id="8806d-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="8806d-110">Bu kullanıcı tarafından yazılan PowerShell tarafından sağlanan komutları tanımlayan bir modül sağlar (örn `Get-ChildItem`) otomatik olarak yüklü olmasını ve doğru şekilde yerleşik komut geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="8806d-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="8806d-111">Dosya hiçbir uzun sabit kodları yeniden yönlendirmesi `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="8806d-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span>

<span data-ttu-id="8806d-112">Tüm önceki sürümlerinde PowerShell, örneğin dosya yeniden yönlendirme operatör tarafından kullanılan dosya kodlamasını denetlemek mümkün değildi `Get-ChildItem > out.txt` PowerShell eklenmiş olduğunuzdan `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="8806d-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="8806d-113">WMF 5.1 ile başlayarak, artık dosya yeniden yönlendirme kodlama ayarlayarak değiştirebilirsiniz `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="8806d-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="8806d-114">Üyeleri erişimde bir gerileme düzeltildi `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="8806d-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span>

<span data-ttu-id="8806d-115">WMF 5.0 ile sunulan bir gerileme erişen üyeleri kesildi `System.Reflection.RuntimeType`, örneğin `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="8806d-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="8806d-116">WMF 5.1 Bu hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="8806d-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="8806d-117">COM nesneleriyle ilgili bazı sorunlar düzeltildi</span><span class="sxs-lookup"><span data-stu-id="8806d-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="8806d-118">WMF 5.0, COM nesneleri ve COM nesneleri erişim özelliklerini çağrılıyor yöntemleri için yeni bir COM bağlayıcı kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="8806d-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="8806d-119">Bu yeni bağlayıcı performansı önemli ölçüde geliştirildi ancak hangi WMF 5.1 düzeltilen bazı hatalar de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8806d-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="8806d-120">Bağımsız değişken dönüşümleri her zaman doğru bir şekilde gerçekleştirilen değil</span><span class="sxs-lookup"><span data-stu-id="8806d-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="8806d-121">Aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="8806d-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="8806d-122">Bir dize SendKeys yöntemi bekleniyor, ancak PowerShell char bir dizeye dönüştürme VariantChangeType bunun yerine '1', '7' ve '3' anahtarları gönderme sonuçlandı dönüştürme yapmak için kullandığı IDispatch::Invoke erteleniyor dönüştürmemenizi Beklenen Volume.Mute anahtarı.</span><span class="sxs-lookup"><span data-stu-id="8806d-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="8806d-123">Her zaman doğru bir şekilde ele numaralandırılabilir COM nesneleri</span><span class="sxs-lookup"><span data-stu-id="8806d-123">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="8806d-124">PowerShell normalde çoğu numaralandırılabilir nesneleri numaralandırır Ancak WMF 5.0 ile sunulan bir gerileme IEnumerable uygulamak COM nesneleri numaralandırmasını engelledi.</span><span class="sxs-lookup"><span data-stu-id="8806d-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="8806d-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8806d-125">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="8806d-126">Yukarıdaki örnekte, WMF 5.0 Scripting.Dictionary anahtar/değer çiftleri numaralandırma yerine işlem hattına yanlış yazıldı.</span><span class="sxs-lookup"><span data-stu-id="8806d-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="8806d-127">Bu değişiklik ayrıca adresleri [1752224 CONNECT'te sorunu](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="8806d-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="8806d-128">`[ordered]` içindeki sınıflara izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="8806d-128">`[ordered]` was not allowed inside classes</span></span>

<span data-ttu-id="8806d-129">WMF 5.0 sınıflarda kullanılan türü değişmez değerlerinin doğrulama sınıflarıyla kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="8806d-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="8806d-130">`[ordered]` bir tür sabit değer gibi görünüyor, ancak gerçek bir .NET türü değil.</span><span class="sxs-lookup"><span data-stu-id="8806d-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="8806d-131">WMF 5.0 yanlış bir hata bildirdi üzerinde `[ordered]` bir sınıf içinde:</span><span class="sxs-lookup"><span data-stu-id="8806d-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="8806d-132">Hakkında Yardım hakkında konuları birden çok sürümü ile çalışmaz</span><span class="sxs-lookup"><span data-stu-id="8806d-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="8806d-133">WMF yüklenen bir modülün birden çok sürümü olan ve tüm bunlar bir Yardım konusu, örneğin, paylaşılan 5.1, about_PSReadline, önce `help about_PSReadline` gerçek yardımını görüntülemek için belirgin bir yolu ile birden çok konu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8806d-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="8806d-134">WMF 5.1, bu konunun en son sürümü için Yardım döndürerek düzeltir.</span><span class="sxs-lookup"><span data-stu-id="8806d-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="8806d-135">`Get-Help` Yardım için hangi sürümün istediğinizi belirtmek için bir yöntem sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8806d-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="8806d-136">Bu sorunu çözmek için modülleri dizine gidin ve tercih ettiğiniz düzenleyiciyi gibi bir araç ile doğrudan Yardımı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="8806d-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="8806d-137">STDIN okuma powershell.exe durdu</span><span class="sxs-lookup"><span data-stu-id="8806d-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="8806d-138">Müşteriler `powershell -command -` PowerShell yürütmek için yerel uygulamalar betikte ne yazık ki bu bozuk diğer değişiklikler son STDIN aracılığıyla konsol konağı iletmeden.</span><span class="sxs-lookup"><span data-stu-id="8806d-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="8806d-139">PowerShell.exe başlangıçta CPU kullanımında ani oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8806d-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="8806d-140">PowerShell oturumu gecikme neden olmaktan kaçınmak için Grup İlkesi aracılığıyla başlatılmışsa denetlemek için WMI sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="8806d-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="8806d-141">WMI sorgusu, yerel saat dilimi bilgilerini almak WMI Win32_Process sınıfı çalışır olduğundan tzres.mui.dll sistem üzerindeki her işlem içine ekleme yukarı sona erer.</span><span class="sxs-lookup"><span data-stu-id="8806d-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="8806d-142">Bu, büyük bir CPU ani wmiprvse (WMI sağlayıcısı ana bilgisayarı) içinde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="8806d-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="8806d-143">Düzeltme WMI kullanmak yerine aynı bilgileri almak için Win32 API çağrılarını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8806d-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
