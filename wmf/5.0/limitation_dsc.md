---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: f39328b240a36deb40d484c4aedb889cee91dc8d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>İstenen durum yapılandırması (DSC) bilinen sorunlar ve sınırlamalar

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Yeni değişiklik: DSC yapılandırmaları parolalarda şifreleme/şifre çözme için kullanılan sertifikaları WMF 5.0 RTM yükledikten sonra çalışmayabilir
--------------------------------------------------------------------------------------------------------------------------------

WMF 4.0 ve WMF 5.0 Önizleme sürümlerde DSC parolaları uzunlukta yapılandırmasında izin vermez birden fazla 121 karakter. DSC uzun ve güçlü parola gerekli olsa bile kısa parolalarını zorlama. Bu önemli değişiklik parolaları DSC yapılandırması, rastgele uzunlukta olmasını sağlar.

**Çözüm:** verileri şifreleme veya anahtar şifreleme anahtarı kullanımını ve belge şifreleme Gelişmiş anahtar kullanımı (1.3.6.1.4.1.311.80.1) sertifikayla yeniden oluşturun. TechNet makalesine <https://technet.microsoft.com/en-us/library/dn807171.aspx> daha fazla bilgi bulunur.


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC cmdlet'leri WMF 5.0 RTM yükledikten sonra başarısız olabilir
------------------------------------------------------------------------------------
Başlangıç DscConfiguration ve diğer DSC cmdlet'lerini şu hata ile WMF 5.0 RTM yükledikten sonra başarısız olabilir:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak DSCEngineCache.mof silin:
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>WMF 5.0 RTM WMF 5.0 üretim Önizleme üzerinde yüklüyse, DSC cmdlet'leri çalışmayabilir.
------------------------------------------------------
**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırın:
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM'yi yönteminde Get-DscConfiguration kullanırken kararsız bir duruma gidebilirsiniz
-------------------------------------------------------------------------------

LCM'yi yönteminde ise, Get-DscConfiguration işlenmesini durdurmak için CTRL + C tuşlarına basarak gitmek LCM'yi neden olabilir bir kararsız duruma gibi bu DSC cmdlet'leri çoğunluğu çalışmaz.

**Çözüm:** Get-DscConfiguration cmdlet'i hata ayıklama sırasında CTRL + C tuşlarına yok.


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a>Stop-DscConfiguration yönteminde kilitlenebilir
------------------------------------------------------------------------------------------------------------------------
LCM'yi yönteminde ise, Get-DscConfiguration tarafından başlatılan bir işlem durdurulmaya çalışılırken sırasında durdurma DscConfiguration kilitlenebilir

**Çözüm:** bölümde özetlendiği gibi Get-DscConfiguration tarafından başlatılan işlem hata ayıklaması son '[hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource)'.


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Yönteminde hiçbir ayrıntılı hata iletileri gösterilir
-----------------------------------------------------------------------------------
LCM'yi yönteminde ise, DSC kaynaklarından herhangi bir ayrıntılı hata iletisi görüntülenir.

**Çözüm:** devre dışı *DebugMode* kaynaktan ayrıntılı iletiler görmek için


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Get-DscConfigurationStatus cmdlet'i tarafından çağırma DscResource işlemler alınamıyor
--------------------------------------------------------------------------------------
Invoke-DscResource cmdlet'i herhangi kaynağın yöntemlerini doğrudan çağırmak için kullandıktan sonra bu tür işlemi kayıtları Get-DscConfigurationStatus daha sonraki bir zamanda alınamıyor.

**Çözüm:** yok.


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus döndürür çekme döngüsü işlemleri türü olarak *tutarlılık*
---------------------------------------------------------------------------------
Bir düğüm gerçekleştirilen, her bir çekme işlemin ÇEKME yenileme modu ayarlandığında Get-DscConfigurationStatus cmdlet'i işlemi türü olarak raporlar *tutarlılık* yerine *ilk*

**Çözüm:** yok.

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Çağırma DscResource cmdlet üretilmiş olan sırada ileti döndürmüyor
---------------------------------------------------------------------------------
Invoke-DscResource cmdlet'i uyarı, ayrıntılı döndürmüyor ve LCM'yi veya DSC kaynağı tarafından üretilmiş olan sırada bir hata iletileri.

**Çözüm:** yok.


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>DSC kaynakları kolayca Invoke-DscResource ile kullanıldığında hata ayıklaması yapılabilir olamaz
-----------------------------------------------------------------------
Hata ayıklama modunda LCM'yi çalışırken (bkz [hata ayıklama DSC kaynakları](https://msdn.microsoft.com/powershell/dsc/debugresource) daha fazla ayrıntı için), Invoke-DscResource cmdlet'i hata ayıklama için bağlanmak için çalışma alanı hakkında bilgi vermek değil.
**Çözüm:** bulma ve cmdlet'lerini kullanarak çalışma attach **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-çalışma** ve  **Hata ayıklama çalışma** DSC kaynağı hata ayıklamak için.

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


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Çeşitli kısmi yapılandırma belgeleri aynı düğüm için aynı kaynak adları olamaz
------------------------------------------------------------------------------------------

