---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsProcess kaynağı
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076778"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess kaynağı

_Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0_

**WindowsProcess** kaynak içinde Windows PowerShell Desired State Configuration (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Özellikler

| Özellik | Açıklama |
| --- | --- |
| Bağımsız değişkenler| Bir işlem olarak geçirilecek bağımsız değişkenleri dizisini gösterir-olduğu. Birden çok bağımsız değişkenleri geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.|
| Yol| İşlem yürütülebilir dosyası yolu. Bu ortamı yürütülebilir dosya (tam olarak nitelenmiş yolu değil) DSC kaynak dosya adını arayacaktır **yolu** değişkeni (`$env:Path`) yürütülebilir dosyası bulunamadı. Bu özelliğin değeri tam bir yolu ise, DSC kullanmaz **yolu** dosyayı bulmak için ortam değişkeni ve yol mevcut değilse bir hata oluşturur. Göreli yollar izin verilmez.|
| Kimlik bilgisi| İşlemi başlatmak için kimlik bilgilerini belirtir.|
| Emin olun| Bir işlem olup olmadığını gösterir. Bu işlem var olduğundan emin olmak için "var" özelliğini ayarlayın. Aksi takdirde, "Yok" ayarlayın. "Var" varsayılandır.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"` .|
| StandardErrorPath| Standart hatayı yazmak için dizin yolu gösterir. Var. Varolan dosyanın üzerine yazılır.|
| StandardInputPath| Standart giriş konumu gösterir.|
| StandardOutputPath| Standart çıkışını yazmak için konumu belirtir. Var. Varolan dosyanın üzerine yazılır.|
| Başlangıç| İşlem için geçerli çalışma dizini kullanılacak konumu belirtir.|