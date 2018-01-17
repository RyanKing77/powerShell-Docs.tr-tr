---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC ProcessSet kaynağı"
ms.openlocfilehash: ec1d6a04b5debc22fe2f3b4a4396c385514a3b0c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess Resource

> İçin geçerlidir: Windows PowerShell 5.0

**ProcessSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar. Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsProcess kaynak](windowsProcessResource.md) belirtilen her grup için `GroupName` parametresi.

## <a name="syntax"></a>Sözdizimi

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Özellikler
|  Özellik  |  Açıklama   | 
|---|---| 
| Bağımsız değişkenler| İşlem olarak geçirilecek bağımsız değişkenleri içeren bir dize-değil. Birden fazla bağımsız değişken geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.| 
| Yol| İşlem yürütülebilir dosya yolları. Bunlar yürütülebilir dosyaları (tam olarak nitelenmiş yollar) adlarını varsa, DSC kaynağı ortam arama **yolu** değişkeni (`$env:Path`) dosyaları bulmak için. Bu özelliğin değerleri, tam yol varsa, DSC kullanmaz **yolu** dosyaları bulmak için ortam değişkeni ve yolların yoksa bir hata özel durum oluşturacak. Göreli yollar izin verilmiyor.| 
| kimlik bilgisi| İşlemi başlatmak için kimlik bilgilerini gösterir.| 
| Emin olun| İşlemler var olup olmadığını belirtir. Bu özelliği işlemi var olduğundan emin olmak için "var" olarak ayarlayın. Aksi takdirde, "Yok" ayarlayın. "Var" varsayılandır.| 
| StandardErrorPath| İşlemler yazma standart hatası yolu. Var. Varolan dosyanın üzerine yazılır.| 
| StandardInputPath| İşlem standart giriş aldığı akış.| 
| StandardOutputPath| Standart çıktı yazma işlemleri için dosyanın yolu. Var. Varolan dosyanın üzerine yazılır.| 
| WorkingDirectory| Geçerli çalışma dizini olarak işlemleri için kullanılan konumu.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **_ResourceType**, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.| 

