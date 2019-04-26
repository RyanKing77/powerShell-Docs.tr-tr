---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Çekme Sunucusundan Düğüm Güncelleştirme
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079107"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="ee1e5-103">Çekme Sunucusundan Düğüm Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="ee1e5-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="ee1e5-104">Aşağıdaki bölümler, zaten bir çekme sunucusu ayarladığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ee1e5-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="ee1e5-105">Çekme sunucunuzu ayarlamadıysanız, aşağıdaki kılavuzları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ee1e5-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="ee1e5-106">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="ee1e5-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="ee1e5-107">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="ee1e5-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="ee1e5-108">Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee1e5-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="ee1e5-109">Bu makale indirilmesi ve kaynakları otomatik olarak indirmek için istemcileri yapılandırın kullanabilmesi için kaynakları karşıya yükleme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee1e5-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="ee1e5-110">Düğümün aldığında atanmış bir yapılandırma yoluyla **çekme** veya **anında iletme** (v5) otomatik olarak karşıdan yüklerken LCM içinde belirtilen konumdan yapılandırma için gerekli tüm kaynakları.</span><span class="sxs-lookup"><span data-stu-id="ee1e5-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="ee1e5-111">Update-DSCConfiguration cmdlet'i kullanarak</span><span class="sxs-lookup"><span data-stu-id="ee1e5-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="ee1e5-112">PowerShell 5. 0'den itibaren [güncelleştirme-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet'ini çekme Sunucusu'ndan alana LCM içinde yapılandırılmış yapılandırmasını güncelleştirmek için bir düğüm zorlar.</span><span class="sxs-lookup"><span data-stu-id="ee1e5-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="ee1e5-113">Invoke-CIMMethod kullanma</span><span class="sxs-lookup"><span data-stu-id="ee1e5-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="ee1e5-114">PowerShell 4. 0'da, yine de el ile yapılandırma kullanılarak güncelleştirilecek çekme istemci zorlayabilirsiniz [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="ee1e5-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="ee1e5-115">Aşağıdaki örnek, bir CIM oturumu belirtilen kimlik bilgilerini oluşturur, uygun CIM yöntemini çağırır ve oturumunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ee1e5-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="ee1e5-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ee1e5-116">See Also</span></span>

[<span data-ttu-id="ee1e5-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="ee1e5-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
