---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Geçici bir düğüm bağımlılıkları belirtme"
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="32a9a-103">Geçici bir düğüm bağımlılıkları belirtme</span><span class="sxs-lookup"><span data-stu-id="32a9a-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="32a9a-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="32a9a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="32a9a-105">DSC özel kaynaklar sağlar **WaitForAll**, **WaitForAny**, ve **WaitForSome** kullanılabilecek yapılandırmalarında diğer yapılandırmaları bağımlılıklarını belirtmek için düğümleri.</span><span class="sxs-lookup"><span data-stu-id="32a9a-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="32a9a-106">Bu kaynaklar davranışını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="32a9a-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="32a9a-107">**WaitForAll**: Belirtilen kaynak tanımlanan tüm hedef düğümleri üzerinde istenen durumda ise başarılı **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a9a-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="32a9a-108">**WaitForAny**: Belirtilen kaynak tanımlanan hedef düğümleri en az biri istenilen durumda ise başarılı **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a9a-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="32a9a-109">**WaitForSome**: belirten bir **NodeCount** özelliğine ek olarak bir **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a9a-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="32a9a-110">Kaynak istenen düğüm sayısı alt sınırı durumda ise kaynak başarılı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a9a-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="32a9a-111">WaitForXXXX kaynaklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="32a9a-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="32a9a-112">Kullanılacak **WaitForXXXX** kaynakları, oluşturduğunuz bir kaynak blok bu kaynak türünün beklemek için düğümlerini ve DSC kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="32a9a-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="32a9a-113">Daha sonra **DependsOn** herhangi bir kaynağa özelliğinde engeller belirtilen koşullar için beklenecek yapılandırmanızda **WaitForXXXX** başarılı olması için düğüm.</span><span class="sxs-lookup"><span data-stu-id="32a9a-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="32a9a-114">Örneğin, aşağıdaki yapılandırmasında, hedef düğüm bekliyor **xADDomain** bitmesi için kaynak **MyDC** en fazla 30 düğümle yeniden deneme sayısı, 15 saniye aralıklarla önce Hedef düğüm etki alanına katılmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="32a9a-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present' 
            Name = 'AD-Domain-Services' 
        }

        xADDomain NewDomain 
        { 
            DomainName = 'Contoso.com'            
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

><span data-ttu-id="32a9a-115">**Not:** WaitForXXX varsayılan kaynakları bir kez deneyin ve sonra başarısız.</span><span class="sxs-lookup"><span data-stu-id="32a9a-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="32a9a-116">Gerekli olmamasına karşın, genellikle bir yeniden deneme aralığı ve sayısı belirtin istersiniz.</span><span class="sxs-lookup"><span data-stu-id="32a9a-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="32a9a-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="32a9a-117">See Also</span></span>
* [<span data-ttu-id="32a9a-118">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="32a9a-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="32a9a-119">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="32a9a-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="32a9a-120">Yerel Yapılandırma Yöneticisi'ni yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a9a-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

