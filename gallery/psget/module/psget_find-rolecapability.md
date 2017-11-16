---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Bul RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a>Bul RoleCapability

Rol özellikleri modülleri bulur.

## <a name="description"></a>Açıklama
Bul RoleCapability cmdlet'i modüllerdeki PowerShell rol özellikleri bulur. Bul RoleCapability modülleri kayıtlı depoları içinde arar. Bu cmdlet bulduğu her rol özelliği için bir PSGetRoleCapabilityInfo nesnesi döndürür. Rol özelliği içeren modülünü yüklemek için Yükle-modül cmdlet PSGetRoleCapabilityInfo nesnesini geçirebilirsiniz.
PowerShell rol özellikleri, komutları tanımlamak, uygulamaları ve benzeri, bir kullanıcı yalnızca yetecek kadar Yönetim (JEA) uç noktada kullanılamaz. Rol özellikleri .psrc uzantılı dosyaları tarafından tanımlanır.

- Bul RoleCapability sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, RequiredVersion, AllVersions.
  - Bu parametreler karşılıklı olarak birbirini dışlar.
  - Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek modülü adıyla izin verilir.
  - RequiredVersion parametresi belirtilmezse, Bul RoleCapability en düşük bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya modülünün en son sürümünü modülü en son sürümünü döndürür.
  - RequiredVersion parametresi belirtilirse, Bul RoleCapability yalnızca tam olarak belirtilen sürümle eşleşen modülü sürümünü döndürür.
- Bul RoleCapability modülü meta filtreleyebilir Tag parametresini ile
- Bul RoleCapability depo özgü arama dili filtreleyebilir - filtre parametresine sahip.
- Bul RoleCapability tüm veya az kayıtlı depoları modüllerden filtre uygulayabilirsiniz.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Bul RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>Örnek komutlar
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

