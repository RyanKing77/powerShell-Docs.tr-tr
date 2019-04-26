---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxEnvironment kaynağı
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078019"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC için Linux nxEnvironment kaynağı

**NxEnvironment** kaynak içinde PowerShell Desired State Configuration (DSC), sistem ortam değişkenlerini Linux düğümde yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| Adı| Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adı gösterir.|
| Değer| Ortam değişkenine atanacak değer.|
| Emin olun| Değişkeni mevcut olup olmadığını denetleyin belirler. Bu özelliği değişkeni var. olmak için "var" olarak ayarlayın. Kümesi "Yok" değişken sağlamak için mevcut değil. "Var" varsayılan değerdir.|
| Yol| Yapılandırılan ortam değişkenini tanımlar. Bu özellik kümesine **$true** değişken ise **yolu** değişken; Aksi takdirde ayarlayın **$false**. Varsayılan değer **$false**. Yapılandırılan değişken ise **yolu** değişkeni aracılığıyla belirtilen değer **değer** özelliği için mevcut değeri eklenir.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Ek Bilgi

* Varsa **yolu** yok veya kümesine **$false**, ortam değişkenleri yönetilen `/etc/environment`. Programlar veya betiklerde kaynak yapılandırma gerektirebilir `/etc/environment` yönetilen ortam değişkenlerine erişmek için dosya.
* Varsa **yolu** ayarlanır **$true**, ortam değişkeni dosyasında yönetilen `/etc/profile.d/DSCenvironment.sh`. Bu dosya yoksa, oluşturulur. Varsa **emin olun** ayarlanmış "Yok" için ve **yolu** ayarlanır **$true**, var olan bir ortam değişkeni yalnızca kaldırılacak. `/etc/profile.d/DSCenvironment.sh` ve diğer dosyalardan.

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl kullanılacağını gösterir **nxEnvironment** emin olmak için kaynak **TestEnvironmentVariable** mevcut olduğundan ve "Test-Value" değerine sahip. Varsa **TestEnvironmentVariable** olduğunu yoksa oluşturulacaktır.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```