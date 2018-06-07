---
ms.date: 06/20/2018
keywords: DSC, powershell, yapılandırma, Kur
title: DSC PackageManagement kaynağı
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753796"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 Windows PowerShell

**PackageManagement** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) yüklemek veya bir hedef düğüm üzerinde paket Yönetimi paketleri kaldırmak için bir mekanizma sağlar. Bu kaynak için gerekli **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.

> [!IMPORTANT]
> **PackageManagement** modülü en az olmalıdır sürüm 1.1.7.0 doğru olması aşağıdaki özellik bilgileri.

## <a name="syntax"></a>Sözdizimi

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Ad| Yüklenecek veya için paket adını belirtir.|
| AdditionalParameters| Sağlayıcı belirli hashtable için aktarılabilecek parametrelerinin `Get-Package -AdditionalArguments`. Örneğin, NuGet sağlayıcısı HedefYolu gibi ek parametreleri geçirebilirsiniz.|
| Emin olun| Paketin yüklü veya kaldırılmış olup olmadığını belirler.|
| MaximumVersion|Bulmak istediğiniz paketinin sürümünü, izin verilen belirtir. Bu parametreyi eklemezseniz, kaynak paketinin yüksek kullanılabilir sürümünü bulur.|
| MinimumVersion|Bulmak istediğiniz paketinin sürümünü, izin verilen en düşük belirtir. Bu parametreyi eklemezseniz, yüksek kullanılabilir paketinin sürümünü, tarafından belirtilen tüm maksimum belirtilen sürüm de karşılayan kaynak bulan _MaximumVersion_ parametresi.|
| ProviderName| Paket arama kapsamınızı kurmak için bir paket sağlayıcının adını belirtir. Çalıştırarak paket sağlayıcı adları alabilirsiniz `Get-PackageProvider` cmdlet'i.|
| RequiredVersion| Yüklemek istediğiniz paketi'nün tam sürümünü belirtir. Bu parametre belirtmezseniz, bu DSC kaynağı tarafından belirtilen herhangi bir en fazla sürümünü de karşılayan paketi kullanılabilir en yeni sürümünü yükler _MaximumVersion_ parametresi.|
| Kaynak| Paket bulunabileceği paket kaynağının adını belirtir. Bu bir URI olabilir veya bir kaynak kayıtlı `Register-PackageSource` veya PackageManagementSource DSC kaynağı.|
| SourceCredential | Belirtilen paket sağlayıcısı veya kaynak için bir paketi yüklemek için haklarına sahip bir kullanıcı hesabı belirtir.|

## <a name="additional-parameters"></a>Ek parametreler

Aşağıdaki tabloda AdditionalParameters özelliği için seçenekleri listeler.
|  Parametre  | Açıklama   |
|---|---|
| HedefYolu| Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır. Yüklenecek paket istediğiniz bir dosya konumu belirtir.|
| InstallationPolicy| Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır. Paket kaynağına güveniyorsanız olup olmadığını belirler. Aşağıdakilerden birini: "Güvenilmeyen", "Güvenilen".|

## <a name="example"></a>Örnek

Bu örnek yükler **JQuery** NuGet paketi ve **GistProvider** PowerShell modülünü kullanarak **PackageManagement** DSC kaynağı. Bu örnek ilk gerekli paket kaynaklarını kullanılabilir sonra beklenen durumunu tanımlar sağlar **JQuery** ve **GistProvider** paketleri (NuGet ve PowerShell, sırasıyla).

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```