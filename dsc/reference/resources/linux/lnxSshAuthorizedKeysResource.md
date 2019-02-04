---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxSshAuthorizedKeys kaynağı
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687807"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC için Linux nxSshAuthorizedKeys kaynağı

**NxAuthorizedKeys** kaynak içinde PowerShell Desired State Configuration (DSC), yönetmek için bir mekanizma ssh yetkili belirli bir kullanıcı için anahtarlar sağlar.

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
| KeyComment| Anahtar için benzersiz bir açıklama. Bu, anahtarlar benzersiz şekilde tanımlamak için kullanılır.|
| Emin olun| Anahtar tanımlı olup olmadığını belirtir. "Yok" anahtar kullanıcının yetkili anahtarlar dosyasına yok sağlamak için bu özelliği ayarlayın. Anahtar kullanıcının yetkili anahtar dosyasında tanımlanan emin olmak için "var" ayarlayın.|
| Kullanıcı Adı| Anahtarlar için SSH yönetmek için kullanıcı adı yetkili. Tanımlı değilse, varsayılan "Kök" kullanıcıdır.|
| üzerine gelin| Anahtar içeriğini. Bu gereklidir **olun** "Var" için ayarlanır.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir ortak ssh yetkili tanımlar "monuser" kullanıcı anahtarı.

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