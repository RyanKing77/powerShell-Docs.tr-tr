---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsFeatureSet kaynağı"
ms.openlocfilehash: 3cdabc36ef35c2bf912ac54393fe40024a8e8bc0
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet kaynağı

> İçin geçerlidir: Windows PowerShell 5.0

**WindowsFeatureSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), roller ve özellikler eklenemez veya kaldırılamaz hedef düğümde emin olmak için bir mekanizma sağlar.
Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsFeature kaynak](windowsfeatureResource.md) belirtilen her bir özelliğin `Name` özelliği.

Çok sayıda Windows özelliği aynı duruma yapılandırmak istediğinizde bu kaynağı kullanın.

## <a name="syntax"></a>Sözdizimi

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]] 
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   | 
|---|---| 
| Ad| Rolleri veya sağlamak istediğiniz özellikleri adlarını eklenir veya kaldırılır. Bu aynı sonucu verir **adı** özelliği [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet'ini ve rollerin veya özelliklerin görünen adı değil.| 
| kimlik bilgisi| Rolleri veya özellikleri eklemek veya kaldırmak için kullanılacak kimlik bilgileri.| 
| Emin olun| Roller veya özellikler eklenip eklenmeyeceğini gösterir. Roller veya özellikler olduğundan emin olmak için eklenen, ayarlanmış roller veya özellikler kaldırıldığından, emin olmak için "var" Bu özelliği ayarlayın "Yok" özelliğine.| 
| IncludeAllSubFeature| Bu özelliği ayarlamak **$true** ile gerekli tüm alt özellikleri ile belirttiğiniz özellikleri içerecek şekilde **adı** özelliği.| 
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.| 
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.| 
| Kaynak| Gerekiyorsa, yükleme için kullanılacak kaynak dosyasının konumunu belirtir.| 

## <a name="example"></a>Örnek

Aşağıdaki yapılandırma sağlar **Web sunucusu** (IIS) ve **SMTP sunucusu** özellikleri ve her, tüm alt özellikleri yüklenir.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        } 
    }
}
```

