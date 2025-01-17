---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC ProcessSet kaynağı
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077118"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess kaynağı

_Uygulama hedefi: Windows PowerShell 5.0_

**ProcessSet** kaynak içinde Windows PowerShell Desired State Configuration (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar. Bu kaynak bir [bileşik kaynak](../../../resources/authoringResourceComposite.md) çağrılarının [WindowsProcess kaynağı](windowsProcessResource.md) belirtilen her grup için `GroupName` parametresi.

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

| Özellik | Açıklama |
| --- | --- |
| Bağımsız değişkenler| İşlem olarak geçirilecek bağımsız değişkenleri içeren bir dize-olduğu. Birden çok bağımsız değişkenleri geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.|
| Yol| İşlem yürütülebilir dosya yolları. Bunlar yürütülebilir dosyaları (tam olarak nitelenmiş yollar) adlarıdır, DSC kaynak ortam arar **yolu** değişkeni (`$env:Path`) dosyaları bulmak için. Bu özellik değerlerini tam olarak nitelenmiş yollar, DSC kullanmaz **yolu** dosyaları bulmak için ortam değişkeni ve yoksa yolların herhangi bir hata oluşturur. Göreli yollar izin verilmez.|
| Kimlik bilgisi| İşlemi başlatmak için kimlik bilgilerini belirtir.|
| Emin olun| İşlemler var olup olmadığını belirtir. Bu işlem var olduğundan emin olmak için "var" özelliğini ayarlayın. Aksi takdirde, "Yok" ayarlayın. "Var" varsayılandır.|
| StandardErrorPath| Standart hata yazma işlemleri için yolu. Var. Varolan dosyanın üzerine yazılır.|
| StandardInputPath| İşlem standart giriş aldığı akış.|
| StandardOutputPath| Standart çıkış yazma işlemleri için dosyanın yolu. Var. Varolan dosyanın üzerine yazılır.|
| Başlangıç| Geçerli çalışma dizini işlemleri için kullanılan konum.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **_ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"` .|
