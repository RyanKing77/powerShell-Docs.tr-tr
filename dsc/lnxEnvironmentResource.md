---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Linux nxEnvironment kaynak için"
ms.openlocfilehash: 61e0c7e77e486cea878351f1929d73f1f80710d8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC Linux nxEnvironment kaynak için

**NxEnvironment** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), sistem ortam değişkenlerini Linux düğümde yönetmek için bir mekanizma sağlar.

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
| Ad| Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adını belirtir.| 
| Değer| Ortam değişkenine atanacak değer.| 
| Emin olun| Değişkeni var olup olmadığını denetlemek belirler. Bu özelliği değişkeni mevcut emin olmak için "var" olarak ayarlayın. "Mevcut için" değişkeni var olmadığından emin olmak için ayarlayın. "Var" varsayılan değerdir.| 
| Yol| Yapılandırılmakta olan ortam değişkeni tanımlar. Bu özelliği ayarlamak **$true** değişken ise **yolu** değişken, aksi takdirde ayarlamak **$false**. Varsayılan değer **$false**. Yapılandırılmakta değişken ise **yolu** değişken değeri sağlanan **değeri** özelliği, var olan değerin eklenir.| 
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Ek Bilgi

* Varsa **yolu** yok veya kümesine **$false**, ortam değişkenleri yönetilen `/etc/environment`. Programları veya komut dosyalarını kaynağı için yapılandırma gerekebilir `/etc/environment` yönetilen ortam değişkenleri erişmek için dosya.
* Varsa **yolu** ayarlanır **$true**, ortam değişkeni dosyasında yönetilen `/etc/profile.d/DSCenvironment.sh`. Bu dosya, henüz yoksa oluşturulur. Varsa **emin olun** ayarlanır "Yok" için ve **yolu** ayarlanır **$true**, varolan bir ortam değişkeni yalnızca konumundan kaldırılacak `/etc/profile.d/DSCenvironment.sh` ve diğer dosyalarından.

## <a name="example"></a>Örnek

Aşağıdaki örnekte nasıl kullanılacağını gösterir **nxEnvironment** emin olmak için kaynak **TestEnvironmentVariable** var ve "Test-Value" değerine sahip. Varsa **TestEnvironmentVariable** olan yoksa, oluşturulur.

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```


