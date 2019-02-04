---
ms.date: 10/17/2017
contributor: keithb
keywords: Galeri, powershell, cmdlet, psget
title: Betikleri uygulamasının yayım öncesi sürümleri
ms.openlocfilehash: 4e7eab682008ed57163c51fe3a61a744b347bef2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683985"
---
# <a name="prerelease-versions-of-scripts"></a>Betikleri uygulamasının yayım öncesi sürümleri

1.6.0 sürümünden itibaren PowerShellGet ve PowerShell Galerisi olarak ön sürüm 1.0.0 büyüktür sürümleri etiketleme için desteği. Bu özelliği önce yayın öncesi paketleri 0 sürümü itibarıyla bulunması sınırlıydı. Bu özellikler için daha büyük destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye dönük uyumluluğu PowerShellGet, PowerShell sürüm 3 ve yukarıdaki veya mevcut sürümlerini bozucu olmadan sürüm oluşturma kuralı. Bu konu, betik özgü özellikler üzerinde odaklanır. Modüller için eşdeğer özellikleri [yayın öncesi modül sürümlerini](module-prerelease-support.md) konu. Bu özellikleri kullanarak yayımcılar bir betik sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra yayım öncesi bir sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.

Yüksek düzeyde, yayın öncesi betik özellikler şunlardır:

- Sürüm dizesi betik bildiriminde PrereleaseString sonek ekleme. PowerShell Galerisi'nde betikleri yayımlandığında, bu verileri bildiriminden ayıklanır ve yayın öncesi paketleri tanımlamak için kullanılan.
- Yayın öncesi paketleri alınıyor gerektirir PowerShellGet komutlarını Find-Script, yükleme betiği, - AllowPrerelease bayrağı ekleme güncelleştirme betiğini ve Save-Script. Bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.
- Find-Script, Get-InstalledScript ve PowerShell Galerisi'ndeki görüntülenen betik sürümleri 2.5.0-alpha olduğu gibi PrereleaseString görüntülenir.

Özellikler için ayrıntıları aşağıda verilmiştir.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Bir yayın öncesi bir betik sürümü tanımlama

Yayın öncesi sürümler için PowerShellGet destek betikler için modülleri kolaydır. Uyumluluk sorunu yok ön dize ekleyerek neden olduğundan betik sürüm oluşturma yalnızca PowerShellGet tarafından desteklenir. Bir komut dosyası ön sürüm olarak PowerShell galerisinde tanımlamak için bir komut dosyası meta verileri doğru şekilde biçimlendirildiğini sürüm dizesi için bir ön eki ekleyin.

Bir örnek bölümü bir komut dosyası bildiriminin yayım öncesi bir sürümü ile aşağıdaki gibi görünür:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Sürüm dizesi bir ön eki kullanmak için aşağıdaki gereksinimleri karşılaması gerekir:

- Bir ön eki yalnızca sürümü Major.Minor.Build için 3 Kesimden olduğunda belirtilebilir.
  Bu SemVer v1.0.0 ile hizalar.
- Ön eki, kısa çizgi ile başlar ve alfasayısal ASCII karakterler içerebilir bir dizedir [0-9A-Za - z-]
- Yalnızca SemVer v1.0.0 ön sürüm dizeleri desteklenir şu anda, bu nedenle ön eki **gerekir** döneme içeren veya + [. +], SemVer 2. 0'verilir
- Desteklenen PrereleaseString dize örnekleridir:-alfa, - alpha1,-BETA, - update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Yayın öncesi sürüm oluşturma sırası ve yükleme klasörleri sıralama etkisi

Sıralama düzeni için PowerShell Galerisi yayımlama sırasında büyük/küçük harf önemlidir, bir ön sürümünü kullanırken ve betikleri PowerShellGet komutlarını kullanarak yüklerken değiştirir. İki sürüm numarasını sürümleriyle komutlar mevcut, kısa çizgi aşağıdaki dize bölümü temel sıralama düzenini temel alır. Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, 2.5.0-gamma değerinden küçük olan küçüktür. İki komut aynı sürüm numarasına sahip ve tek bir PrereleaseString betik varsa **olmadan** üretime hazır sürüm olduğu varsayılır ve yayın öncesi sürümünden büyük bir sürüm olarak sıralanmış, ön eki Sürüm. Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak sürüm değerlendirilir iki büyük.

PowerShell Galerisi'nde yayımlama sırasında varsayılan olarak PowerShell Galerisi önceden yayımlanan sürümü daha büyük bir sürümse yayımlanmakta betik sürümüne sahip olmanız gerekir. Bir yayımcı, sürüm 2.5.0-alpha 2.5.0-beta 2.5.0 (ile ön sonek) ile veya güncelleştirebilir.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Bulma ve PowerShellGet komutlarını kullanarak yayın öncesi paketleri alınıyor

PowerShellGet Find-Script, yükleme betiği, Update-komut dosyası, yayın öncesi paketlerle ilgilenme ve Kaydet komut gerektirir - AllowPrerelease bayrağı ekleme. -AllowPrerelease belirtilmediği takdirde, mevcut değilse yayın öncesi paketleri dahil edilir. -AllowPrerelease bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.

Bunun tek özel durum PowerShellGet betik komutlarında şunlardır: Get-InstalledScript ve kaldırma betiğini ile bazı durumlarda.

- Varsa, get-InstalledScript her zaman otomatik olarak yayın öncesi bilgiler sürüm dizesini gösterir.
- Kaldırma betiği varsayılan olarak kaldırılır en son sürümünü bir betik, **sürüm** belirtilir. Bu davranış değişmemiştir. Ancak, bir ön sürümünü kullanarak belirtilirse `-RequiredVersion`, `-AllowPrerelease` gerekli olacaktır.

## <a name="examples"></a>Örnekler

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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

-RequiredVersion sağlanmazsa, bir komut dosyası geçerli sürümü kaldırma betiği kaldırır.
Belirtilen ve ön sürüm - RequiredVersion, - AllowPrerelease komutu eklenmesi gerekir.

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

- [Yayın öncesi modül sürümleri](module-prerelease-support.md)
- [Bulma komut dosyası](/powershell/module/powershellget/find-script)
- [Yükleme betiği](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Güncelleştirme betiği](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [Kaldırma betiği](/powershell/module/powershellget/uninstall-script)
