---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: PrereleaseScript
ms.openlocfilehash: 575babd6bc373e99a4e924fafef6e9edeec972d4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-versions-of-scripts"></a>Komut dosyaları uygulamasının yayım öncesi sürümleri

1.6.0 sürümünden başlayarak, PowerShellGet ve PowerShell Galerisi sürümleri bir yayın öncesi olarak 1.0.0 büyük etiketleme için desteği. Bu özellik önce ön öğeleri 0 ile başlayan bir sürüm olması için sınırlı. Bu özellikler için daha fazla destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye doğru sürümleriyle uyumluluk PowerShell sürümleri 3 ve yukarıdaki veya varolan PowerShellGet çiğnemekten olmadan sürüm oluşturma kuralı.
Bu konu betik özgü özelliklerine odaklanmıştır. Modüller için eşdeğer özellikler bulunan [yayın öncesi modül sürümleri](../module/PrereleaseModule.md) konu. Bu özellikleri kullanarak, yayımcılar bir komut dosyası sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra ön sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.

Yüksek düzeyde, yayın öncesi betiği özellikleri içerir:

* Komut dosyası bildiriminde sürüm dizesi PrereleaseString sonek ekleme.
PowerShell Galerisi betikleri yayımlandığında, bu veriler bildirimden ayıklanan ve yayın öncesi öğeleri tanımlamak için kullanılan.
* Yayın öncesi öğeleri alınırken gerektirir - AllowPrerelease bayrağı PowerShellGet komutları Bul-komut dosyası, yükleme betiği ekleme güncelleştirme betiğini ve Kaydet-komut dosyası.
Bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.
* Komut dosyası sürümleri Bul-komut dosyası, Get-InstalledScript tarafından ve PowerShell Galerisi görüntülenen 2.5.0-alpha olduğu gibi PrereleaseString birlikte görüntülenir.

Özellikler için Ayrıntılar aşağıda verilmiştir.


## <a name="identifying-a-script-version-as-a-prerelease"></a>Bir komut dosyası sürüm yayın öncesi tanımlama

Yayın öncesi sürümler için PowerShellGet destek betikler için modülleri kolaydır.
Yayın öncesi dize ekleyerek neden uyumluluk sorunu yok olduklarından betik sürüm yalnızca PowerShellGet tarafından desteklenir.
Bir komut dosyasını bir yayın öncesi olarak PowerShell galerisinde tanımlamak için komut dosyası meta verilerde düzgün biçimlendirilmiş sürüm dizesi için yayın öncesi soneki ekleyin.

Bir komut dosyası bildirimi ön sürümü ile örnek bölümünde aşağıdaki gibi görünür:
```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

Bir yayın öncesi soneki kullanmak için sürüm dizesi aşağıdaki gereksinimleri karşılamalıdır:

* Bir yayın öncesi soneki yalnızca sürüm 3 kesim birincil.İkincil.derleme için olduğunda belirtilebilir. Bu SemVer v1.0.0 ile hizalar
* Yayın öncesi soneki çizgi ile başlayan ve ASCII alfasayısal içerebilir bir dizedir [0-9A-Za - z-]
* Yalnızca SemVer v1.0.0 yayın öncesi dizeler desteklenir şu anda, bu nedenle ön soneki __bulunmamalıdır__ ya da süresi içeren veya + [. +], SemVer 2. 0'verilir
* Desteklenen PrereleaseString dizesi örnekleri:-alfasayısal, - alpha1,-BETA, - update20171020

__Yayın öncesi sürüm etkisini sırası ve yükleme klasörleri sıralama__

Sıralama için PowerShell Galerisi yayımlarken önemlidir, bir yayın öncesi sürüm kullanırken ve PowerShellGet komutları kullanarak komut dosyalarını yüklerken değiştirir.
İki sürüm numarasını sürümleriyle komut dosyaları var, sıralama düzeni tire aşağıdaki dize bölümü dayanır. Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, hangi 2.5.0-gamma değerinden azdır.
İki komut aynı sürüm numarasına sahip ve tek bir PrereleaseString komut dosyası varsa __olmadan__ yayın öncesi soneki üretime hazır sürüm olduğu varsayılır ve yayın öncesi sürümünden daha yüksek bir sürüm olarak sıralanmış Sürüm.
Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak, sürüm göz önünde bulundurulmalı iki daha büyük.

PowerShell Galerisi yayımlama sırasında varsayılan olarak yayımlanmakta komut dosyasının sürümünü PowerShell Galerisi önceden yayımlanan sürümü'den büyük bir sürüm olmalıdır.
Bir yayımcı sürüm 2.5.0-alpha 2.5.0-beta 2.5.0 (ile ön sonek) ile veya güncelleştirebilir.

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Bulma ve PowerShellGet komutları kullanarak ön öğeleri alınıyor

PowerShellGet Bul-komut dosyası, yükleme betiğini güncelleştirmesi-komut dosyası, kullanarak ön öğelerle ilgili ve Kaydet komut gerektirir - AllowPrerelease bayrağı ekleme.
-AllowPrerelease belirtilirse, mevcut olup olmadığını ön öğeleri dahil edilir.
-AllowPrerelease bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.

Yalnızca bu PowerShellGet betik komutlarda Get-InstalledScript ve bazı durumlarda kaldırma komut dosyası ile durumlardır.

* Varsa, get-InstalledScript her zaman otomatik olarak yayın öncesi bilgiler sürüm dizesi içinde gösterir.
* Kaldırma komut dosyası varsayılan olarak kaldırılır bir komut dosyasının en son sürümünü, __hiçbir sürüm__ belirtilir. Bu davranışı değişmemiştir. Ancak, bir yayın öncesi sürüm - RequiredVersion, kullanarak belirtilmişse, - AllowPrerelease gerekli olacaktır.

## <a name="examples"></a>Örnekler
```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

Kaldırma komut dosyası geçerli bir komut dosyası sürümünü kaldırırsanız - RequiredVersion sağlanmadı.
-RequiredVersion belirtilir ve bir yayın öncesi ise, - AllowPrerelease komutu eklenmesi gerekir.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage


```



## <a name="more-details"></a>Daha fazla ayrıntı
### <a name="prerelease-module-versionsmoduleprereleasemodulemd"></a>[Yayın öncesi modül sürümleri](../module/PrereleaseModule.md)
### <a name="find-scriptpsgetfind-scriptmd"></a>[Bulma komut dosyası](./psget_find-script.md)
### <a name="install-scriptpsgetinstall-scriptmd"></a>[Yükleme betiği](./psget_install-script.md)
### <a name="save-scriptpsgetsave-scriptmd"></a>[Kaydet-komut dosyası](./psget_save-script.md)
### <a name="update-scriptpsgetupdate-scriptmd"></a>[Update-script](./psget_update-script.md)
### <a name="get-installedscriptpsgetget-installedscriptmd"></a>[Get-Installedscript](./psget_get-installedscript.md)
### <a name="uninstall-scriptpsgetuninstall-scriptmd"></a>[UnInstall-script](./psget_uninstall-script.md)