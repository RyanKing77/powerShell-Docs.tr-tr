---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsProcess kaynağı"
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

**WindowsProcess** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar.

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
| Bağımsız değişkenler| Bir işlem olarak geçirilecek bağımsız değişkenleri dizisini gösterir-değil. Birden fazla bağımsız değişken geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.| 
| Yol| İşlem yürütülebilir dosyası yolu. Bu ortam çalıştırılabilir dosyanın (olmayan tam yolunu), DSC kaynağı dosya adını arayacaktır **yolu** değişkeni (`$env:Path`) yürütülebilir dosyası bulunamadı. Bu özelliğin değeri tam bir yol ise, DSC kullanmaz **yolu** dosyayı bulmak için ortam değişkeni ve yol yoksa, bir hata özel durum oluşturacak. Göreli yollar izin verilmiyor.| 
| kimlik bilgisi| İşlemi başlatmak için kimlik bilgilerini gösterir.| 
| Emin olun| İşlem var olup olmadığını gösterir. Bu özelliği işlemi var olduğundan emin olmak için "var" olarak ayarlayın. Aksi takdirde, "Yok" ayarlayın. "Var" varsayılandır.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.| 
| StandardErrorPath| Standart hatayı yazmak için dizin yolu gösterir. Var. Varolan dosyanın üzerine yazılır.| 
| StandardInputPath| Standart giriş konumu gösterir.| 
| StandardOutputPath| Standart çıktı yazmak için konumu belirtir. Var. Varolan dosyanın üzerine yazılır.| 
| WorkingDirectory| Geçerli çalışma dizini olarak işlemi için kullanılacak konumu gösterir.| 

