---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "İç içe geçme yapılandırmaları"
ms.openlocfilehash: 89badda86707a129909b1c3cc3f79afa0b5f5df6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="3eb57-103">DSC yapılandırmaları iç içe geçme</span><span class="sxs-lookup"><span data-stu-id="3eb57-103">Nesting DSC configurations</span></span>

<span data-ttu-id="3eb57-104">(Bileşik configuration olarak da adlandırılır) bir iç içe geçmiş yapılandırma içinde başka bir yapılandırma bir kaynak kabul edildiğinde çağrılan bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="3eb57-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="3eb57-105">Aynı dosyada iki yapılandırma tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3eb57-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="3eb57-106">Basit bir örneğe bakalım:</span><span class="sxs-lookup"><span data-stu-id="3eb57-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="3eb57-107">Bu örnekte, `FileConfig` iki zorunlu parametreler isteyen **CopyFrom** ve **CopyTo**, için değerler olarak kullanılan **KaynakYolu** ve  **HedefYolu** özelliklerinde `File` kaynak bloğu.</span><span class="sxs-lookup"><span data-stu-id="3eb57-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="3eb57-108">`NestedConfig` Yapılandırma çağrıları `FileConfig` kaynak değilmiş gibi.</span><span class="sxs-lookup"><span data-stu-id="3eb57-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="3eb57-109">Özelliklerinde `NestedConfig` kaynak blok (**CopyFrom** ve **CopyTo**) parametreleri `FileConfig` yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3eb57-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="3eb57-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3eb57-110">See Also</span></span>

- [<span data-ttu-id="3eb57-111">DSC yapılandırması bir kaynak olarak kullanarak bileşik kaynakları--</span><span class="sxs-lookup"><span data-stu-id="3eb57-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)

