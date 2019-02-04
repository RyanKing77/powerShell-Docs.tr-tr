---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Paket DSC kaynağı
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686064"
---
# <a name="dsc-package-resource"></a>Paket DSC kaynağı

_Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0_

**Paket** kaynak olarak Windows PowerShell Desired State Configuration (DSC) yüklemek veya bir hedef düğüm üzerinde Windows Installer ve setup.exe paketleri gibi paketleri kaldırmak için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a>Özellikler

| Özellik | Açıklama |
| --- | --- |
| Adı| Belirli bir durumu sağlamak istediğiniz paketinin adını belirtir.|
| Yol| Paketin bulunduğu yol gösterir.|
| ProductID| Paketi benzersiz olarak tanımlayan ürün Kimliğini belirtir.|
| Bağımsız değişkenler| Paketi tam olarak sağlanan şekilde geçirilecek bağımsız değişken bir dize listeler.|
| Kimlik bilgisi| Uzak bir kaynak üzerinde paket erişimi sağlar. Bu özellik, paketi yüklemek için kullanılmaz. Paket her zaman yerel sistemde yüklenir.|
| Emin olun| Paketin yüklü olup olmadığını gösterir. Bu özelliği "Yok" paketi yüklü emin olun (veya paket yüklüyse kaldırmak için) olarak ayarlayın. "Paket yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.|
| LogPath| Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz tam yolunu belirtir.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| ReturnCode| Beklenen dönüş kodu gösterir. Gerçek kodu döndürmesi durumunda beklenen değer, burada, yapılandırma, bir hata döndürür sağlanan eşleşmiyor.|

## <a name="example"></a>Örnek

Bu örnek belirtilen yolda bulunur ve belirtilen ürün kimliği olan .msi yükleyicisini çalıştırır.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```