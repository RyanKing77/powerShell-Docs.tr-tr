---
ms.date: 06/20/2018
keywords: DSC, powershell, yapılandırma, Kur
title: DSC PackageManagementSource kaynağı
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753779"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 Windows PowerShell

**PackageManagementSource** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) kaydetmek veya paket Yönetimi kaynakları bir hedef düğümdeki kaydı için bir mekanizma sağlar. **Bu şekilde kayıtlı paket Yönetimi kaynaklarını bağlamında sistem, sistem hesabı veya DSC altyapısı tarafından kullanılabilir kaydedilir.** Bu kaynak için gerekli **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.

> [!IMPORTANT]
> **PackageManagement** modülü en az olmalıdır sürüm 1.1.7.0 doğru olması aşağıdaki özellik bilgileri.

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
| Ad| Kayıtlı veya sisteminizde kaydı için paket kaynağı adını belirtir.|
| ProviderName| Paket kaynağı ile birlikte çalışma ile yapabilecekleriniz OneGet sağlayıcının adını belirtir.|
| SourceLocation| Paket kaynağının URI belirtir.|
| Emin olun| Paket kaynağı kaydedildiğinde veya kaydı için olup olmadığını belirler.|
| InstallationPolicy| Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır. Paket kaynağına güveniyorsanız olup olmadığını belirler. Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".|
| SourceCredential| Uzak bir kaynağı üzerinde paket erişim sağlar.|

## <a name="example"></a>Örnek

Bu örnek kaydeder http://nuget.org kaynak paketini kullanarak **PackageManagementSource** DSC kaynağı.

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