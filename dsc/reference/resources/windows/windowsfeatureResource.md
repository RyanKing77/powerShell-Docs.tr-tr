---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsFeature kaynağı
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076710"
---
# <a name="dsc-windowsfeature-resource"></a>DSC WindowsFeature kaynağı

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

**WindowsFeature** kaynak olarak Windows PowerShell Desired State Configuration (DSC), roller ve Özellikler eklenen veya kaldırılan bir hedef düğümde emin olmak için bir mekanizma sağlar.

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
| Adı| Sağlamak istediğiniz rol veya özellik adını eklendiğinde veya kaldırıldığında gösterir. Bu, aynı __adı__ özelliğinden [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet'ini ve rol veya özellik görünen adı değil.|
| Kimlik bilgisi| Rol veya özellik eklemek veya kaldırmak için kullanılacak kimlik bilgilerini belirtir.|
| Emin olun| Rol veya özelliğin eklenip eklenmediğini belirtir. Rol veya özellik olduğundan emin olmak için ek olarak ayarlayın "Var" rol veya özellik kaldırıldığını, emin olmak için bu özelliği ayarlayın "Yok" özelliği.|
| IncludeAllSubFeature| Bu özellik kümesine __$true__ belirttiğiniz ile gerekli tüm alt özellik durumuyla durumunu emin olmak için __adı__ özelliği.|
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolunu gösterir.|
| dependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| Kaynak| Gerekirse yüklenmesi için kullanılacak kaynak dosyasının konumunu gösterir.|

## <a name="example"></a>Örnek
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```