---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsFeature kaynağı"
ms.openlocfilehash: b4f50cb9ee172600b1811175e9cf67f6a7ed2d55
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="dsc-windowsfeature-resource"></a>DSC WindowsFeature kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

**WindowsFeature** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), roller ve özellikler eklenemez veya kaldırılamaz hedef düğümde emin olmak için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   | 
|---|---| 
| Ad| Sağlamak istediğiniz rol veya özellik adını eklenen veya kaldırılan gösterir. Bu aynı sonucu verir __adı__ özelliğinden [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet'ini ve rol veya özellik görünen adı değil.| 
| kimlik bilgisi| Rol veya özellik eklemek veya kaldırmak için kullanılacak kimlik bilgilerini gösterir.| 
| Emin olun| Rol veya özellik eklediyseniz gösterir. Rol veya özellik olduğundan emin olmak için eklenen, ayarlanmış bu özelliğe rol veya özellik kaldırıldığını, emin olmak için "var" olarak ayarlayın "Yok" özelliği.| 
| IncludeAllSubFeature| Bu özelliği ayarlamak __$true__ belirttiğiniz ile gerekli tüm alt özellikleri özellik durumuyla durumunu emin olmak için __adı__ özelliği.| 
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolunu gösterir.| 
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.| 
| Kaynak| Gerekiyorsa, yükleme için kullanılacak kaynak dosyasının konumunu belirtir.| 

## <a name="example"></a>Örnek
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

