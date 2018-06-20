---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218425"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="063c8-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="063c8-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="063c8-104">Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="063c8-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="063c8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="063c8-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="063c8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="063c8-106">Parameters</span></span>
----------

<span data-ttu-id="063c8-107">*configurationData* \[içinde\] göndermek için yapılandırma verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="063c8-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="063c8-108">*yapılandırmaları* \[çıkışı\] getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="063c8-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="063c8-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="063c8-109">Return value</span></span>
------------

<span data-ttu-id="063c8-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="063c8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="063c8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="063c8-111">Remarks</span></span>

<span data-ttu-id="063c8-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="063c8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="063c8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="063c8-113">Requirements</span></span>
------------
><span data-ttu-id="063c8-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="063c8-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="063c8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="063c8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="063c8-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="063c8-116">See also</span></span>


[<span data-ttu-id="063c8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="063c8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)