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
# <a name="bug-fixes-in-wmf-51"></a>WMF 5.1, hata düzeltmeleri

## <a name="bug-fixes"></a>Hata düzeltmeleri

WMF 5.1 aşağıdaki önemli hatalar düzeltildi:

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>Otomatik bulma modülü PSModulePath tam olarak geliştirir.

Modül otomatik bulma (bir açık içeri aktarma-komutu çağrılırken modülü olmadan otomatik olarak yüklenmesini modülleri) WMF 3'te tanıtıldı. Sunulan, PowerShell komutlarında kontrol `$PSHome\Modules` kullanmadan önce `$env:PSModulePath`.

WMF 5.1 uymanız Bu davranış değişiklikleri `$env:PSModulePath` tamamen. Bu kullanıcı tarafından yazılan PowerShell tarafından sağlanan komutları tanımlayan bir modül sağlar (örn `Get-ChildItem`) otomatik olarak yüklü olmasını ve doğru şekilde yerleşik komut geçersiz kılma.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Hiçbir uzun sabit kodları yeniden yönlendirme dosya-Unicode kodlama

Tüm önceki sürümlerinde PowerShell, dosya yeniden yönlendirme işleciyle kullanılan dosya kodlamasını denetlemek mümkün değildi.

WMF 5.1 ile başlayarak, artık dosya yeniden yönlendirme kodlama ayarlayarak değiştirebilirsiniz `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>System.Reflection.TypeInfo üyeleri erişimde bir gerileme düzeltildi

WMF 5.0 ile sunulan bir gerileme erişen üyeleri kesildi `System.Reflection.RuntimeType`, örneğin, `[int].ImplementedInterfaces`. WMF 5.1 Bu hata düzeltildi.

### <a name="fixed-some-issues-with-com-objects"></a>COM nesneleriyle ilgili bazı sorunlar düzeltildi

WMF 5.0, COM nesneleri ve COM nesneleri erişim özelliklerini çağrılıyor yöntemleri için yeni bir COM bağlayıcı kullanıma sunuldu. Bu yeni bağlayıcı performansı önemli ölçüde geliştirildi ancak hangi WMF 5.1 düzeltilen bazı hatalar de kullanıma sunulmuştur.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Bağımsız değişken dönüşümleri her zaman doğru bir şekilde gerçekleştirilen değil

Aşağıdaki örnekte:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

**SendKeys** yöntemi bir dize bekleniyor, ancak PowerShell değil dönüştürme char bir dizeye dönüştürme erteleniyor **IDispatch::Invoke**, kullanan **VariantChangeType**dönüştürme yapmak için. Bu örnekte, bu anahtarlar, '1', '7' ve '3' beklenen yerine gönderme sonuçlandı. **Volume.Mute** anahtarı.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Her zaman doğru bir şekilde ele numaralandırılabilir COM nesneleri

PowerShell normalde çoğu numaralandırılabilir nesneleri numaralandırır Ancak WMF 5.0 ile sunulan bir gerileme IEnumerable uygulamak COM nesneleri numaralandırmasını engelledi. Örneğin:

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

Yukarıdaki örnekte, WMF 5.0 yanlış yazmış **Scripting.Dictionary** anahtar/değer çiftleri numaralandırma yerine işlem hattına.

### <a name="ordered-was-not-allowed-inside-classes"></a>[sıralı] içindeki sınıflara izin verilmiyor

WMF 5.0 sınıflarda kullanılan türü değişmez değerlerinin doğrulama sınıflarıyla kullanıma sunuldu. `[ordered]` bir tür sabit değer gibi görünüyor, ancak gerçek bir .NET türü değil. WMF 5.0 yanlış bir hata bildirdi üzerinde `[ordered]` bir sınıf içinde:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Hakkında Yardım hakkında konuları birden çok sürümü ile çalışmaz

WMF yüklenen bir modülün birden çok sürümü olan ve tüm bunlar bir Yardım konusu, örneğin, paylaşılan 5.1, about_PSReadline, önce `help about_PSReadline` gerçek yardımını görüntülemek için belirgin bir yolu ile birden çok konu döndürür.

WMF 5.1, bu konunun en son sürümü için Yardım döndürerek düzeltir.

`Get-Help` Yardım için hangi sürümün istediğinizi belirtmek için bir yöntem sağlamaz. Bu sorunu çözmek için modülleri dizine gidin ve tercih ettiğiniz düzenleyiciyi gibi bir araç ile doğrudan Yardımı görüntüleyin.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>STDIN okuma powershell.exe durdu

Müşteriler `powershell -command -` PowerShell yürütmek için yerel uygulamalar betikte STDIN ne yazık ki bu geçirerek diğer değişikliklerden Konsolu ana bozuk.

Bu, Windows 10 Yıldönümü Güncelleştirmesi'nde sürüm 5.1 için sabittir.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe başlangıçta CPU kullanımında ani oluşturur.

PowerShell oturumu gecikme neden olmaktan kaçınmak için Grup İlkesi aracılığıyla başlatılmışsa denetlemek için WMI sorgusu kullanır. WMI sorgusu tzres.mui.dll sistemdeki her işlemine itibaren WMI ekleme yukarı sona erer **Win32_Process** sınıfı yerel saat dilimi bilgilerini almayı dener. Büyük bir CPU ani artış sonuçlanır **wmiprvse** (WMI sağlayıcısı ana bilgisayarı). Düzeltme WMI kullanmak yerine aynı bilgileri almak için Win32 API çağrılarını kullanmaktır.
