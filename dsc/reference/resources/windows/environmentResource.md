---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Environment kaynağı
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685987"
---
# <a name="dsc-environment-resource"></a>DSC Environment kaynağı

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

__Ortam__ kaynak olarak Windows PowerShell Desired State Configuration (DSC), sistem ortam değişkenlerini yönetmek için bir mekanizma sağlar.

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
| Adı| Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adı gösterir.|
| Emin olun| Bir değişkenin olup olmadığını gösterir. Bu özellik kümesine __mevcut__ henüz yoksa ortam değişkenini oluşturmak veya değerini aracılığıyla sağlanan eşleştiğinden emin olmak için __değer__ değişkeni zaten varsa, özelliği. Ayarlayın __devamsızlık__ varsa değişken silinemedi.|
| Yol| Yapılandırılan ortam değişkenini tanımlar. Bu özellik kümesine __$true__ değişken ise __yolu__ değişken; Aksi takdirde ayarlayın __$false__. Varsayılan değer __$false__. Yapılandırılan değişken ise __yolu__ değişkeni aracılığıyla belirtilen değer __değer__ özelliği için mevcut değeri eklenir.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| Değer| Ortam değişkenine atanacak değer.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, sağlar __TestEnvironmentVariable__ mevcut olduğundan ve değere sahip __TestValue__. Mevcut değilse, onu oluşturur.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```