---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfı"
ms.openlocfilehash: b2d2ce000988f2c10ab04c4ba5a4650bd3c75ec7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7ade0-103">MSFT_DSCLocalConfigurationManager sınıfı</span><span class="sxs-lookup"><span data-stu-id="7ade0-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7ade0-104">Yerel Yapılandırma Yöneticisi'ni (yapılandırma dosyalarını durumunu denetler ve yapılandırma aracısı yapılandırmaları uygulamak için kullandığı LCM'yi).</span><span class="sxs-lookup"><span data-stu-id="7ade0-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="7ade0-105">Aşağıdaki sözdizimini yönetilen Nesne Biçimi (MOF) koddan Basitleştirilmiş ve tüm devralınan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="7ade0-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ade0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ade0-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="7ade0-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ade0-107">Members</span></span>
-------

<span data-ttu-id="7ade0-108">**MSFT_DSCLocalConfigurationManager** sınıfı aşağıdaki üyeleri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7ade0-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="7ade0-109">[Methods][]</span><span class="sxs-lookup"><span data-stu-id="7ade0-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="7ade0-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ade0-110">Methods</span></span>

<span data-ttu-id="7ade0-111">**MSFT_DSCLocalConfigurationManager** sınıfı bu yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="7ade0-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ade0-112">Method</span></span> |<span data-ttu-id="7ade0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ade0-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="7ade0-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="7ade0-115">Bekleyen yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>| 
| [<span data-ttu-id="7ade0-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="7ade0-117">DSC kaynak hata ayıklama devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-117">Disables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="7ade0-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="7ade0-119">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7ade0-119">Enables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="7ade0-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="7ade0-121">Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ade0-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="7ade0-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="7ade0-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="7ade0-123">Belirli bir iş ile ilgili yapılandırma aracısı çıktısını alır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-123">Gets the Configuration Agent output relating to a specific job.</span></span>| 
| [<span data-ttu-id="7ade0-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="7ade0-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="7ade0-125">Yapılandırma durumu geçmişi alın.</span><span class="sxs-lookup"><span data-stu-id="7ade0-125">Get the configuration status history.</span></span>| 
| [<span data-ttu-id="7ade0-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="7ade0-127">Yapılandırma aracısı denetlemek için kullanılan LCM'yi ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>| 
| [<span data-ttu-id="7ade0-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="7ade0-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="7ade0-129">Tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-129">Starts the consistency check.</span></span>| 
| [<span data-ttu-id="7ade0-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="7ade0-131">Yapılandırma dosyalarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-131">Removes the configuration files.</span></span>| 
| [<span data-ttu-id="7ade0-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="7ade0-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="7ade0-133">Doğrudan çağıran **almak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ade0-133">Directly calls the **Get** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="7ade0-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="7ade0-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="7ade0-135">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ade0-135">Directly calls the **Set** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="7ade0-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="7ade0-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="7ade0-137">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ade0-137">Directly calls the **Test** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="7ade0-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="7ade0-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="7ade0-139">Dökümünü önceki yapılandırmaya geri dön.</span><span class="sxs-lookup"><span data-stu-id="7ade0-139">Rolls back to a previous configuration.</span></span>| 
| [<span data-ttu-id="7ade0-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="7ade0-141">Yönetilen düğüme yapılandırma belgesini gönderir ve bekleyen bir değişiklik kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7ade0-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>| 
| [<span data-ttu-id="7ade0-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="7ade0-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="7ade0-143">Yönetilen düğüme yapılandırma belgesini gönderir ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ade0-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="7ade0-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="7ade0-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="7ade0-145">Yönetilen düğüme yapılandırma belgesi göndermek ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="7ade0-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="7ade0-146">Sonuç çıkış almak için GetConfigurationResultOutput kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ade0-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>| 
| [<span data-ttu-id="7ade0-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="7ade0-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="7ade0-148">Yapılandırma aracısı denetlemek için kullanılan LCM'yi ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="7ade0-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>| 
| [<span data-ttu-id="7ade0-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="7ade0-150">Devam ediyor yapılandırma durdurur.</span><span class="sxs-lookup"><span data-stu-id="7ade0-150">Stops the configuration that is in progress.</span></span>| 
| [<span data-ttu-id="7ade0-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="7ade0-152">Yönetilen düğüme yapılandırma belgesini gönderir ve geçerli yapılandırma belge karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="7ade0-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>| 



 

## <a name="requirements"></a><span data-ttu-id="7ade0-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ade0-153">Requirements</span></span>
------------
><span data-ttu-id="7ade0-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7ade0-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7ade0-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ade0-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>



 

 



