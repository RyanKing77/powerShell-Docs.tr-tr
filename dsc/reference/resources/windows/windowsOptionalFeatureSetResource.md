---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsOptionalFeatureSet kaynağı
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076982"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet kaynağı

> Uygulama hedefi: Windows PowerShell 5.0

**WindowsOptionalFeatureSet** kaynak olarak Windows PowerShell Desired State Configuration (DSC), isteğe bağlı özellikler hedef düğümde etkinleştirildiğinden emin olmak için bir mekanizma sağlar.
Bu kaynak bir [bileşik kaynak](../../../resources/authoringResourceComposite.md) çağrılarının [WindowsOptionalFeature kaynağı](windowsOptionalFeatureResource.md) belirtilen her bir özellik `Name` özelliği.

Windows isteğe bağlı özellikler aynı duruma yapılandırmak istediğinizde bu kaynağı kullanın.

## <a name="syntax"></a>Sözdizimi

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Adı| Sağlamak istediğiniz özelliklerini adını etkin veya devre dışı gösterir.|
| Emin olun| Özelliklerin etkinleştirilip etkinleştirilmeyeceğini belirtir. Özellikleri olmasını sağlamak için etkin olarak ayarlayın "Etkinleştir" özellikleri devre dışı olduğunu, emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğini.|
| Kaynak| Henüz uygulanmadı.|
| NoWindowsUpdateCheck| DISM özellikleri etkinleştirmek kaynak dosyalarının aranacağı Windows Update (WU) kişiler olup olmadığını belirtir. $True, DISM WU sizinle iletişime değil.|
| RemoveFilesOnDisable| Kümesine **$true** devre dışı bırakılana özelliklerle ilişkili tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır için "Yok").|
| GünlükDüzeyi| Günlüklerde gösterilen maksimum çıktı düzeyini. Kabul edilen değerler şunlardır: "(Yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hataları, uyarıları ve hata ayıklama bilgileri kaydedilir).|
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.|
| dependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini belirtir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
