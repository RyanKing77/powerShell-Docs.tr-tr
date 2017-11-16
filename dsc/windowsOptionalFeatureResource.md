---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsOptionalFeature kaynağı"
ms.openlocfilehash: 388fbe1bc430098d6680902e0b5643243fbf7f4c
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature kaynağı

> İçin geçerlidir: Windows PowerShell 5.0

**WindowsOptionalFeature** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), isteğe bağlı özellikler hedef düğümde etkin olduğundan emin olmak için bir mekanizma sağlar.

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
| Ad| Sağlamak istediğiniz özelliğin adını etkin veya devre dışı olduğunu belirtir.| 
| Emin olun| Özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir. Özellik olduğundan emin olmak için etkinleştirilmişse, Ayarla "Etkinleştir" özelliğini devre dışı bırakıldığından, emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğine.|
| Kaynak| Henüz uygulanmadı.|
| NoWindowsUpdateCheck| DISM Windows Update (WU) bir özelliği etkinleştirmek kaynak dosyalarını ararken kişiler olup olmadığını belirtir. $True, DISM WU başvurun değil.|
| RemoveFilesOnDisable| Kümesine **$true** devre dışı olduğunda özelliği ile ilişkilendirilen tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır "Yok" için).|
| GünlükDüzeyi| Günlüklerde gösterilen maksimum çıktı düzeyini. Kabul edilen değerler şunlardır: "(yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hatalar, uyarılar ve hata ayıklama bilgileri kaydedilir).|
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.| 
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız belirtir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.| 
 



