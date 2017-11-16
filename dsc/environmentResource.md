---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC ortamı kaynak"
ms.openlocfilehash: 7c98798fa0e8fc865798ea30530e41ac87b2dadc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-environment-resource"></a>DSC ortamı kaynak

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

__Ortam__ kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), sistem ortam değişkenlerini yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   | 
|---|---| 
| Ad| Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adını belirtir.| 
| Emin olun| Bir değişken var olup olmadığını gösterir. Bu özelliği ayarlamak __mevcut__ henüz yoksa ortam değişkeni oluşturmak veya değerini aracılığıyla sunulan uyduğundan emin olmak için __değeri__ değişkeni zaten varsa, özelliği. Ayarlamak __etmeksizin__ varsa değişkeni silmek için.| 
| Yol| Yapılandırılmakta olan ortam değişkeni tanımlar. Bu özelliği ayarlamak __$true__ değişken ise __yolu__ değişken, aksi takdirde ayarlamak __$false__. Varsayılan değer __$false__. Yapılandırılmakta değişken ise __yolu__ değişken değeri sağlanan __değeri__ özelliği, var olan değerin eklenir.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.| 
| Değer| Ortam değişkenine atanacak değer.| 

## <a name="example"></a>Örnek

Aşağıdaki örnek sağlar __TestEnvironmentVariable__ bulunduğundan ve değerine sahip __TestValue__. Mevcut değilse, onu oluşturur.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

