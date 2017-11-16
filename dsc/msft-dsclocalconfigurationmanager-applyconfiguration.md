---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1164a-103">MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="1164a-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1164a-104">Bekleyen yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1164a-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="1164a-105">Bekleyen yapılandırma yoksa, bu yöntem geçerli yapılandırmasını yeniden uygular.</span><span class="sxs-lookup"><span data-stu-id="1164a-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="1164a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1164a-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="1164a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1164a-107">Parameters</span></span>
----------

<span data-ttu-id="1164a-108">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="1164a-108">*force* \[in\]</span></span>  
<span data-ttu-id="1164a-109">Bu ise **doğru**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden.</span><span class="sxs-lookup"><span data-stu-id="1164a-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="1164a-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="1164a-110">Return value</span></span>
------------

<span data-ttu-id="1164a-111">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1164a-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1164a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1164a-112">Remarks</span></span>

<span data-ttu-id="1164a-113">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="1164a-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1164a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1164a-114">Requirements</span></span>
------------
><span data-ttu-id="1164a-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1164a-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1164a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1164a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1164a-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1164a-117">See also</span></span>


[<span data-ttu-id="1164a-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1164a-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



