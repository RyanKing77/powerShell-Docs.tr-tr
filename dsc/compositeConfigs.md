---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "İç içe geçme yapılandırmaları"
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
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

Bu örnekte, `FileConfig` iki zorunlu parametreler isteyen **CopyFrom** ve **CopyTo**, için değerler olarak kullanılan **KaynakYolu** ve  **HedefYolu** özelliklerinde `File` kaynak bloğu. `NestedConfig` Yapılandırma çağrıları `FileConfig` kaynak değilmiş gibi.
Özelliklerinde `NestedConfig` kaynak blok (**CopyFrom** ve **CopyTo**) parametreleri `FileConfig` yapılandırma.

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırması bir kaynak olarak kullanarak bileşik kaynakları--](authoringResourceComposite.md)

