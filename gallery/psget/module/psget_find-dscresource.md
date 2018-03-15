---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Find-DscResource
ms.openlocfilehash: 6c5713f122d48e9c9d5e0aa45dc14047afc56102
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="find-dscresource"></a>Find-DscResource

Modüllerdeki DSC kaynakları bulur.

## <a name="description"></a>Açıklama

Bul DscResource cmdlet bulur [istenen durum Yapılandırması'nı (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) kayıtlı depoları öğesinden belirtilen ölçütlerle eşleşen modüllerde bulunan kaynaklar.
Modüllerin her zaman bu cmdlet bulur Bul DscResource yükleme-Bu cmdlet döndürür ve kaynakları içeren modüllerini yüklemek için modülüne iletebildiğiniz bir PSGetDscResourceInfo nesnesi döndürür.

DSC, Windows PowerShell'de, dağıtma ve yazılım hizmetleri için yapılandırma verilerini yönetmek ve bu hizmetleri çalıştırdığınız ortamının yönetilmesi sağlayan yeni bir yönetim platformudur.

İstenen durum Yapılandırması'nı (DSC) kaynaklar, DSC yapılandırması için yapı taşlarını sağlar. Bir kaynak yapılandırılmış (şema) olabilir ve "Bunu yapmak için" yerel Configuration Manager (LCM'yi) çağıran PowerShell Betiği işlevleri içeren özellikleri sunar.

Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucu ayarı olarak belirli bir şey model oluşturabilirsiniz. Grupları, kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve nasıl kullanılmaya kaynaklara yönelik tanımlamak için meta verileri içeren bir yapı düzenler bir DSC modülü, birleştirilir.

- Bul DscResource sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, RequiredVersion, AllVersions.
  - Bu parametreler karşılıklı olarak birbirini dışlar.
  - Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek modülü adıyla izin verilir.
  - RequiredVersion parametresi belirtilmezse, Bul DscResource en düşük bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya modülünün en son sürümünü modülü en son sürümünü döndürür.
  - RequiredVersion parametresi belirtilirse, Bul DscResource yalnızca tam olarak belirtilen sürümle eşleşen modülü sürümünü döndürür.
- Bul DscResource modülü meta filtreleyebilir Tag parametresini ile
- Bul DscResource depo özgü arama dili filtreleyebilir - filtre parametresine sahip.
- Bul DscResource tüm veya az kayıtlı depoları modüllerden filtre uygulayabilirsiniz.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>Örnek komutlar
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

