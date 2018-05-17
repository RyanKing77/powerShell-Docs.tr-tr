---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 hata düzeltmeleri
ms.openlocfilehash: 1e46d6d0419b3497450e6eaddbaa47456b004691
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="bug-fixes-in-wmf-51"></a>WMF 5.1# hata düzeltmeleri

## <a name="bug-fixes"></a>Hata düzeltmeleri ##

WMF 5.1, aşağıdaki önemli hatalar düzeltildi:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>Modül otomatik bulma tam olarak geliştirir `$env:PSModulePath` ###

Modül otomatik bulma (bir açık Import-bir komutu çağrılırken Module olmadan otomatik olarak yüklenmesini modüller) WMF 3'te tanıtıldı.
Sunulan, PowerShell komutları için iade `$PSHome\Modules` kullanmadan önce `$env:PSModulePath`.

WMF 5.1 vermenizin Bu davranış değişiklikleri `$env:PSModulePath` tamamen.
Bu kullanıcı tarafından yazılan PowerShell tarafından sağlanan komutları tanımlayan bir modül sağlar (örneğin `Get-ChildItem`) otomatik yüklü olmasını ve doğru şekilde yerleşik komut geçersiz kılma.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Hiçbir uzun sabit kodları dosya yeniden yönlendirmesi `-Encoding Unicode` ###

Tüm önceki sürümlerinde PowerShell, örneğin dosya yeniden yönlendirme operatör tarafından kullanılan dosya kodlamasını denetlemek imkansız `Get-ChildItem > out.txt` PowerShell eklenmiş olduğundan `-Encoding Unicode`.

WMF 5.1 ile başlayarak, artık dosya yeniden yönlendirme kodlama ayarlayarak değiştirebileceğiniz `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Üyeleri erişimde bir gerileme sabit `System.Reflection.TypeInfo` ###

WMF 5.0 ile sunulan bir gerileme erişilirken üyeleri ihlal `System.Reflection.RuntimeType`, örneğin `[int].ImplementedInterfaces`.
Bu hatayı WMF 5.1 düzeltilmiştir.


### <a name="fixed-some-issues-with-com-objects"></a>COM nesneleri ile giderilen bazı sorunlar ###

WMF 5.0 COM nesneleri ve COM nesnelerini erişme özelliklerini çağıran yöntemleri için yeni bir COM bağlayıcı sunmuştur.
Bu yeni bağlayıcı performansı önemli ölçüde iyileştirilmiştir, ancak ayrıca WMF 5.1 düzeltilen bazı hatalar sunulmuştur.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Bağımsız değişken dönüşümleri her zaman doğru gerçekleştirilen değil ####

Aşağıdaki örnekte:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

SendKeys yöntemi bir dize bekliyor, ancak PowerShell char bir dize, bunun yerine '1', '7' ve '3' anahtarları gönderme sonuçlandı dönüştürme yapmak için VariantChangeType kullanır IDispatch::Invoke dönüştürme ertelemeyi dönüştürmemenizi Beklenen Volume.Mute anahtarı.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Her zaman doğru bir şekilde ele numaralandırılabilir COM nesneleri ####

PowerShell normal olarak çoğu numaralandırılabilir nesneleri numaralandırır Ancak WMF 5.0 ile sunulan bir gerileme IEnumerable arabirimini uygulayan COM nesneleri listesi engelledi.  Örneğin:

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

Yukarıdaki örnekte WMF 5.0 Scripting.Dictionary anahtar/değer çiftlerini numaralandırma yerine ardışık düzenine yanlış yazıldı.

Bu değişiklik ayrıca adresleri [Kurulunca 1752224 sorun](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` sınıfları içinde izin verilmiyor ###

WMF 5.0 sınıflarda kullanılan türü değişmez değerleri doğrulaması sınıflarıyla sunmuştur.
`[ordered]` türü değişmez değer gibi görünüyor, ancak gerçek bir .NET türü değil.
WMF 5.0 yanlış bir hata bildirdi üzerinde `[ordered]` bir sınıf içinde:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Birden çok sürümünün olduğu konuları hakkında Yardım üzerinde çalışmıyor ###

WMF modül yüklü birden fazla sürümünü vardı ve bunların tümü Yardım konusunun, örneğin, paylaşılan 5.1, about_PSReadline, önce `help about_PSReadline` gerçek yardımını görüntülemek için belirgin yolu ile birden çok konu döndürecektir.

WMF 5.1 Bu konunun en son sürümü için Yardım döndürerek giderir.

`Get-Help` hangi sürümü için Yardım istediğinizi belirtmek için bir yol sağlamaz.
Bu sorunu çözmek için modülleri dizine gidin ve tercih ettiğiniz Düzenleyicisi gibi bir araçla doğrudan Yardımı görüntüleyin.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>STDIN okuma powershell.exe durdu

Müşteriler `powershell -command -` PowerShell yürütmek için yerel uygulamalar komut dosyasındaki ne yazık ki bu bozuk diğer tüm değişiklikler son STDIN aracılığıyla bu konsolu konak geçirme.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe başlangıç CPU kullanımında ani oluşturur

PowerShell oturumu gecikmeye neden önlemek için Grup İlkesi aracılığıyla başlattıysanız denetlemek için WMI sorgusu kullanır.
WMI sorgusu yerel saat dilimi bilgilerini almak WMI Win32_Process sınıfı çalışır olduğundan tzres.mui.dll sistem üzerindeki her işlemine injecting yukarı sona erer.
Bu, büyük bir CPU ani wmiprvse (WMI sağlayıcısı ana bilgisayarı) içinde sonuçlanır.
Düzeltme WMI kullanmak yerine aynı bilgi almak için Win32 API çağrıları kullanmaktır.
