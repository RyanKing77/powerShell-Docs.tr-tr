---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi
ms.openlocfilehash: b4d4c901268344ba67d77e4dc982042bfc2abd78
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9b5c7-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b5c7-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9b5c7-104">Yönetilen düğüme yapılandırma belgesini gönderir ve bekleyen bir değişiklik kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9b5c7-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="9b5c7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b5c7-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="9b5c7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b5c7-106">Parameters</span></span>
----------

<span data-ttu-id="9b5c7-107">*ConfigurationData* \[içinde\] yapılandırması için ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="9b5c7-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9b5c7-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="9b5c7-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9b5c7-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9b5c7-109">Return value</span></span>
------------

<span data-ttu-id="9b5c7-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b5c7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b5c7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b5c7-111">Remarks</span></span>

<span data-ttu-id="9b5c7-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9b5c7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b5c7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b5c7-113">Requirements</span></span>
------------
><span data-ttu-id="9b5c7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9b5c7-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9b5c7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9b5c7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9b5c7-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9b5c7-116">See also</span></span>


[<span data-ttu-id="9b5c7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9b5c7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)