Tek bir düğüme dağıtılan birkaç kısmi yapılandırmaları için kaynakları neden aynı adlarını çalıştırma hatası.

**Çözüm:** farklı kısmi yapılandırmalarında bile aynı kaynakları için farklı adlar kullanın.


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Başlangıç DscConfiguration – UseExisting çalışmıyor ile - kimlik bilgisi
------------------------------------------------------------------

Başlangıç DscConfiguration – UseExisting parametresiyle kullanırken kimlik bilgisi parametresi yoksayılır. DSC işlemi devam etmek için varsayılan işlem kimliğini kullanır. Uzak düğümde devam etmek için farklı bir kimlik bilgisi gerektiğinde bu hataya neden olur.

**Çözüm:** kullanım CIM oturumu uzak DSC işlemler için:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6 adresleri DSC yapılandırmalarında düğüm adı olarak
--------------------------------------------------
IPv6 adresleri düğüm adları DSC yapılandırma komut olarak bu sürümde desteklenmez.

**Çözüm:** yok.


<a name="debugging-of-class-based-dsc-resources"></a>Sınıf tabanlı DSC kaynakları hata ayıklama
--------------------------------------
Sınıf tabanlı DSC kaynakları hata ayıklama bu sürümde desteklenmiyor.

**Çözüm:** yok.


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Değişkenleri & DSC sınıf tabanlı kaynak $script kapsamda tanımlanan işlevleri DSC kaynağı için birden fazla çağrı arasında korunmaz 
-------------------------------------------------------------------------------------------------------------------------------------

Yapılandırma değişkenleri veya işlevleri $script kapsamda tanımlı olan tüm sınıf tabanlı kaynak kullanıyorsa, başlangıç DSCConfiguration birden çok ardışık çağrıları başarısız olur.

**Çözüm:** tüm değişkenleri ve işlevleri DSC kaynağı sınıfında kendisini tanımlayın. No $script kapsam değişkenleri/işlevler.


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>DSC kaynağı bir kaynak PSDscRunAsCredential kullanılırken hata ayıklama
----------------------------------------------------------------------
Bir kaynak kullanırken DSC kaynak hata ayıklama *PSDscRunAsCredential* yapılandırma özelliğinde desteklenen bu sürümde değil.

**Çözüm:** yok.


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential DSC bileşik kaynaklar için desteklenmiyor
----------------------------------------------------------------

**Çözüm:** kullanım kimlik bilgisi özelliği varsa. Örnek ServiceSet ve WindowsFeatureSet


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource-sözdizimi* PsDscRunAsCredential doğru şekilde yansıtmaz
-------------------------------------------------------------------------
Get-DscResource-sözdizimi değil yansıtacak PsDscRunAsCredential doğru kaynak zorunlu olarak işaretler veya bunu desteklemiyor.

**Çözüm:** yok. Ancak, işe yapılandırmasında yazma PsDscRunAsCredential özelliği hakkında doğru meta veri IntelliSense kullanırken'yansıtır.


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>Windows 7'de WindowsOptionalFeature kullanılamıyor
-----------------------------------------------------

WindowsOptionalFeature DSC kaynağı, Windows 7'de kullanılamaz. Bu kaynak DISM modülünü ve Windows 8 ve Windows işletim sisteminin daha yeni sürümleri başlayarak kullanılabilir DISM cmdlet'leri gerektirir.

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Sınıf tabanlı DSC kaynakları için içeri aktarma DscResource - ModuleVersion beklendiği gibi çalışmayabilir.   
------------------------------------------------------------------------------------------
Derleme düğümü bir sınıf tabanlı DSC kaynağı modülü, birden fazla sürümü varsa `Import-DscResource -ModuleVersion` belirtilen sürüm çekme değil ve aşağıdaki derleme hata neden olur.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Çözüm:** tanımlayarak gerekli sürümü alma *ModuleSpecification* nesnesini `-ModuleName` ile `RequiredVersion` gibi belirtilen anahtarı:
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Kayıt defteri kaynak gibi bazı DSC kaynakları isteğini işlemek için uzun zaman başlayabilir.
--------------------------------------------------------------------------------------------------------------------------------

**Resolution1:** aşağıdaki klasörü düzenli aralıklarla temizlenir bir zamanlama görevi oluşturun.
``` PowerShell 
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis 
```

**Resolution2:** temizlemek için DSC yapılandırmasını değiştirme *CommandAnalysis* yapılandırmasının sonunda klasör.
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

