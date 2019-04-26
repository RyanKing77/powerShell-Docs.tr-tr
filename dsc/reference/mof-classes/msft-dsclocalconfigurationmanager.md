---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfı
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078070"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="05dcc-103">MSFT_DSCLocalConfigurationManager sınıfı</span><span class="sxs-lookup"><span data-stu-id="05dcc-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="05dcc-104">Yapılandırma durumunu kontrol yerel Configuration Manager (LCM) dosyaları ve yapılandırmaları uygulamak için Yapılandırma Aracı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="05dcc-105">Aşağıdaki söz dizimini Yönetilen Nesne Biçimi (MOF) koddan Basitleştirilmiş ve tüm devralınan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="05dcc-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="05dcc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05dcc-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="05dcc-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="05dcc-107">Members</span></span>

<span data-ttu-id="05dcc-108">**MSFT_DSCLocalConfigurationManager** sınıfı aşağıdaki üyelere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="05dcc-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="05dcc-109">[Yöntemleri] []</span><span class="sxs-lookup"><span data-stu-id="05dcc-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="05dcc-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="05dcc-110">Methods</span></span>

<span data-ttu-id="05dcc-111">**MSFT_DSCLocalConfigurationManager** sınıfı bu yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="05dcc-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="05dcc-112">Method</span></span> |<span data-ttu-id="05dcc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05dcc-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="05dcc-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="05dcc-115">Yapılandırma Aracı, bekleyen yapılandırmayı uygulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="05dcc-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="05dcc-117">DSC kaynak hata ayıklama devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="05dcc-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="05dcc-119">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="05dcc-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="05dcc-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="05dcc-121">Yönetilen düğüme yapılandırma belgesi gönderir ve kullandığı **alma** yapılandırmayı uygulamak için yapılandırma aracısı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05dcc-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="05dcc-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="05dcc-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="05dcc-123">Belirli bir işle ilgili yapılandırma aracı çıkış alır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="05dcc-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="05dcc-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="05dcc-125">Yapılandırma durumu geçmişi Al</span><span class="sxs-lookup"><span data-stu-id="05dcc-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="05dcc-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="05dcc-127">Yapılandırma Aracı denetlemek için kullanılan LCM ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="05dcc-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="05dcc-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="05dcc-129">Tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="05dcc-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="05dcc-131">Yapılandırma dosyaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="05dcc-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="05dcc-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="05dcc-133">Doğrudan çağıran **alma** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05dcc-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="05dcc-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="05dcc-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="05dcc-135">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05dcc-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="05dcc-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="05dcc-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="05dcc-137">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05dcc-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="05dcc-138">Geri alma</span><span class="sxs-lookup"><span data-stu-id="05dcc-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="05dcc-139">Bir önceki yapılandırmaya geri dön dökümü yapar.</span><span class="sxs-lookup"><span data-stu-id="05dcc-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="05dcc-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="05dcc-141">Yapılandırma belgelerini yönetilen düğüme gönderir ve bir bekleyen değişiklik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="05dcc-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="05dcc-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="05dcc-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="05dcc-143">Yapılandırma belgelerini yönetilen düğüme gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="05dcc-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="05dcc-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="05dcc-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="05dcc-145">Yapılandırma belgelerini yönetilen düğüme gönderin ve yapılandırmayı uygulamak için Yapılandırma Aracı'nı kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="05dcc-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="05dcc-146">GetConfigurationResultOutput sonuç çıkış almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="05dcc-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="05dcc-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="05dcc-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="05dcc-148">Yapılandırma Aracı denetlemek için kullanılan LCM ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="05dcc-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="05dcc-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="05dcc-150">Devam eden yapılandırma durdurur.</span><span class="sxs-lookup"><span data-stu-id="05dcc-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="05dcc-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="05dcc-152">Yapılandırma belgelerini yönetilen düğüme gönderir ve belgeyi karşı geçerli yapılandırmasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="05dcc-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="05dcc-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05dcc-153">Requirements</span></span>

<span data-ttu-id="05dcc-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="05dcc-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="05dcc-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="05dcc-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>