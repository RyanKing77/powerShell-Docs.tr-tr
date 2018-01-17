---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Kaynaklar birden çok sürümü ile kullanma"
ms.openlocfilehash: 8bd8b1dab9418c6d8cf64cd682c527a7f039cdb4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="bb458-103">Kaynaklar birden çok sürümü ile kullanma</span><span class="sxs-lookup"><span data-stu-id="bb458-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="bb458-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bb458-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bb458-105">PowerShell 5. 0'da, DSC kaynakları birden çok sürümü olabilir ve bir bilgisayar yan yana üzerinde sürümleri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bb458-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="bb458-106">Bu, aynı modülü klasörde yer alan birden çok kaynak Modül sürümü sağlayarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bb458-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="bb458-107">Birden çok kaynak sürümlerini yan yana yükleme</span><span class="sxs-lookup"><span data-stu-id="bb458-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="bb458-108">Kullanabileceğiniz **MinimumVersion**, **MaximumVersion**, ve **RequiredVersion** parametrelerinin [yükleme-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) belirtmek için cmdlet yüklemek için bir modül hangi sürümü.</span><span class="sxs-lookup"><span data-stu-id="bb458-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="bb458-109">Çağırma **yükleme-Module** belirtmeden bir sürüm en son sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="bb458-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="bb458-110">Örneğin, birden çok sürümü vardır **xFailOverCluster** modülü, her biri içeren bir **xCluster** kaynağa.</span><span class="sxs-lookup"><span data-stu-id="bb458-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="bb458-111">Arama sonucu **yükleme-Module** sürüm belirtmeden numarası aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bb458-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="bb458-112">Şimdi çağırırsanız, **yükleme-Module** yeniden, ancak belirtin bir **RequiredVersion** 1.1.0.0 bunu aşağıdaki sonuçları:</span><span class="sxs-lookup"><span data-stu-id="bb458-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="bb458-113">Bir kaynak sürümü bir yapılandırmada belirtme</span><span class="sxs-lookup"><span data-stu-id="bb458-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="bb458-114">Bir bilgisayarda yüklü birden fazla kaynaklarınız varsa, bir yapılandırmada kullandığınızda, bu kaynak sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb458-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="bb458-115">Belirterek bunu **ModuleVersion** parametresinin **alma DscResource** anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bb458-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="bb458-116">Yapılandırma birden çok sürüm yüklü olan bir kaynağın kaynak modülünün sürümünü belirtmek başarısız olursa bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb458-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="bb458-117">Aşağıdaki yapılandırma çağırmak için kaynak sürümünü belirtin gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bb458-117">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

><span data-ttu-id="bb458-118">Not: Alma DscResource ModuleVersion parametresinin PowerShell 4. 0 ' kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="bb458-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="bb458-119">PowerShell 4. 0'da, bir modül sürümü alma DscResource ModuleName parametresi için bir modül belirtimi nesnesi geçirerek belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb458-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="bb458-120">Bir modül belirtimi ModuleName ve RequiredVersion anahtarları içeren bir karma tablosu nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="bb458-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="bb458-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb458-121">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

<span data-ttu-id="bb458-122">Bu PowerShell 5. 0'da çalışır, ancak kullanmanız önerilir **ModuleVersion** parametresi.</span><span class="sxs-lookup"><span data-stu-id="bb458-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb458-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bb458-123">See also</span></span>
* [<span data-ttu-id="bb458-124">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="bb458-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="bb458-125">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="bb458-125">DSC Resources</span></span>](resources.md)

