---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC paket kaynağı
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-package-resource"></a>DSC paket kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

**Paket** kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) yüklemek veya bir hedef düğüm üzerinde Windows Installer ve setup.exe paketleri gibi paketleri kaldırmak için bir mekanizma sağlar.

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
|  Özellik  |  Açıklama   |
|---|---|
| Ad| Belirli bir durumu sağlamak istediğiniz paketinin adını belirtir.|
| Yol| Paketin bulunduğu yolu gösterir.|
| ProductID| Paketi benzersiz olarak tanıtan ürün kimliği gösterir.|
| Bağımsız değişkenler| Paketi tam olarak sağlanan gibi geçirilen bağımsız değişken bir dize listeler.|
| kimlik bilgisi| Uzak bir kaynağı üzerinde paket erişim sağlar. Bu özellik paketini yüklemek için kullanılmaz. Paket yerel sistem üzerindeki her zaman yüklenir.|
| Emin olun| Paketin yüklü olup olmadığını gösterir. Bu özelliği paketi yüklü değil emin olun (veya paket yüklüyse kaldırmak için) "yok" olarak ayarlayın. "Paketinin yüklü emin olmak için (varsayılan değer) sunmak için" olarak ayarlayın.|
| LogPath| Sağlayıcı yüklemek veya paket kaldırmak için bir günlük dosyasını kaydetmek istediğiniz yeri tam yolunu belirtir.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **ResourceType**, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.|
| ReturnCode| Beklenen dönüş kodu gösterir. Gerçek kodu döndürmesi durumunda yapılandırma bir hata döndürecektir beklenen değer burada sağlanan adla eşleşmiyor.|

## <a name="example"></a>Örnek

Bu örnek belirtilen yolda bulunur ve belirtilen ürün kimliği olan .msi yükleyicisini çalıştırır

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