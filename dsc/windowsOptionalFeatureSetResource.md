---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsOptionalFeatureSet kaynağı"
ms.openlocfilehash: 3bf6a993d0ec9ce71c1e9222ddaa3bb429accb15
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet kaynağı

> İçin geçerlidir: Windows PowerShell 5.0

**WindowsOptionalFeatureSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), isteğe bağlı özellikler hedef düğümde etkin olduğundan emin olmak için bir mekanizma sağlar. Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsOptionalFeature kaynak](windowsOptionalFeatureResource.md) belirtilen her bir özelliğin `Name` özelliği.

Çok sayıda Windows isteğe bağlı özelliği aynı duruma yapılandırmak istediğinizde bu kaynağı kullanın.

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
| Ad| Sağlamak istediğiniz özellikleri adını etkin veya devre dışı gösterir.| 
| Emin olun| Özelliklerin etkinleştirilip etkinleştirilmeyeceğini belirtir. Özellikleri olduğundan emin olmak için etkinleştirilmişse, ayarlanmış "Etkinleştir" özellikleri devre dışı olduğunu, emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğine.|
| Kaynak| Henüz uygulanmadı.|
| NoWindowsUpdateCheck| DISM Windows Update (WU) özelliklerini etkinleştirmek kaynak dosyalarını ararken kişiler olup olmadığını belirtir. $True, DISM WU başvurun değil.|
| RemoveFilesOnDisable| Kümesine **$true** bunlar devre dışı bırakıldığında özelliklerle ilişkili tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır "Yok" için).|
| GünlükDüzeyi| Günlüklerde gösterilen maksimum çıktı düzeyini. Kabul edilen değerler şunlardır: "(yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hatalar, uyarılar ve hata ayıklama bilgileri kaydedilir).|
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.| 
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız belirtir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.| 
 



