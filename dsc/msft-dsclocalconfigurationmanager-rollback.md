---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının geri alma yöntemi"
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9dd2a-103">MSFT_DSCLocalConfigurationManager sınıfının geri alma yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dd2a-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9dd2a-104">Geri önceki bir sürüm olarak yapılandırma yapar.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="9dd2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dd2a-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="9dd2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9dd2a-106">Parameters</span></span>
----------

<span data-ttu-id="9dd2a-107">*configurationNumber* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="9dd2a-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="9dd2a-108">İstenen yapılandırma belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="9dd2a-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9dd2a-109">Return value</span></span>
------------

<span data-ttu-id="9dd2a-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9dd2a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dd2a-111">Remarks</span></span>

<span data-ttu-id="9dd2a-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9dd2a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9dd2a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dd2a-113">Requirements</span></span>
------------
><span data-ttu-id="9dd2a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9dd2a-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9dd2a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9dd2a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9dd2a-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9dd2a-116">See also</span></span>


[<span data-ttu-id="9dd2a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9dd2a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



