---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1, hata düzeltmeleri
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856213"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="956d8-103">WMF 5.1, hata düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="956d8-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="956d8-104">Hata düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="956d8-104">Bug fixes</span></span>

<span data-ttu-id="956d8-105">WMF 5.1 aşağıdaki önemli hatalar düzeltildi:</span><span class="sxs-lookup"><span data-stu-id="956d8-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="956d8-106">Otomatik bulma modülü PSModulePath tam olarak geliştirir.</span><span class="sxs-lookup"><span data-stu-id="956d8-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="956d8-107">Modül otomatik bulma (bir açık içeri aktarma-komutu çağrılırken modülü olmadan otomatik olarak yüklenmesini modülleri) WMF 3'te tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="956d8-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="956d8-108">Sunulan, PowerShell komutlarında kontrol `$PSHome\Modules` kullanmadan önce `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="956d8-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="956d8-109">WMF 5.1 uymanız Bu davranış değişiklikleri `$env:PSModulePath` tamamen.</span><span class="sxs-lookup"><span data-stu-id="956d8-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="956d8-110">Bu kullanıcı tarafından yazılan PowerShell tarafından sağlanan komutları tanımlayan bir modül sağlar (örn `Get-ChildItem`) otomatik olarak yüklü olmasını ve doğru şekilde yerleşik komut geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="956d8-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="956d8-111">Hiçbir uzun sabit kodları yeniden yönlendirme dosya-Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="956d8-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="956d8-112">Tüm önceki sürümlerinde PowerShell, dosya yeniden yönlendirme işleciyle kullanılan dosya kodlamasını denetlemek mümkün değildi.</span><span class="sxs-lookup"><span data-stu-id="956d8-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="956d8-113">WMF 5.1 ile başlayarak, artık dosya yeniden yönlendirme kodlama ayarlayarak değiştirebilirsiniz `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="956d8-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="956d8-114">System.Reflection.TypeInfo üyeleri erişimde bir gerileme düzeltildi</span><span class="sxs-lookup"><span data-stu-id="956d8-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="956d8-115">WMF 5.0 ile sunulan bir gerileme erişen üyeleri kesildi `System.Reflection.RuntimeType`, örneğin, `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="956d8-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="956d8-116">WMF 5.1 Bu hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="956d8-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="956d8-117">COM nesneleriyle ilgili bazı sorunlar düzeltildi</span><span class="sxs-lookup"><span data-stu-id="956d8-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="956d8-118">WMF 5.0, COM nesneleri ve COM nesneleri erişim özelliklerini çağrılıyor yöntemleri için yeni bir COM bağlayıcı kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="956d8-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="956d8-119">Bu yeni bağlayıcı performansı önemli ölçüde geliştirildi ancak hangi WMF 5.1 düzeltilen bazı hatalar de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="956d8-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="956d8-120">Bağımsız değişken dönüşümleri her zaman doğru bir şekilde gerçekleştirilen değil</span><span class="sxs-lookup"><span data-stu-id="956d8-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="956d8-121">Aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="956d8-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="956d8-122">**SendKeys** yöntemi bir dize bekleniyor, ancak PowerShell değil dönüştürme char bir dizeye dönüştürme erteleniyor **IDispatch::Invoke**, kullanan **VariantChangeType**dönüştürme yapmak için.</span><span class="sxs-lookup"><span data-stu-id="956d8-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="956d8-123">Bu örnekte, bu anahtarlar, '1', '7' ve '3' beklenen yerine gönderme sonuçlandı. **Volume.Mute** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="956d8-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="956d8-124">Her zaman doğru bir şekilde ele numaralandırılabilir COM nesneleri</span><span class="sxs-lookup"><span data-stu-id="956d8-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="956d8-125">PowerShell normalde çoğu numaralandırılabilir nesneleri numaralandırır Ancak WMF 5.0 ile sunulan bir gerileme IEnumerable uygulamak COM nesneleri numaralandırmasını engelledi.</span><span class="sxs-lookup"><span data-stu-id="956d8-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="956d8-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="956d8-126">For example:</span></span>

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

<span data-ttu-id="956d8-127">Yukarıdaki örnekte, WMF 5.0 yanlış yazmış **Scripting.Dictionary** anahtar/değer çiftleri numaralandırma yerine işlem hattına.</span><span class="sxs-lookup"><span data-stu-id="956d8-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="956d8-128">[sıralı] içindeki sınıflara izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="956d8-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="956d8-129">WMF 5.0 sınıflarda kullanılan türü değişmez değerlerinin doğrulama sınıflarıyla kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="956d8-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="956d8-130">`[ordered]` bir tür sabit değer gibi görünüyor, ancak gerçek bir .NET türü değil.</span><span class="sxs-lookup"><span data-stu-id="956d8-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="956d8-131">WMF 5.0 yanlış bir hata bildirdi üzerinde `[ordered]` bir sınıf içinde:</span><span class="sxs-lookup"><span data-stu-id="956d8-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="956d8-132">Hakkında Yardım hakkında konuları birden çok sürümü ile çalışmaz</span><span class="sxs-lookup"><span data-stu-id="956d8-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="956d8-133">WMF yüklenen bir modülün birden çok sürümü olan ve tüm bunlar bir Yardım konusu, örneğin, paylaşılan 5.1, about_PSReadline, önce `help about_PSReadline` gerçek yardımını görüntülemek için belirgin bir yolu ile birden çok konu döndürür.</span><span class="sxs-lookup"><span data-stu-id="956d8-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="956d8-134">WMF 5.1, bu konunun en son sürümü için Yardım döndürerek düzeltir.</span><span class="sxs-lookup"><span data-stu-id="956d8-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="956d8-135">`Get-Help` Yardım için hangi sürümün istediğinizi belirtmek için bir yöntem sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="956d8-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="956d8-136">Bu sorunu çözmek için modülleri dizine gidin ve tercih ettiğiniz düzenleyiciyi gibi bir araç ile doğrudan Yardımı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="956d8-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="956d8-137">STDIN okuma powershell.exe durdu</span><span class="sxs-lookup"><span data-stu-id="956d8-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="956d8-138">Müşteriler `powershell -command -` PowerShell yürütmek için yerel uygulamalar betikte STDIN ne yazık ki bu geçirerek diğer değişikliklerden Konsolu ana bozuk.</span><span class="sxs-lookup"><span data-stu-id="956d8-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="956d8-139">Bu, Windows 10 Yıldönümü Güncelleştirmesi'nde sürüm 5.1 için sabittir.</span><span class="sxs-lookup"><span data-stu-id="956d8-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="956d8-140">PowerShell.exe başlangıçta CPU kullanımında ani oluşturur.</span><span class="sxs-lookup"><span data-stu-id="956d8-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="956d8-141">PowerShell oturumu gecikme neden olmaktan kaçınmak için Grup İlkesi aracılığıyla başlatılmışsa denetlemek için WMI sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="956d8-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="956d8-142">WMI sorgusu tzres.mui.dll sistemdeki her işlemine itibaren WMI ekleme yukarı sona erer **Win32_Process** sınıfı yerel saat dilimi bilgilerini almayı dener.</span><span class="sxs-lookup"><span data-stu-id="956d8-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="956d8-143">Büyük bir CPU ani artış sonuçlanır **wmiprvse** (WMI sağlayıcısı ana bilgisayarı).</span><span class="sxs-lookup"><span data-stu-id="956d8-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="956d8-144">Düzeltme WMI kullanmak yerine aynı bilgileri almak için Win32 API çağrılarını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="956d8-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
