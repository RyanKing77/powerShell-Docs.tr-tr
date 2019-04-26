---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsFeatureSet kaynağı
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076795"
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet kaynağı

> Uygulama hedefi: Windows PowerShell 5.0

**WindowsFeatureSet** kaynak olarak Windows PowerShell Desired State Configuration (DSC), roller ve Özellikler eklenen veya kaldırılan bir hedef düğümde emin olmak için bir mekanizma sağlar.
Bu kaynak bir [bileşik kaynak](../../../resources/authoringResourceComposite.md) çağrılarının [WindowsFeature kaynağı](windowsfeatureResource.md) belirtilen her bir özellik `Name` özelliği.

Bu kaynak, çok sayıda Windows özelliği aynı duruma yapılandırmak istediğinizde kullanın.

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
| Adı| Rolleri veya özellikleri sağlamak istediğiniz adlarını eklendiğinde veya kaldırıldığında. Bu, aynı **adı** özelliği [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet'ini ve rollerin veya özelliklerin görünen adı değil.|
| Kimlik bilgisi| Rolleri veya özellikleri eklemek veya kaldırmak için kullanılacak kimlik bilgileri.|
| Emin olun| Roller veya özellikler eklenip eklenmeyeceğini gösterir. Rolleri veya özellikleri olmasını sağlamak için ek olarak ayarlayın "Var" rollerin veya özelliklerin kaldırıldığını, emin olmak için bu özelliği ayarlayın özelliğini "Yok".|
| IncludeAllSubFeature| Bu özellik kümesine **$true** ile belirttiğiniz özellikleri ile gerekli tüm alt özellikleri içerecek şekilde **adı** özelliği.|
| LogPath| Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.|
| dependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| Kaynak| Gerekirse yüklenmesi için kullanılacak kaynak dosyasının konumunu gösterir.|

## <a name="example"></a>Örnek

Aşağıdaki yapılandırma, sağlar **Web-Server** (IIS) ve **SMTP sunucusu** özellikleri ve her, tüm alt özellikleri yüklenir.

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
