---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfı
ms.openlocfilehash: 615f2998b11a0a927d3868d852e0d408f500c86d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188844"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cb940-103">MSFT_DSCLocalConfigurationManager sınıfı</span><span class="sxs-lookup"><span data-stu-id="cb940-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cb940-104">Yerel Yapılandırma Yöneticisi'ni (yapılandırma dosyalarını durumunu denetler ve yapılandırma aracısı yapılandırmaları uygulamak için kullandığı LCM'yi).</span><span class="sxs-lookup"><span data-stu-id="cb940-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="cb940-105">Aşağıdaki sözdizimini yönetilen Nesne Biçimi (MOF) koddan Basitleştirilmiş ve tüm devralınan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="cb940-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb940-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb940-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="cb940-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb940-107">Members</span></span>
-------

<span data-ttu-id="cb940-108">**MSFT_DSCLocalConfigurationManager** sınıfı aşağıdaki üyeleri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cb940-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="cb940-109">[Yöntemleri] []</span><span class="sxs-lookup"><span data-stu-id="cb940-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="cb940-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cb940-110">Methods</span></span>

<span data-ttu-id="cb940-111">**MSFT_DSCLocalConfigurationManager** sınıfı bu yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="cb940-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="cb940-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cb940-112">Method</span></span> |<span data-ttu-id="cb940-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb940-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="cb940-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="cb940-115">Bekleyen yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb940-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="cb940-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="cb940-117">DSC kaynak hata ayıklama devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="cb940-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="cb940-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="cb940-119">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="cb940-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="cb940-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="cb940-121">Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb940-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="cb940-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="cb940-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="cb940-123">Belirli bir iş ile ilgili yapılandırma aracısı çıktısını alır.</span><span class="sxs-lookup"><span data-stu-id="cb940-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="cb940-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="cb940-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="cb940-125">Yapılandırma durumu geçmişi alın.</span><span class="sxs-lookup"><span data-stu-id="cb940-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="cb940-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="cb940-127">Yapılandırma aracısı denetlemek için kullanılan LCM'yi ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="cb940-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="cb940-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="cb940-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="cb940-129">Tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="cb940-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="cb940-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="cb940-131">Yapılandırma dosyalarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cb940-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="cb940-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="cb940-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="cb940-133">Doğrudan çağıran **almak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb940-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="cb940-134">resourceSet</span><span class="sxs-lookup"><span data-stu-id="cb940-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="cb940-135">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb940-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="cb940-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="cb940-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="cb940-137">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb940-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="cb940-138">Geri alma</span><span class="sxs-lookup"><span data-stu-id="cb940-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="cb940-139">Dökümünü önceki yapılandırmaya geri dön.</span><span class="sxs-lookup"><span data-stu-id="cb940-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="cb940-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="cb940-141">Yönetilen düğüme yapılandırma belgesini gönderir ve bekleyen bir değişiklik kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cb940-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="cb940-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="cb940-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="cb940-143">Yönetilen düğüme yapılandırma belgesini gönderir ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb940-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="cb940-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="cb940-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="cb940-145">Yönetilen düğüme yapılandırma belgesi göndermek ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="cb940-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="cb940-146">Sonuç çıkış almak için GetConfigurationResultOutput kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb940-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="cb940-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="cb940-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="cb940-148">Yapılandırma aracısı denetlemek için kullanılan LCM'yi ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="cb940-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="cb940-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="cb940-150">Devam ediyor yapılandırma durdurur.</span><span class="sxs-lookup"><span data-stu-id="cb940-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="cb940-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="cb940-152">Yönetilen düğüme yapılandırma belgesini gönderir ve geçerli yapılandırma belge karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="cb940-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|





## <a name="requirements"></a><span data-ttu-id="cb940-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb940-153">Requirements</span></span>
------------
><span data-ttu-id="cb940-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cb940-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cb940-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb940-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>