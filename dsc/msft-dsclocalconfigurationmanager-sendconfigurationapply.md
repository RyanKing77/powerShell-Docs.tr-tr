---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApply yöntemi
ms.openlocfilehash: c578f4f52d3ea70e7bcf683ac204d6e484d4630d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222165"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cb01f-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb01f-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cb01f-104">Yönetilen düğüme yapılandırma belgesini gönderir ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb01f-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="cb01f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb01f-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="cb01f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb01f-106">Parameters</span></span>
----------

<span data-ttu-id="cb01f-107">*ConfigurationData* \[içinde\] yapılandırması için ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="cb01f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="cb01f-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="cb01f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="cb01f-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="cb01f-109">Return value</span></span>
------------

<span data-ttu-id="cb01f-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb01f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb01f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb01f-111">Remarks</span></span>

<span data-ttu-id="cb01f-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="cb01f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb01f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb01f-113">Requirements</span></span>
------------
><span data-ttu-id="cb01f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cb01f-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cb01f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb01f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cb01f-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="cb01f-116">See also</span></span>


[<span data-ttu-id="cb01f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cb01f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)