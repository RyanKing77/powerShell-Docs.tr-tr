---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırmaları iç içe yerleştirme
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219003"
---
# <a name="nesting-dsc-configurations"></a>DSC yapılandırmaları iç içe geçme

(Bileşik configuration olarak da adlandırılır) bir iç içe geçmiş yapılandırma içinde başka bir yapılandırma bir kaynak kabul edildiğinde çağrılan bir yapılandırmadır.
Aynı dosyada iki yapılandırma tanımlanması gerekir.

Basit bir örneğe bakalım:

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

Bu örnekte, `FileConfig` iki zorunlu parametreler isteyen **CopyFrom** ve **CopyTo**, için değerler olarak kullanılan **KaynakYolu** ve  **HedefYolu** özelliklerinde `File` kaynak bloğu.
`NestedConfig` Yapılandırma çağrıları `FileConfig` kaynak değilmiş gibi.
Özelliklerinde `NestedConfig` kaynak blok (**CopyFrom** ve **CopyTo**) parametreleri `FileConfig` yapılandırma.

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırması bir kaynak olarak kullanarak bileşik kaynakları--](authoringResourceComposite.md)