---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: DSC PackageManagementSource Resource
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource Resource

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

**PackageManagementSource** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) kaydetmek veya paket Yönetimi kaynakları bir hedef düğümdeki kaydı için bir mekanizma sağlar. **Bu şekilde kayıtlı paket Yönetimi kaynaklarını bağlamında sistem, sistem hesabı veya DSC altyapısı tarafından kullanılabilir kaydedilir.** Bu kaynak için gerekli **PackageManagement** modülü, http://PowerShellGallery.com kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Özellikler
|  Özellik  |  Açıklama   | 
|---|---| 
| Ad| Kayıtlı veya sisteminizde kaydı için paket kaynağı adını belirtir.| 
| Emin olun| Paket kaynağı kaydedildiğinde veya kaydı için olup olmadığını belirler.| 
| InstallationPolicy| Paket kaynağı güven olup olmadığını belirler. Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".| 
| ProviderName| Paket kaynağı ile birlikte çalışma ile yapabilecekleriniz OneGet sağlayıcının adını belirtir.| 
| SourceUri| Paket kaynağının URI belirtir.| 
| SourceCredential| Uzak bir kaynağı üzerinde paket erişim sağlar.| 

## <a name="example"></a>Örnek

Bu örnek http://nuget.org paket kaynağı kullanılarak kaydeder **PackageManagementSource** DSC kaynağı.

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

