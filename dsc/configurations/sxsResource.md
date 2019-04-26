---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yüklü bir kaynağın belirli bir sürümünü içeri aktarma
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080014"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="75ad3-103">Yüklü bir kaynağın belirli bir sürümünü içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="75ad3-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="75ad3-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="75ad3-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="75ad3-105">PowerShell 5. 0'da, DSC kaynakları ayrı sürümleri bir bilgisayarda yan yana yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="75ad3-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="75ad3-106">Kaynak modülü sürüm klasörleri adlı ayrı bir kaynak sürümleri depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75ad3-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="75ad3-107">Ayrı kaynak sürümlerini yan yana yükleme</span><span class="sxs-lookup"><span data-stu-id="75ad3-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="75ad3-108">Kullanabileceğiniz **MinimumVersion**, **MaximumVersion**, ve **RequiredVersion** parametrelerinin [Install-Module](/powershell/module/PowershellGet/Install-Module) belirtmek için cmdlet hangi sürümü yüklemek için bir modülün.</span><span class="sxs-lookup"><span data-stu-id="75ad3-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="75ad3-109">Çağırma **Install-Module** belirtmeden bir sürümü, en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="75ad3-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="75ad3-110">Örneğin, birden çok sürümü vardır **xFailOverCluster** modülü, her birinde bir **xCluster** kaynak.</span><span class="sxs-lookup"><span data-stu-id="75ad3-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="75ad3-111">Çağırma **Install-Module** sürümü belirtmeden numarası modülünün en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="75ad3-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="75ad3-112">Bir modülün belirli bir sürümünü yüklemek için belirtin bir **RequiredVersion** 1.1.0.0 biri.</span><span class="sxs-lookup"><span data-stu-id="75ad3-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="75ad3-113">Bu, belirtilen sürümü yüklü olan sürümü ile yan yana yüklenir.</span><span class="sxs-lookup"><span data-stu-id="75ad3-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="75ad3-114">Her ikisi de artık bkz modülünün sürümünü kullandığınızda listelenen `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="75ad3-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="75ad3-115">Bir yapılandırmada bir kaynak sürümünü belirtme</span><span class="sxs-lookup"><span data-stu-id="75ad3-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="75ad3-116">Bir bilgisayarda yüklü ayrı kaynak sürümleri varsa, bu kaynağın sürümünü bir yapılandırmada kullandığınızda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="75ad3-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="75ad3-117">Belirterek bunu **ModuleVersion** parametresinin **Import-DscResource** anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="75ad3-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="75ad3-118">Bir kaynak modülü birden fazla sürümü yüklü olan bir kaynağın sürümünü belirtmek başarısız olursa, yapılandırma, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75ad3-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="75ad3-119">Aşağıdaki yapılandırmayı çağırmak için kaynağın sürümünü belirteceğiniz gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="75ad3-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="75ad3-120">Not: Import-DscResource ModuleVersion parametresini PowerShell 4. 0'kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="75ad3-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="75ad3-121">PowerShell 4. 0'da, Import-DscResource ModuleName parametresi için bir modül belirtimi nesnesi geçirerek bir modül sürümü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75ad3-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="75ad3-122">Modülü belirtimi nesnesi ModuleName ve RequiredVersion anahtarları içeren bir karma tablodur.</span><span class="sxs-lookup"><span data-stu-id="75ad3-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="75ad3-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="75ad3-123">For example:</span></span>

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

<span data-ttu-id="75ad3-124">Bu PowerShell 5. 0'da çalışır, ancak kullanmanızı tavsiye edilir **ModuleVersion** parametresi.</span><span class="sxs-lookup"><span data-stu-id="75ad3-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="75ad3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75ad3-125">See also</span></span>

- [<span data-ttu-id="75ad3-126">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="75ad3-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="75ad3-127">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="75ad3-127">DSC Resources</span></span>](../resources/resources.md)
