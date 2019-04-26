---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085176"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) bilinen sorunlar ve sınırlamalar

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Yeni değişiklik: DSC yapılandırmaları parolaları şifreleme/şifre çözme için kullanılan sertifikaları WMF 5.0 RTM'ye yükledikten sonra çalışmayabilir

WMF 4.0 ve WMF 5.0 Önizleme sürümlerinde DSC parolaları uzunlukta yapılandırmada izin vermez 121'den fazla karakter. DSC bile uzun ve güçlü bir parola istenen kısa parolalarını zorlama. Bu değişiklik, parolalar DSC yapılandırma rastgele uzunlukta olmasını sağlar.

**Çözüm:** Veri şifreleme veya anahtar şifreleme anahtarı kullanım yanı sıra, belge şifreleme Gelişmiş anahtar kullanımı (1.3.6.1.4.1.311.80.1) sertifikayla yeniden oluşturun. TechNet makalesine <https://technet.microsoft.com/library/dn807171.aspx> daha fazla bilgi bulunur.

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>WMF 5.0 RTM'ye yükledikten sonra DSC cmdlet başarısız olabilir

Start-DscConfiguration ve diğer DSC cmdlet'leri WMF 5.0 RTM'ye şu hata ile yükledikten sonra başarısız olabilir:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Çözüm:** (Yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak DSCEngineCache.mof silin:

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>WMF 5.0 RTM'ye WMF 5.0 üretim önizlemesi üzerine yüklenirse, DSC cmdlet'leri çalışmayabilir

**Çözüm:** (Yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırın:
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>Get-DscConfiguration yönteminde kullanırken kararsız bir duruma LCM gidebilirsiniz

Yönteminde LCM ise, Get-DscConfiguration işlenmesini durdurmak için CTRL + C tuşlarına basarak Git LCM neden olabilir, DSC cmdlet'leri çoğunu bir kararsız duruma gibi çalışmaz.

**Çözüm:** Get-DscConfiguration cmdlet'i hata ayıklama sırasında CTRL + C tuşlarına basın yok.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration yönteminde yanıtlayamayabilir

Yönteminde LCM ise bir işlem durdurulmaya çalışılırken Get-DscConfiguration başlatılırken Stop-DscConfiguration yanıtlayamayabilir

**Çözüm:** Son bölümde açıklandığı gibi Get-DscConfiguration tarafından başlatılan işlem hata ayıklama '[hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource)'.

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Hiçbir ayrıntılı hata iletilerini yönteminde gösterilir

LCM yönteminde, DSC kaynaklarından herhangi bir ayrıntılı hata iletisi görüntülenir.

**Çözüm:** Devre dışı *DebugMode* kaynaktan ayrıntılı iletileri görüntülemek için

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Invoke-DscResource işlemler Get-DscConfigurationStatus cmdlet'i tarafından geri alınamaz

Herhangi bir kaynağın yöntemleri doğrudan çağırmak için Invoke-DscResource cmdlet'i kullandıktan sonra bu işlemi kayıtlarını Get-DscConfigurationStatus daha sonraki bir zamanda alınamıyor.

**Çözüm:** Yok.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus döndürür çekme döngüsü işlemleri türü olarak *tutarlılık*

Bir düğüm her çekme işleminde gerçekleştirilen, ÇEKME yenileme moduna ayarlandığında Get-DscConfigurationStatus cmdlet'i işlem türü olarak raporlar *tutarlılık* yerine *ilk*

**Çözüm:** Yok.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Invoke-DscResource cmdlet'i üretilmiş olan sırayla ileti döndürmez

Invoke-DscResource cmdlet uyarı, ayrıntılı döndürmüyor ve LCM veya DSC kaynağı tarafından üretilmiş olan sırayla hata iletileri.

**Çözüm:** Yok.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>DSC kaynakları kolayca Invoke-DscResource ile kullanıldığında ayıklanamıyor

LCM hata ayıklama modunda çalışırken (bkz [hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource) daha fazla ayrıntı için), Invoke-DscResource cmdlet'i, hata ayıklama için bağlanmak için çalışma alanı hakkında bilgi vermek değil.
**Çözüm:** Bulma ve cmdlet'lerini kullanarak bir çalışma ekleme **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-çalışma** ve **hataayıklama-çalışmaalanı** DSC kaynak hata ayıklamak için.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Aynı kaynak adları aynı düğüm için çeşitli kısmi yapılandırma belgelerini sahip olamaz

Tek bir düğüme dağıtılır birkaç kısmi yapılandırmalar için kaynakları neden aynı adları çalıştırma hatası.

**Çözüm:** Kısmi farklı yapılandırmalarda bile aynı kaynakları için farklı adlar kullanın.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration – UseExisting çalışmıyor - ile kimlik bilgisi

Start-DscConfiguration – UseExisting parametresiyle birlikte kullanıldığında Credential parametresi yok sayıldı. DSC, işleme devam etmek için varsayılan işlem kimliğini kullanır. Uzak düğüm üzerinde devam etmek için farklı bir kimlik bilgisi gerektiğinde bu hataya neden olur.

**Çözüm:** CIM oturumu, uzak DSC işlemleri için kullanın:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>DSC yapılandırmaları düğüm adları olarak IPv6 adresleri

IPv6 adresleri DSC yapılandırma betiklerini düğüm adları olarak bu sürümde desteklenmez.

**Çözüm:** Yok.

## <a name="debugging-of-class-based-dsc-resources"></a>Sınıf tabanlı DSC kaynaklarında hata ayıklama

DSC kaynakları sınıf tabanlı hata ayıklama bu sürümde desteklenmiyor.

**Çözüm:** Yok.

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Değişkenleri İşle & vleri DSC sınıf tabanlı kaynak $script kapsamda tanımlanan birden çok çağrı DSC kaynak arasında korunmaz

Yapılandırma değişkenleri veya $script kapsamında tanımlanan işlevleri olan tüm sınıf tabanlı kaynak kullanıyorsa, birden çok ardışık Başlat-DSCConfiguration çağrı başarısız olur.

**Çözüm:** Tüm değişkenlerin ve işlevlerin DSC kaynak kendisini tanımlayan sınıf. No $script kapsam değişkenleri/işlevler.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>DSC kaynak bir kaynak PSDscRunAsCredential kullanılırken hata ayıklama

DSC kaynak bir kaynak kullanılırken hata ayıklama *PSDscRunAsCredential* Yapılandırma özelliği bu sürümde vnet'i değil.

**Çözüm:** Yok.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential bileşik DSC kaynakları için desteklenmiyor

**Çözüm:** Kimlik bilgisi özelliği varsa kullanın. Örnek ServiceSet ve WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource-söz dizimi* PsDscRunAsCredential doğru şekilde yansıtmaz

Get-DscResource-söz dizimi yansıtmıyor PsDscRunAsCredential doğru kaynak zorunlu olarak işaretler ya da bunu desteklemiyor.

**Çözüm:** Yok. Ancak, işe yapılandırmasında yazma PsDscRunAsCredential özelliği doğru meta verilerini IntelliSense kullanırken'yansıtır.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature Windows 7'de kullanılamıyor

WindowsOptionalFeature DSC kaynak, Windows 7'de kullanılamıyor. Bu kaynak, DISM modülünü ve Windows 8 Windows işletim sisteminin daha yeni sürümlerde başlayarak kullanılabilir olan DISM cmdlet'leri gerektirir.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Sınıf tabanlı DSC kaynakları için Import-DscResource - ModuleVersion beklendiği gibi çalışmayabilir

Derleme düğümü DSC kaynak sınıf tabanlı modülü birden fazla sürümü varsa `Import-DscResource -ModuleVersion` belirtilen sürümde çekme değil ve aşağıdaki derleme hatasına neden olur.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Çözüm:** Tanımlayarak gerekli sürümü alma *ModuleSpecification* nesnesini `-ModuleName` ile `RequiredVersion` gibi belirtilen bir anahtarı:

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Registry kaynağı gibi bazı DSC kaynakları isteği işlemek için uzun süren başlayabilir.

**Resolution1:** Aşağıdaki klasörü düzenli aralıklarla temizleyen bir zamanlama görev oluşturun.

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolution2:** Temizlemek için DSC yapılandırmasını değiştirmek *CommandAnalysis* yapılandırmanın sonunda klasör.

``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
