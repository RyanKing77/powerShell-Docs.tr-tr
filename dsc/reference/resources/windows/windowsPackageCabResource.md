---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsPackageCab kaynağı
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076948"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab kaynağı

> Uygulama hedefi: Windows PowerShell 5.1 ve üzeri

**WindowsPackageCab** kaynak olarak Windows PowerShell Desired State Configuration (DSC) yüklemek veya bir hedef düğümde Windows dolap (.cab) paketleri kaldırmak için bir mekanizma sağlar.

Hedef düğüm DISM PowerShell Modülü yüklü olmalıdır. Bilgi için [Windows PowerShell DISM kullanım](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


## <a name="syntax"></a>Sözdizimi

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Adı| Belirli bir durumu sağlamak istediğiniz için paket adını belirtir.|
| Emin olun| Paketin yüklü olup olmadığını gösterir. Bu özelliği "Yok" paketi yüklü emin olun (veya paket yüklüyse kaldırmak için) olarak ayarlayın. "Paket yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.|
| Yol| Paketin bulunduğu yol gösterir.|
| LogPath| Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz tam yolunu belirtir.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.|

## <a name="example"></a>Örnek

Aşağıdaki örnek yapılandırma parametrelerini alır ve .cab dosyası tarafından belirtilen sağlar `$Name` parametresi yüklenir.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```