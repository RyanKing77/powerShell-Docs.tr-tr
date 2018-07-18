---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsProcess kaynağı
ms.openlocfilehash: 3c4e6d8377c3dcbf4f1db87a603d5483b8caafb8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093744"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess kaynağı

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

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

|  Özellik  |  Açıklama   |
|---|---|
| Bağımsız değişkenler| Bir işlem olarak geçirilecek bağımsız değişkenleri dizisini gösterir-olduğu. Birden çok bağımsız değişkenleri geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.|
| Yol| İşlem yürütülebilir dosyası yolu. Bu ortamı yürütülebilir dosya (tam olarak nitelenmiş yolu değil) DSC kaynak dosya adını arayacaktır **yolu** değişkeni (`$env:Path`) yürütülebilir dosyası bulunamadı. Bu özelliğin değeri tam bir yolu ise, DSC kullanmaz **yolu** dosyayı bulmak için ortam değişkeni ve yol mevcut değilse bir hata oluşturur. Göreli yollar izin verilmez.|
| Kimlik bilgisi| İşlemi başlatmak için kimlik bilgilerini belirtir.|
| Emin olun| Bir işlem olup olmadığını gösterir. Bu işlem var olduğundan emin olmak için "var" özelliğini ayarlayın. Aksi takdirde, "Yok" ayarlayın. "Var" varsayılandır.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.|
| StandardErrorPath| Standart hatayı yazmak için dizin yolu gösterir. Var. Varolan dosyanın üzerine yazılır.|
| StandardInputPath| Standart giriş konumu gösterir.|
| StandardOutputPath| Standart çıkışını yazmak için konumu belirtir. Var. Varolan dosyanın üzerine yazılır.|
| WorkingDirectory| İşlem için geçerli çalışma dizini kullanılacak konumu belirtir.|