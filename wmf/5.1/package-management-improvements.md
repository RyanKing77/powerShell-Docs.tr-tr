---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
contributor: jianyunt, quoctruong
title: "WMF 5.1 içinde paket yönetimi geliştirmeleri"
ms.openlocfilehash: b55a1742530b7cd48d60d79b7d4866ebee80a3b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-package-management-in-wmf-51"></a>WMF 5.1# içinde paket yönetimi geliştirmeleri

## <a name="improvements-in-packagemanagement"></a>PackageManagement yenilikleri ##
WMF 5.1 yapılan düzeltmeler şunlardır: 

### <a name="version-alias"></a>Sürüm diğer adı

**Senaryo**: sürüm 1.0 ve 2.0, sisteminizde yüklü bir paketin P1, sahip olduğunuz ve sürüm 1.0 kaldırmak istediğiniz, şunu çalıştırırsınız: `Uninstall-Package -Name P1 -Version 1.0` ve sürüm 1.0 cmdlet'ini çalıştırdıktan sonra kaldırılması için bekler. Ancak sonucu 2.0 sürümünün kaldırılması.  
    
Bu kaynaklanır `-Version` parametredir bir diğer ad `-MinimumVersion` parametresi. En düşük sürüm 1.0 olan tam bir paket için PackageManagement bakıldığında, en son sürümünü döndürür. Bu normal durumlarda istenilen sonucu genellikle en yeni sürüm olduğundan bulma için beklenen davranıştır. Ancak, bunun uygulanması gereken değil `Uninstall-Package` durumda.
    
**Çözüm**: kaldırılan `-Version` tamamen PackageManagement diğer adı (paketini OneGet) ve PowerShellGet. 

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>NuGet sağlayıcısı önyükleme için birden çok komut istemleri

**Senaryo**: çalıştırdığınızda `Find-Module` veya `Install-Module` veya diğer PackageManagement cmdlet'leri PackageManagement ilk kez bilgisayarınızda NuGet sağlayıcı bootstrap dener. PowerShellGet sağlayıcısı NuGet sağlayıcısı ayrıca PowerShell modülleri indirmek için kullandığı için bunu yapar. PackageManagement ardından kullanıcıdan NuGet Sağlayıcısı'nı yüklemek izin ister. Kullanıcı önyüklemesi için "Evet" seçtikten sonra NuGet sağlayıcısının son sürümünün yüklenecek. 
    
Bilgisayarınızda yüklü NuGet Sağlayıcısı'nın eski bir sürümü varsa, ancak bazı durumlarda, eski sürümü NuGet bazen ilk (yani PackageManagement yarış durumu) PowerShell oturumuna yüklenen. Ancak PowerShellGet NuGet sağlayıcısı yeniden bootstrap PackageManagement ister şekilde PowerShellGet çalışmak için NuGet provider'ın sonraki bir sürümünü gerektirir. Bu, NuGet sağlayıcısı önyükleme için birden çok komut istemlerini sonuçlanır.

**Çözüm**: WMF5.1 içinde PackageManagement NuGet sağlayıcısı önyükleme için birden çok komut istemlerini önlemek için NuGet Sağlayıcısı'nın en son sürümü yükler.

Aynı zamanda bu sorunu çözmek, NuGet sağlayıcı (NuGet-Anycpu.exe) eski sürümü el ile silerek sorunu var. $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Yalnızca Intranet erişimi olan bilgisayarlarda PackageManagement için destek

**Senaryo**: Kurumsal senaryo için bir ortamı altında Kişiler çalıştığınız söz konusu olduğunda hiçbir Internet erişimi ancak Intranet yalnızca. PackageManagement bu durumda WMF 5.0 desteklememektedir.

**Senaryo**: içinde WMF 5.0, PackageManagement desteği yalnızca Intranet (ancak Internet'değil) sahip bilgisayarların erişim.

**Çözüm**: WMF 5.1'nde, Intranet bilgisayarların PackageManagement kullanmasına izin vermek için aşağıdaki adımları izleyin:

1. NuGet sağlayıcıyı kullanarak bir Internet bağlantısı olan başka bir bilgisayara kullanarak karşıdan `Install-PackageProvider -Name NuGet`.

2. NuGet sağlayıcısı ya da altında Bul `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` veya `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Intranet bilgisayarına erişmek ve NuGet sağlayıcısıyla yüklemek bir klasör veya ağ paylaşımı konumu ikili dosyaları kopyalamak `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Olay günlüğü geliştirmeleri

Paketleri yüklediğinizde, bilgisayarın durumunu değiştiriyorsunuz. WMF 5.1 PackageManagement şimdi olayları için Windows olay günlüğüne kaydeder `Install-Package`, `Uninstall-Package`, ve `Save-Package` etkinlikler. Olay günlüğü PowerShell, diğer bir deyişle, aynıdır `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Temel kimlik doğrulaması için destek

WMF 5.1, bulma ve temel kimlik doğrulaması gerektiren bir depodan paketler yükleme PackageManagement destekler. Kimlik bilgilerinizi sağlamanız `Find-Package` ve `Install-Package` cmdlet'leri. Örneğin:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Bir proxy'nin arkasında PackageManagement kullanma desteği

WMF 5.1 PackageManagement şimdi yeni proxy kullandığı parametreler `-ProxyCredential` ve `-Proxy`. Bu parametreleri kullanarak proxy URL'si ve PackageManagement cmdlet'leri için kimlik bilgileri belirtebilirsiniz. Varsayılan olarak, sistem proxy ayarları kullanılır. Örneğin:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```

