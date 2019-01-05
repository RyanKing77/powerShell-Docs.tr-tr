---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsOptionalFeature kaynağı
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048696"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature kaynağı

> Şunun için geçerlidir: Windows PowerShell 5.0

**WindowsOptionalFeature** kaynak olarak Windows PowerShell Desired State Configuration (DSC), isteğe bağlı özellikler hedef düğümde etkinleştirildiğinden emin olmak için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Ad| Sağlamak istediğiniz özelliğin adını etkin veya devre dışı gösterir.|
| Emin olun| Özelliğin etkin olup olmadığını belirtir. Özelliği olduğundan emin olmak için etkin olarak ayarlayın "Etkinleştir" özellik devre dışıdır emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğini.|
| Kaynak| Henüz uygulanmadı.|
| NoWindowsUpdateCheck| DISM'nin Windows Update (WU) bir özelliği etkinleştirmek kaynak dosyalarının aranacağı kişiler olup olmadığını belirtir. $True, DISM WU sizinle iletişime değil.|
| RemoveFilesOnDisable| Kümesine **$true** devre dışı olduğunda özellikle ilişkilendirilen tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır için "Yok").|
| GünlükDüzeyi| Günlüklerde gösterilen maksimum çıktı düzeyini. Kabul edilen değerler şunlardır: "(Yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hataları, uyarıları ve hata ayıklama bilgileri kaydedilir).|
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.|
| DependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini belirtir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|