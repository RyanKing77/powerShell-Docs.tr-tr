---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218884"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dbfee-103">MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="dbfee-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dbfee-104">Devam ediyor yapılandırma değişikliği durdurur.</span><span class="sxs-lookup"><span data-stu-id="dbfee-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="dbfee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbfee-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="dbfee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbfee-106">Parameters</span></span>
----------

<span data-ttu-id="dbfee-107">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="dbfee-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="dbfee-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="dbfee-108">Return value</span></span>
------------

<span data-ttu-id="dbfee-109">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="dbfee-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbfee-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbfee-110">Remarks</span></span>

<span data-ttu-id="dbfee-111">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="dbfee-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dbfee-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbfee-112">Requirements</span></span>
------------
><span data-ttu-id="dbfee-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dbfee-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="dbfee-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dbfee-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="dbfee-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="dbfee-115">See also</span></span>


[<span data-ttu-id="dbfee-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dbfee-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)