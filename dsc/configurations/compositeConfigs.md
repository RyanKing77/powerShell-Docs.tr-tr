---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırmaları iç içe yerleştirme
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080246"
---
# <a name="nesting-dsc-configurations"></a>DSC yapılandırmaları iç içe yerleştirme

(Bileşik configuration olarak da bilinir) bir iç içe geçmiş yapılandırması içinde başka bir yapılandırma bir kaynağı kabul edildiğinde çağrılan bir yapılandırmadır.
Aynı dosyada iki yapılandırma tanımlanması gerekir.

Basit bir örneğe göz atalım:

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }

}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

Bu örnekte, `FileConfig` iki zorunlu parametre **CopyFrom** ve **CopyTo**, için değerler olarak kullanılan **SourcePath** ve  **HedefYolu** özelliklerinde `File` kaynak blok.
`NestedConfig` Yapılandırma çağrıları `FileConfig` kaynak değilmiş gibi.
Özelliklerinde `NestedConfig` kaynak blok (**CopyFrom** ve **CopyTo**) parametreleri `FileConfig` yapılandırma.

## <a name="see-also"></a>Ayrıca bkz:

- [Bileşik kaynaklar bir kaynak olarak bir DSC Yapılandırması kullanılarak--](../resources/authoringResourceComposite.md)