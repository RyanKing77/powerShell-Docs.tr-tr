---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxFileLine kaynağı
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048624"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC için Linux nxFileLine kaynağı

**NxFileLine** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde bir yapılandırma dosyası içindeki satırların yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| Dosya yolu| Hedef düğümde bulunan satırları yönetmek için dosyanın tam yolu.|
| ContainsLine| Dosyada emin olmak için bir satır var. Dosyasında yoksa, bu satırı dosyasına eklenir. **ContainsLine** zorunludur, ancak boş bir dize olarak ayarlanabilir (`ContainsLine = ""`) durumunda gerekli değildir.|
| DoesNotContainPattern| Dosyasında bulunmamalıdır satırlar için normal ifade deseni. Bu normal bir ifadeyle eşleşen dosyasında bulunan tüm satırlar için satırın dosyasından kaldırılır.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Kullanarak bu örnek gösterir **nxFileLine** yapılandırmak için kaynak `/etc/sudoers` kullanıcı sağlanarak dosyası: monuser değil requiretty için yapılandırılır.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```