---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1, paket yönetimi geliştirmeleri
ms.openlocfilehash: 24ff05d6bf5993826106f1a1d2cee6dad363d1e2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856164"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>WMF 5.1, paket yönetimi geliştirmeleri

WMF 5.1 yapılan düzeltmeler aşağıda verilmiştir:

## <a name="version-alias"></a>Sürüm diğer adı

**Senaryo**: Sürüm 1.0 ve 2.0, sisteminizde yüklü bir paketin olan, P1, sahip olduğunuz ve sürüm 1.0 kaldırmak istediğinizi, çalıştırırsınız `Uninstall-Package -Name P1 -Version 1.0` ve sürüm 1.0 cmdlet'ini çalıştırdıktan sonra kaldırılacak. Bununla birlikte, sürüm 2.0 sonucudur kaldırılır.

Bu durum oluşur `-Version` parametresi, bir diğer adını `-MinimumVersion` parametresi. En düşük sürümü 1.0 olan tam bir paket için PackageManagement bakıldığında, en son sürümünü döndürür. Bu normal durumlarda en son sürümü genellikle istenen sonucu olduğunu bulmak için beklenen bir davranıştır. Bununla birlikte, uygulanması gereken değil `Uninstall-Package` çalışması.

**Çözüm**: kaldırıldı `-Version` diğer tamamen PackageManagement (yani) OneGet) ve PowerShellGet.

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>NuGet sağlayıcısı önyükleme için birden çok istemleri

**Senaryo**: Çalıştırdığınızda `Find-Module` veya `Install-Module` veya diğer PackageManagement cmdlet'leri bilgisayarınızda ilk kez, PackageManagement NuGet sağlayıcısı bootstrap dener. PowerShellGet sağlayıcı NuGet sağlayıcısı ayrıca PowerShell modüllerini yüklemek için kullandığı için bunu yapar.
PackageManagement daha sonra kullanıcı NuGet sağlayıcısını yüklemek izin ister. Kullanıcı önyüklemesi için "Evet" seçtikten sonra NuGet sağlayıcısı en son sürümü yüklenir.

NuGet sağlayıcısı, bilgisayarınızda yüklü eski bir sürümü varsa, ancak bazı durumlarda, eski NuGet bazen ilk (yani PackageManagement yarış durumu) PowerShell oturumuna versiyonu. Ancak, PowerShellGet NuGet sağlayıcısı yeniden önyükleme PackageManagement bu nedenle PowerShellGet çalışmak için NuGet Sağlayıcısı'nın sonraki bir sürümünü gerektirir.
NuGet sağlayıcısı önyükleme için birden çok istemleri sonuçlanır.

**Çözüm**: WMF5.1 PackageManagement NuGet sağlayıcısı önyükleme için birden çok komut istemlerini önlemek için NuGet sağlayıcısı en son sürümünü yükler.

Bu sorunu da çalışabilir, NuGet sağlayıcısı (NuGet Anycpu.exe) eski sürümü el ile silerek sorunu var. $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>PackageManagement desteği yalnızca Intranet erişimi olan bilgisayarlara

**Senaryo**: Kurumsal senaryo için kişinin çalıştığı bir ortamda olduğunda hiçbir Internet erişimi ancak Intranet yalnızca. PackageManagement WMF 5.0 Bu durumda desteklememektedir.

**Senaryo**: WMF 5. 0'da, yalnızca Intranet (ancak Internet değil) olan bilgisayarları PackageManagement desteklememektedir erişim.

**Çözüm**: WMF 5.1, Intranet bilgisayarların, PackageManagement kullanmasına izin vermek için aşağıdaki adımları izleyebilirsiniz:

1. Kullanarak bir Internet bağlantısı olan başka bir bilgisayar kullanarak NuGet sağlayıcısını indir `Install-PackageProvider -Name NuGet`.

2. NuGet sağlayıcısı ya da altında bulma `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` veya `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. İkili dosyaları, Intranet bilgisayar erişmek ve NuGet sağlayıcıyla yüklemeyi bir klasör veya ağ paylaşımı konumu kopyalayın `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


## <a name="event-logging-improvements"></a>Olay günlüğü geliştirmeleri

Paketleri yükleme sırasında bilgisayarın durumunu değiştirmiş olursunuz. WMF 5.1, PackageManagement artık olayları için Windows olay günlüğüne kaydeder `Install-Package`, `Uninstall-Package`, ve `Save-Package` etkinlikler. Olay günlüğü PowerShell, diğer bir deyişle, aynıdır `Microsoft-Windows-PowerShell, Operational`.

## <a name="support-for-basic-authentication"></a>Temel kimlik doğrulaması için destek

WMF 5.1, bulma ve temel kimlik doğrulaması gerektiren bir depodaki paketlerini yükleme PackageManagement destekler. Kimlik bilgilerinizle sağladığınız `Find-Package` ve `Install-Package` cmdlet'leri. Örneğin:

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Bir proxy'nin arkasındayken PackageManagement kullanma desteği

WMF 5.1, PackageManagement artık yeni proxy parametre almayan `-ProxyCredential` ve `-Proxy`. Bu parametreleri kullanarak, PackageManagement cmdlet'leri için kimlik bilgilerini ve proxy URL'si belirtebilirsiniz. Varsayılan olarak, sistem proxy ayarlarını kullanılır. Örneğin:

```powershell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
