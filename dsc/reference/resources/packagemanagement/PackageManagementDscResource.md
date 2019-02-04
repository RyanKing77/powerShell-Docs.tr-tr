---
ms.date: 06/20/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC PackageManagement kaynak
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686869"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement kaynak

Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 Windows PowerShell

**PackageManagement** kaynak olarak Windows PowerShell Desired State Configuration (DSC) yüklemek veya bir hedef düğümde paket yönetim paketlerini kaldırmak için bir mekanizma sağlar. Bu kaynak gerektiriyor **PackageManagement** modülü, kullanılabilir [ http://PowerShellGallery.com ](http://PowerShellGallery.com).

> [!IMPORTANT]
> **PackageManagement** modülü olmalıdır en az sürüm 1.1.7.0 doğru olması aşağıdaki özellik bilgileri.

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

| Özellik | Açıklama |
| --- | --- |
| Adı| Yüklenecek veya için paket adını belirtir.|
| AdditionalParameters| Sağlayıcı belirli hashtable için geçirilir parametrelerinin `Get-Package -AdditionalArguments`. Örneğin, NuGet sağlayıcısı DestinationPath gibi ek parametreler geçirebilir.|
| Emin olun| Paket yüklü veya kaldırılmış olup olmadığını belirler.|
| MaximumVersion|Bulmak istediğiniz paketin sürümü izin verilen üst sınırı belirtir. Bu parametreyi eklemezseniz, kaynak paketin en yüksek kullanılabilir sürümü bulur.|
| MinimumVersion|Bulmak istediğiniz paketin sürümü izin verilen en düşük belirtir. Bu parametreyi eklemezseniz, yüksek kullanılabilir sürümü tarafından belirtilen en yüksek herhangi belirtilen sürümü de karşılayan kaynak bulan _MaximumVersion_ parametresi.|
| ProviderName| Paket aramanızın kapsamını yapılacak bir paket sağlayıcı adını belirtir. Çalıştırarak paketin sağlayıcısı adlarını alabilirsiniz `Get-PackageProvider` cmdlet'i.|
| RequiredVersion| Yüklemek istediğiniz paketin'ün tam sürümünü belirtir. Bu parametreyi belirtmezseniz, bu DSC kaynağı tarafından belirtilen herhangi bir en yüksek sürümü de karşılayan paket kullanılabilir en yeni sürümü yükler _MaximumVersion_ parametresi.|
| Kaynak| Paket bulunabileceği paket kaynağının adını belirtir. Bu bir URI olabilir veya bir kaynak kayıtlı `Register-PackageSource` veya PackageManagementSource DSC kaynağı.|
| SourceCredential | Belirtilen paket sağlayıcısı veya kaynak için bir paket yüklemek için haklarına sahip bir kullanıcı hesabı belirtir.|

## <a name="additional-parameters"></a>Ek parametreler

Aşağıdaki tabloda, AdditionalParameters özelliği için seçenekleri listeler.

| Parametre | Açıklama |
| --- | --- |
| DestinationPath| Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır. Yüklenecek paket istediğiniz bir dosya konumu belirtir.|
| InstallationPolicy| Yerleşik Nuget sağlayıcısı gibi sağlayıcıları tarafından kullanılır. Kaynak paketin güvendiğiniz olup olmadığını belirler. Şunlardan biri: `Untrusted`, `Trusted`.|

## <a name="example"></a>Örnek

Bu örnek yükler **JQuery** NuGet paketi ve **GistProvider** PowerShell modülünü kullanarak **PackageManagement** DSC kaynağı. Bu örnekte, önce gerekli paket kaynakları kullanılabilir sonra beklenen durumunu tanımlar sağlar **JQuery** ve **GistProvider** paketleri (NuGet ve PowerShell, sırasıyla).

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