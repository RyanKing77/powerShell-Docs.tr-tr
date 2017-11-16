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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="953bb-103">DSC yapılandırmaları iç içe geçme</span><span class="sxs-lookup"><span data-stu-id="953bb-103">Nesting DSC configurations</span></span>

<span data-ttu-id="953bb-104">(Bileşik configuration olarak da adlandırılır) bir iç içe geçmiş yapılandırma içinde başka bir yapılandırma bir kaynak kabul edildiğinde çağrılan bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="953bb-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="953bb-105">Aynı dosyada iki yapılandırma tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="953bb-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="953bb-106">Basit bir örneğe bakalım:</span><span class="sxs-lookup"><span data-stu-id="953bb-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="953bb-107">Bu örnekte, `FileConfig` iki zorunlu parametreler isteyen **CopyFrom** ve **CopyTo**, için değerler olarak kullanılan **KaynakYolu** ve  **HedefYolu** özelliklerinde `File` kaynak bloğu.</span><span class="sxs-lookup"><span data-stu-id="953bb-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="953bb-108">`NestedConfig` Yapılandırma çağrıları `FileConfig` kaynak değilmiş gibi.</span><span class="sxs-lookup"><span data-stu-id="953bb-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="953bb-109">Özelliklerinde `NestedConfig` kaynak blok (**CopyFrom** ve **CopyTo**) parametreleri `FileConfig` yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="953bb-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="953bb-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="953bb-110">See Also</span></span>

- [<span data-ttu-id="953bb-111">DSC yapılandırması bir kaynak olarak kullanarak bileşik kaynakları--</span><span class="sxs-lookup"><span data-stu-id="953bb-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)

