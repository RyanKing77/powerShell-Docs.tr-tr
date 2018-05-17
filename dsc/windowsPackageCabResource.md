---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC WindowsPackageCab kaynağı
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab kaynağı

> İçin geçerlidir: Windows PowerShell 5.1 ve sonrası

**WindowsPackageCab** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) yüklemek veya bir hedef düğümde Windows dolap (.cab) paketleri kaldırmak için bir mekanizma sağlar.

Hedef düğüm DISM PowerShell modül yüklü olması gerekir. Bilgi için bkz: [kullanım DISM Windows PowerShell'de](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


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
| Ad| Belirli bir durumu sağlamak istediğiniz paketinin adını belirtir.|
| Emin olun| Paketin yüklü olup olmadığını gösterir. Bu özelliği paketi yüklü değil emin olun (veya paket yüklüyse kaldırmak için) "yok" olarak ayarlayın. "Paketinin yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.|
| Yol| Paketin bulunduğu yolu gösterir.|
| LogPath| Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz yeri tam yolunu belirtir.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **ResourceType**, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.|

## <a name="example"></a>Örnek

Aşağıdaki örnek yapılandırma giriş parametreleri alır ve bir .cab dosyası tarafından belirtilen sağlar `$Name` parametresi yüklenir.

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