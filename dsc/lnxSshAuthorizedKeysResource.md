---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxSshAuthorizedKeys kaynak için
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC Linux nxSshAuthorizedKeys kaynak için

**NxAuthorizedKeys** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), yönetmek için bir mekanizma ssh yetkili belirli bir kullanıcı için anahtarlar sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| KeyComment| Anahtar için benzersiz bir açıklama. Bu anahtarları benzersiz şekilde tanımlamak için kullanılır.|
| Emin olun| Anahtar tanımlı olup olmadığını belirtir. Bu özelliği anahtarı kullanıcının yetkili anahtarları dosyasında yok emin olmak için "yok" olarak ayarlayın. Anahtar kullanıcının yetkili anahtar dosyasında tanımlanan emin olmak için "var" ayarlayın.|
| Kullanıcı Adı| SSH yönetmek için kullanıcı adı için anahtarları yetkili. Tanımlı değil, varsayılan kullanıcı "Kök" olur.|
| üzerine gelin| Anahtar içerikleri. Bu gereklidir **olun** "Var" ayarlanır.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, ssh yetkili ortak tanımlar "monuser" kullanıcı için anahtar.

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```