---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="18501-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="18501-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="18501-104">Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="18501-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="18501-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18501-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="18501-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18501-106">Parameters</span></span>
----------

<span data-ttu-id="18501-107">*configurationData* \[içinde\] göndermek için yapılandırma verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="18501-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="18501-108">*yapılandırmaları* \[çıkışı\] getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="18501-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="18501-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="18501-109">Return value</span></span>
------------

<span data-ttu-id="18501-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="18501-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="18501-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18501-111">Remarks</span></span>

<span data-ttu-id="18501-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="18501-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18501-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18501-113">Requirements</span></span>
------------
><span data-ttu-id="18501-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="18501-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="18501-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="18501-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="18501-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="18501-116">See also</span></span>


[<span data-ttu-id="18501-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="18501-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)