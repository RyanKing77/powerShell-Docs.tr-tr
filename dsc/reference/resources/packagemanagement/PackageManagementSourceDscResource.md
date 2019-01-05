---
ms.date: 06/20/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC PackageManagementSource kaynak
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048628"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource kaynak

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 Windows PowerShell

**PackageManagementSource** kaynak olarak Windows PowerShell Desired State Configuration (DSC) kaydetmek veya paket Yönetimi kaynakları bir hedef düğümdeki kaydını silmek için bir mekanizma sağlar. **Bu şekilde kayıtlı paket Yönetimi kaynakları, sistem hesabı veya DSC altyapısı tarafından kullanılabilir sistem bağlamı altında kaydedilir.** Bu kaynak gerektiriyor **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.

> [!IMPORTANT]
> **PackageManagement** modülü olmalıdır en az sürüm 1.1.7.0 doğru olması aşağıdaki özellik bilgileri.

## <a name="syntax"></a>Sözdizimi

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Ad| Kayıtlı veya Kayıtsız sisteminizde için paket kaynağının adını belirtir.|
| ProviderName| Paket kaynağı ile birlikte çalışma ile yapabilecekleriniz OneGet sağlayıcısı adını belirtir.|
| SourceLocation| Paket kaynağının URI'sini belirtir.|
| Emin olun| Kayıtlı veya Kayıtsız için paket kaynağı olup olmadığını belirler.|
| InstallationPolicy| Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır. Kaynak paketin güvendiğiniz olup olmadığını belirler. Biri: "Güvenilmeyen", "güvenilir".|
| SourceCredential| Uzak bir kaynak üzerinde paket erişimi sağlar.|

## <a name="example"></a>Örnek

Bu örnekte kaydeder http://nuget.org kaynak paketini kullanarak **PackageManagementSource** DSC kaynağı.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```