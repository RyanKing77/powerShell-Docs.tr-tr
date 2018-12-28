---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırmaları iç içe yerleştirme
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405702"
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