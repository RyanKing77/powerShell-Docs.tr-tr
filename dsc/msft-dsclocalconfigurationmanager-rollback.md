---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının geri alma yöntemi"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c5638-103">MSFT_DSCLocalConfigurationManager sınıfının geri alma yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5638-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c5638-104">Geri önceki bir sürüm olarak yapılandırma yapar.</span><span class="sxs-lookup"><span data-stu-id="c5638-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="c5638-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5638-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="c5638-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5638-106">Parameters</span></span>
----------

<span data-ttu-id="c5638-107">*configurationNumber* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="c5638-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="c5638-108">İstenen yapılandırma belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5638-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="c5638-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="c5638-109">Return value</span></span>
------------

<span data-ttu-id="c5638-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5638-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5638-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5638-111">Remarks</span></span>

<span data-ttu-id="c5638-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c5638-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5638-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5638-113">Requirements</span></span>
------------
><span data-ttu-id="c5638-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c5638-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c5638-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5638-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c5638-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c5638-116">See also</span></span>


[<span data-ttu-id="c5638-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c5638-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



