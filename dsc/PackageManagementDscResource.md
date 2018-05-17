---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC PackageManagement kaynağı
ms.openlocfilehash: f850c389214fe5adf139c3bd01fb60addc5ec238
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

**PackageManagement** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) yüklemek veya bir hedef düğüm üzerinde paket Yönetimi paketleri kaldırmak için bir mekanizma sağlar. Bu kaynak için gerekli **PackageManagement** modülü, kullanılabilir http://PowerShellGallery.com.

## <a name="syntax"></a>Sözdizimi

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Özellikler
|  Özellik  |  Açıklama   |
|---|---|
| Ad| Yüklenecek veya için paket adını belirtir.|
| Kaynak| Paket bulunabileceği paket kaynağının adını belirtir. Bu bir URI olabilir veya bir kaynak kaydı PackageSource veya PackageManagementSource DSC kaynağı ile kayıtlı. DSC kaynağı MSFT_PackageManagementSource bir paket kaynağı da kaydedebilirsiniz.|
| Emin olun| Paketin yüklü veya kaldırılmış olup olmadığını belirler.|
| RequiredVersion| Yüklemek istediğiniz paketi'nün tam sürümünü belirtir. Bu parametre belirtmezseniz, bu DSC kaynağı MaximumVersion parametresi tarafından belirtilen herhangi bir en fazla sürümünü de karşılayan paketin kullanılabilir en yeni sürümü yükler.|
| MinimumVersion| Yüklemek istediğiniz paketinin sürümünü, izin verilen en düşük belirtir. Bu parametreyi eklemezseniz, bu DSC kaynağı intalls yüksek kullanılabilir paketinin sürümünü, herhangi bir maksimum belirtilen sürümünü de karşılayan MaximumVersion parametresi tarafından belirtilen.|
| MaximumVersion| Yüklemek istediğiniz paketinin sürümünü, izin verilen belirtir. Bu parametre belirtmezseniz, bu DSC kaynağı en yüksek numaralı kullanılabilir paketin sürümünü yükler.|
| SourceCredential | Belirtilen paket sağlayıcısı veya kaynak için bir paketi yüklemek için haklarına sahip bir kullanıcı hesabı belirtir.|
| ProviderName| Paket arama kapsamınızı kurmak için bir paket sağlayıcının adını belirtir. Get-PackageProvider cmdlet'ini çalıştırarak paket sağlayıcı adları elde edebilirsiniz.|
| AdditionalParameters| Bir karma tablosu olarak geçirilen belirli parametreleri sağlayıcı. Örneğin, NuGet sağlayıcısı HedefYolu gibi ek parametreleri geçirebilirsiniz.|

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
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
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